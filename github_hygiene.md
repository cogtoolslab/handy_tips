### Note about storing code vs. data on GitHub
A good rule of thumb is to think of GitHub as a tool to store _code_ and _not data_. There are some exceptions to this rule, e.g., when we want to make it easier for others to download our tidy experimental dataframes as `.csv` files and re-analyze them. But these files should not be too large. >100MB is too large, and >10MB is a little bit too large. If you need a place to store a large public dataset, there are other resources we can use besides GitHub. If you simply need to share a dataset with a colleague/collaborator within cogtoolslab or at UCSD, there is likely to be another option (e.g., on a shared filesystem we all have access to).

So one of the first things to do is to update the `.gitignore` in your new project repo. Add these lines to ignore common data files (e.g., images, videos, byproducts of compiling LaTeX source, etc.) and anything likely to contain sensitive information (e.g., auth text files). Also ignore the annoying `.DS_Store` file that is part of MacOS. 

```
.DS_Store
*.csv
*.json
*.pdf
*.png
*.jpeg
*.jpg
*.tiff
*.svg
*.eps
*.ai
auth.json
auth.txt
```

### GitHub Hygiene Basics

Here are some basic GitHub hygiene practices we encourage:

0. When you sit down to start working, it is good practice to run `git pull` to pull in any changes that have been made to the repo since you last finished working. This will help to reduce the chance of nasty merge conflicts by making sure that you've synchronized your clone with the remote repo before starting to make new changes. 

1. It is generally better to make several small commits than one large, complex commit. In many cases, this means running `git add` on just a single file at a time! This allows you to leave more informative commit messages for your collaborators (including your future self).

2. Before you push, use `git diff` to inspect changes before committing to make sure they are what were intended. To get out of the git diff view, press `q`.

3. Fixing merge conflicts can be a pain. Basically, when you run into a merge conflict, inhale+exhale, then open up the file in question to identify which version of the code to keep and which to discard. The two different versions in conflict lie in between the `<<<` and the `>>>`. For example:

```
<<<<<<< HEAD:file.txt
Hello world
=======
Goodbye
>>>>>>> 77976da35a11db4580b80ae27e8d65caf5208086:file.txt
```
Here, the code that is on top with the `HEAD` marker (`Hello world`) is your local copy. The code that is on bottom with the filename and the commit hash (`Goodbye`) is what is "incoming" from the remote copy of the repository (likely pushed by one of your collaborators).

You need to do this manually for each such conflict in each file where such a conflict exists. Any file that still has this motif in it `<<<<<<< HEAD` anywhere at all in the file still has a merge conflict, and won’t execute. Various fancier text editors, e.g., Atom, have ways of easing this process, but you still want to be vigilant to make sure that these fancy editors are parsing the conflicting region properly.

4. Use `git mv` and `git rm` to "rename" files when moving them around, rather than the bare `mv` and `rm`, b/c this will make sure that the git history moves around with these files and they are not removed from the history. 

5. Generally speaking, you want to "restart and clear all output" from your jupyter notebooks before you commit them. This will keep the file size down and make it easier for collaborators to open and run them.
