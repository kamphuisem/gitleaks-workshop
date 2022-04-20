# Exceptions to the rule(s)
Now we are protected against accidental commits of secrets, we find ourselfs struggling again when we want to document our repo.

We consider to commit a markdown file, containing a piece of sample code/config like this:

    {
        "MyPassword": "This1sMyP@$$w0rD!"
    }

Now, when we try to commit this documentation, using a dummy password, we can't!

Fortunately there are ways to get around this problem.

## Allow rules
Unless specified otherwise, gitleaks scans staged files for secrets.

You can configure rules of the `[allowlist]` kind in the gitleaks.toml file, which can define paths to skip from scanning and/or regexes to allow if a detection occurs.

## Skip (not recommended)
Git contains an option to skip pre-commit hooks from executing. This can be done by setting an environment variable `SKIP=<id>`, where the `id` is the ID from our .pre-commit-config.yaml file (in this case 'gitleaks'). Example: `SKIP=gitleaks git commit -m "commit skipping gitleaks check"`

A downside of this, is that the entire commit will not be checked for secrets. In this case, adding a single it's not really a big deal, but consider when you want to commit multiple files...

Also, the environment variable will usually stay set for a longer period of time, be it the lifetime of the window, or worse... on system level.

## Assignment
Add a markdown page to the repo. Fill the page with some content and a piece of sample code/config like above. Try to commit the page as often as needed, before the commit is blocked because of a 'detected secret'.

Now, add an `allowlist` rule to gitleaks.toml, which skips this (and any future) markdown file from being scanned by gitleaks.

## Advanced assignment
When we created our JSON config file, we forgot to add an important public key from one of our suppliers: `"AppPublicKey": "-----BEGIN OPENSSH PUBLIC KEY BLOCK-----bm90c29zZWNyZXRiYXNlNjRlbmNvZGVkcHVibGlja2V5"`
Please add it to your config and try to commit the file.

As public keys are, by definition, not really secret, we want to allow this value (and any future) public key configuration items to be committed to the repo. Try to create an `allowlist` rule with a regex that allows this change to be committed.