# Setting up gitleaks as pre-commit hook
Now we (roughly) understand how gitleaks works, let's see how we can actually use this tool to prevent secrets being committed to git.

The way we do this, is by making use of a so called [pre-commit hook](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks). A git hook is basically a way to extend git functionality, by being able to run custom scripts on important client side git actions, like commit or merge, before or after git continues to do it's business.

As the name suggests, a pre-commit hook is a way to run those scripts before a commit is actually committed to the git repo.

In order to tell git what exactly it should execute, we need two things:
- A configuration file which tells git which script(s) to run
- Install the configuration in our git project

In this case, all we need to do is point the pre-commit config to a particular version of gitleaks on Github, configure gitleaks where to find our rules-configuration file and weither it should detect or protect secrets it finds.

One final note, before going to the assignments: by default, pre-commit only runs against added/modified files. This means that only the changes in those files will be scanned, not the entire files. This also means that, if you have an existing repo, and you want to add gitleaks, it's generally a good idea to run gitleaks against all files.

## Pre-assignment
If you want to do the advanced assignment (scan existing files), please grab the 'hints/badconfig.json' file and add/commit it to the repository, before continuing with the assignments. Try to resist peeking the contents of the file, as this spoils part of the first assignment =]

## Assignment
In the workshop folder on your machine, download the .pre-commit-config.yaml file from this git folder. Open the file and try to make sense of what it will do when we do a `git commit` in the next part of the assignment.

Once you've downloaded the file, install the pre-commit hook by executing this command: `pre-commit install`.

Your project is now setup to detect secrets!

Now, try to add and commit a new JSON config file to the repo, containing several items you believe should be recognized as secrets and therefor never be able to commit.

Play around with several name/value combinations inside the JSON file. Is there anything you notice?

## Advanced assignment
Your repo is now protected against accidental commits containing 'generic' secrets like keys, tokens and passwords, but not really anything else (like connectionstrings). Can you create a new rule which can prevent a commit of a SQL connectionstring containing a password?