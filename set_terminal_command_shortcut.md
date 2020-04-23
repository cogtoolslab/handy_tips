This is for setting up the shortcut commands in Mac terminal
For example, if I type ```cts``` in my terminal, it will directly link to the lab server
How?
1. I used oh-my-zsh from here https://ohmyz.sh/ but it would work for regular terminals too
2a. If you use oh-my-zsh: You find ```~/.zshrc```.
2b. If you just use default terminal, just open ```~/.bash_profile```.
3. I installed Atom as my text editor so I can open it from my terminal ```atom ~/.zshrc``` to edit it. But any text editor tools would work. If you open it from your desktop, you may need to view invisible files to see it.
4. Add under "alias" and save the file. For example ```alias cts = "ssh someone@cogtoolslab.com"```. Next time, I entered ```cts``` in my terminal, it would directly execute the command.


Other helpful shortcut can be found here:
https://medium.com/the-lazy-developer/five-life-changing-git-aliases-e4211c090017
