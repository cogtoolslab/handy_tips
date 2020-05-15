Preparation for running study on server before launching
1. After logging in the lab server via ssh connection, Git clone the the repo if haven't already done;
2. In side the study folder, there is “app.js” (communicates with client and talks to store.js) “store.js”(talks to MongoDB)
Below are useful shortcuts related to "sessions":
    ```tmux ls``` (list what sessions we have)
    ```tmux new -s SESSION_NAME``` (create a new session)
    ```tmux attach-session -t SESSION_NAME``` (attach session so that we can view it, ```ctrl+B+D``` for detach)
    ```tmux kill-session -t SESSION_NAME``` (remove session)
3. Then we create a parallel pane so we can look at it:
    Press 2 keys ```ctrl+B``` then release then ```%``` (left and right view) or ``”``` (up and down view)
    Press 2 keys ```ctrl+B``` then release then ```X``` to remove pane
4. In one pane, we can type ```node app.js```
5. In another pane, we can type ```node store.js``` (if for the very first time, running ```npm install``` first)
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
