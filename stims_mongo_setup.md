# Guide to hosting your stimuli on the lab experiment server database and using in your experiment
The cogtoolslab experiment server (located at cogtoolslab.org) is linked to a MongoDB instance which hosts most of the lab's stimuli and data.

So, do you want to put your stimuli on the mongo DB?
benefits:
* no need to commit your stimuli to the repo
* existing cogtoolslab server code counts how many sessions (participants) have used those stimuli
* it's stored somewhere in the cloud, although it's probably safer to back it up on your own local machines.

## preliminaries

You can visualize what's on the database using [mongoDB compass, a software tool](https://www.mongodb.com/products/tools/compass).

## hosting (putting your stimuli online so it's accessible to the server)
so you made your stims, e.g. as a bunch of JSON files.
We have several jupyter notebooks which implement how to put stimuli on the database.
An example is [here](https://github.com/cogtoolslab/tangram_construction/blob/main/stimuli/upload_stimuli_to_mongo.ipynb).
it:
1) connects to mongoDB (DB stands for database)
2) puts the stimuli on the database

Important things to think about:
Many experiments have their stimuli hosted on the server, we don't want to overwrite or collide with those!
Make a database name that is unique to your experiment.
One style is to have a database name called `[experiment name]_input` for stimuli only, and a separate database called `[experiment name]_output` for collected data.

### but I have non-JSON assets, e.g. images.
We have an S3 bucket set up for hosting large files and large amounts of files like images.
TODO: write a guide on how to put images on S3.

#### OK, but I only have like, 30 images.
A simple workaround is to place them on the server directly in your client code, e.g. in a folder called `assets` in your experiment's folder.
(TODO: why is this a bad idea in some cases?).
Depending on your experiment set up, you might just commit those to version control and use Git to place them on the server.
But that's probably not the best.
Another way is to put them up there at the same time you upload your (corresponding) JSON stimuli to the mongoDB database.
An example of how this might work using python is [here with `paramiko`](https://github.com/cogtoolslab/tangram_construction/blob/develop/stimuli/upload_stimuli_to_mongo.ipynb).

## pulling (loading stimuli into your experiment)

<!--There does not seem to be a convention on where (server (app.js, store.js), database (i.e. in how data are stored on mongoDB), or experiment client (i.e. JSPsych))) trial stimuli and conditions are randomized. but... --> 

mongoDB works by :
* sending POST request to `/db/getstims`.
  * This is implemented in `store.js`.
* One `collection` is one group of trial stimuli, you can use this to have one collection per experiment run (e.g. pilot, v2, v3, etc.)
   * or you could have a single collection that has all the stimuli, with each single _document_ including an array of all the stimuli for a single iteration of the experiment.
   * this is what the example server code is written before below.

### in experiment
You need an installation of socket.io on your client side (experiment) code.
An easy way is to include a `socket.io.js` file in your client code directly (and add it to the repo).

**Very important:** Make sure that the version of socket.io used in the client (e.g. `experiment.html`) matches the version that is used on the cogtoolslab.org server.
The server socket.io version is installed via node. 
This can be looked up in a `package-lock.json` of an existing experiment repo that you know works.
One way to install socket.io in your client code is to simple save a minified copy of it (`socket.io.js`) in your client code directly, e.g. in a `js/lib` folder.
You could copy the `socket.io.js` file from an experiment repo that you know works, and match the server's socket.io version to what that repo has listed in `package-lock.json`.

#### 1) in html, need script tag
```angular2html
<script>
    socket = io.connect();
    // this results in calling io.on('connection') in app.js
</script>
```

#### 2) in `app.js`, need to route to your stimuli
```js
// around line 77 in app.js
sendPostRequest('...', {
    json: {
    dbname: 'stimuli', // one cogtoolslab convention, another is [experiment name]_input
    collection: 'yourCollectionNameHere',
    gameid: '' // keep this as is in app.js, it will save you 
});
```

in `store.js`, need to handle the request for stimuli and retrieve them from mongoDB instance.
Usually you shouldn't need to mess with this if borrowing from existing experiment code (app.js, store.js) that works.
```js
app.post('/db/getstims', (request, response) => {
  if (!request.body) {
    return failure(response, '/db/getstims needs post request body');
  }
  console.log('request:',request.body);
  console.log(`got request to get stims from ${request.body.dbname}/${request.body.colname}/${request.body.it_name}`);

  const databaseName = request.body.dbname;
  const collectionName = request.body.colname;
  const iterName = request.body.it_name;
  if (!collectionName) {
    return failure(response, '/db/getstims needs collection');
  }
  if (!databaseName) {
    return failure(response, '/db/getstims needs database');
  }

  const database = connection.db(databaseName);
  const collection = database.collection(collectionName);

  collection.aggregate([
    { $match: { iteration: iterName } }, // only retrieve the iteration we want
  ]).toArray((err, results) => {
    if (err) {
      console.log("Error while aggregating for iternamer", iterName, " error: ", err);
    } else {
      // Immediately mark as annotated so others won't get it too
      try {
        markAnnotation(collection, request.body.gameid, results[0]['_id']);
      }
      catch (err) {
        console.log("Couldn't mark gameID as served", err);
      }
      console.log("Sending", results[0]);
      // this gets sent to store.js (not client yet)
      response.send(results[0]);
    }
  });
});
```

#### 3) in your JSPsych experiment (client) code
```js
// get stimuli from database
let socket = io.connect();
console.log("requesting stims");
socket.emit("getStims", {
    proj_name: YOUR_DATABASE_NAME,  // i.e. in mongoDB
    exp_name: YOUR_COLLECTION_NAME,
    iter_name: YOUR_ITERATION_NAME,
});
socket.on("stims", (stimuliConfig) => {
    // input of this function is the output of the server's sendPostRequest,
    // which should be the stimuli requested
    //console.log("got stims, loading experiment");
    //console.log(stimuliConfig);
    // gameId assigned by app.js
    let gameID = stimuliConfig.gameid;
    let allStims = stimuliConfig.stims;
    yourExperimentCode(gameID, allStims, ...);
});
```





