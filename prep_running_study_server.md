## Preparation for running your behavioral experiment on the `cogtoolslab.org` server


### Getting set up on the server

The `cogtoolslab.org` server is a very simple Linux virtual machine. Its reason for being is to host web-based behavioral experiments. If you do not yet have an account on `cogtoolslab.org` and need one, please reach out to Judy and/or the lab manager. 

Once you have an account, it is recommended that you join the `#computing_resources` and `#running_experiments` Slack channel so you can be aware of any outages/issues or post issues re: the server.

By the way, there are 50 ports that the server is able to listen to https requests over: 8850-8899, so if you set up the app to listen over a port number outside that range, it won't work.
You can check which ports are currently open by running `$ check_ports.sh` anywhere on the lab server.
You should also check which ports others are trying to use in the "ports" tab of the lab info doc, and reserve your own!

We use a lab-wide shared mongodb instance running on the same server. Please "cc:" Judy on any Slack/email requests for the credentials for authenticating to our database. This mongodb is used in basically two ways: (1) to store stimulus metadata that can be fetched when participants take part in our experiments; (2) to write behavioral data to in real time during experiments, which is then fetched for subsequent analyses. 

### Procedure
1. After logging in the lab server via ssh connection, Git clone the the repo if haven't already done;
2. In side the study folder, there is “app.js” (communicates with client and talks to store.js) “store.js”(talks to MongoDB)
Below are useful shortcuts related to "sessions":
    ```tmux ls``` (list what sessions we have)
    ```tmux new -s SESSION_NAME``` (create a new session)
    ```tmux attach-session -t SESSION_NAME``` (attach session so that we can view it, ```ctrl+B```-release-then```D``` for detach)
    ```tmux kill-session -t SESSION_NAME``` (remove session)
3. Then we create a parallel pane so we can look at it:
    Press 2 keys ```ctrl+B``` then release then ```%``` (left and right view) or ```”``` (up and down view)
    Press 2 keys ```ctrl+B``` then release then ```X``` to remove pane
4. In one pane, we can type ```node app.js```
5. In another pane (to switch panes, ```ctrl+B``` then release then ```o```), we can type ```node store.js``` (if for the very first time, running ```npm install``` first)
6. 3 things to check:
     -  before first time running ```node store.js```, we need to run ```npm install``` first
     - if you see the gameport number (the number in the public url and can only take values between 8880-8889) is taken, change it by ```emacs app.js``` and ```emacs store.js```
     -  if you see an error like the following, change “localhost number” in function "writeDataToMongo" by ```emacs app.js``` and “const Localhost” to a different same number by ```emacs store.js```:
    ```
    Error: listen EADDRINUSE: address already in use :::7000
    at Server.setupListenHandle [as _listen2] (net.js:1279:14)
    at listenInCluster (net.js:1327:12)
    at Server.listen (net.js:1414:7)
    at Function.listen (/home/tonexu/blendraw/studies/node_modules/express/lib/application.js:618:24)
    at mongoConnectWithRetry (/home/tonexu/blendraw/studies/store.js:99:9)
    at MongoClient.connect (/home/tonexu/blendraw/studies/store.js:50:7)
    at connectCallback (/home/tonexu/blendraw/studies/node_modules/mongodb/lib/mongo_client.js:527:5)
    at /home/tonexu/blendraw/studies/node_modules/mongodb/lib/mongo_client.js:449:13
    at process._tickCallback (internal/process/next_tick.js:61:11)
    Emitted 'error' event at:
    at emitErrorNT (net.js:1306:8)
    at process._tickCallback (internal/process/next_tick.js:63:19)
    ```
7. You can now visit your study at the url: `https://cogtoolslab.org:PORT/FILE.html` where `PORT` is the gameport specified in/to `app.js`, and `FILE` is a path to a file relative to the directory where `app.js` was _run from_. Note `https`! 

### Related Resources
* For handy tips on how to run HITs on MTurk, please also see the [wiki](https://github.com/cogtoolslab/mturkrecords/wiki) associated with the (private) mturkrecords repo. 
* For handy tips on how to migrate your experiment from MTurk to Prolific, see this documentation: https://github.com/cogtoolslab/handy_tips/blob/master/MTurk_to_Prolific.md
