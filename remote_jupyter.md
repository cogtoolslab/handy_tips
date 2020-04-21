A useful thing you may want is to have a persistent jupyter notebook server that you can re-connect to whenever you want.

How to setup to connect to a remote jupyter notebook server on the cogtoolslab nightingale machine:

1. To create a new named tmux session, run:

 `tmux new -s NAME_OF_SESSION`

  e.g., `tmux new -s 'jupyter'`

2. Fire up jupyter notebook server within this session. After you have installed Anaconda.

  i.e., `jupyter notebook` 

  To detach from this tmux session:
    Hold `CTRL + B`, then `+ D` 

  Note: To re-attach to this jupyter session, run:
    `tmux attach-session -t jupyter`

  If this is your first time connecting, make a note of which port it is being served on. It might be something like 8890.  

  Also make a note of the token, which is a really long number.

3. Next, establish SSH tunnel to nightingale from your local machine. To do this, run:

  `ssh -fNL 8158:localhost:8890 USER@nightingale.ucsd.edu`

  where "8889" is the remote port that your jupyter notebook server is running on and
  where "8158" is the local port that you want to bind to. This can be anything, actually, 8158 is just an example.

4. Open up local browser and type: `localhost://PORT_NUM`

  where PORT_NUM is the port that you bound to in step 3 (e.g., 8158).

  If this is your first time, copy and paste the token (from step 2) into the token fields and set a password for your jupyter notebooks. 

