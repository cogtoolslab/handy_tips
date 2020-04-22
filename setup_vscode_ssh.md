  
Enables VS Code to directly edit files on a remote computer using SSH. 
i.e. lets you use a real editor instead of relying on e.g. Jupyter/ VIM/ EMACS
Also lets you sort merge conflicts more easily.

Look here for tutorial, or follow steps below:
https://code.visualstudio.com/docs/remote/ssh


Make sure you've set up SSH keys- follow setup.txt

In VS Code Press F1 to open command palette

To open a folder one time only type (replacing YOUR_USER_NAME with your user name): 
    Remote-SSH: Connect to Host
    YOUR_USER_NAME@nightingale.ucsd.edu


To add a shortcut for connecting (and keep a folder in your workspace), edit the ssh config file. Press F1: 
    Remote-SSH: Open Configuration File. 

Append to end of file: 
    Host nightingale
        HostName nightingale.ucsd.edu
        User YOUR_USER_NAME
