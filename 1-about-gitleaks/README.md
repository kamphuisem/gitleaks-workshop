# What is gitleaks?
[Gitleaks](https://github.com/zricethezav/gitleaks) is a SAST (Static Application Security Testing) tool for detecting hardcoded secrets (like passwords, keys and tokens) and preventing them to be committed to git repos.

In order to find these secrets, gitleaks processes rules you configure for your project against all files added to the Git repo.
Rules are, in essence, nothing more then a set of regexes with some extra processing options.
Every rule should be tailored to find a specific kind of secret.
For instance a private key contains the text `-----BEGIN PRIVATE KEY-----`, whereas an access token for Slack starts with `xox[baprs]-` (read as regex).

Gitleaks uses configuration files in the [TOML format](https://en.wikipedia.org/wiki/TOML). You can find an example configuration in the gitleaks.toml file in this folder.

## Assignment
Create an empty folder on your machine and initialize that folder as a git repo (run `git init` inside the empty folder). Download the example configuration (gitleaks.toml file) to that folder. You will need it in the next assignments.

Open the file and try to make some sense of the regex and the rule options.

### Tip
Take the regex from the gitleaks.toml file to a regex-testing application (like RegexHero) and see if you can create some input which will cause the regex to find a match (i.e. recognize a secret).
