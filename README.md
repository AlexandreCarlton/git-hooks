# git-hooks
A personal set of [git hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
to automate mundane tasks.

## Setting up
This is not compatible with the new `core.hooksPath` option (yet).

```bash
mkdir --parents "${HOME}/.config/git/templates"
git config --global init.templatedir "${HOME}/.config/git/templates"
git clone https://github.com/AlexandreCarlton/git-hooks.git "${HOME}/.config/git/templates/hooks"
```

## clean-python-bytecode-files
Deletes any `.pyc`, `.pyo` and `__pycache__` files found in the project to
force recompilation of `.py` files on a checkout.

## create-tags-file
"Adapted" from [Effortless Ctags with Git](https://tbaggery.com/2011/08/08/effortless-ctags-with-git.html),
this script will create a tags file from all tracked files in the repository.

## insert-jira-ticket
Attempts to determine the ticket number of a [JIRA issue](https://confluence.atlassian.com/jira064/what-is-an-issue-720416138.html)
from the current branch name ([generated by Bitbucket Server](https://confluence.atlassian.com/bitbucketserver/using-branches-in-bitbucket-server-776639968.html#UsingbranchesinBitbucketServer-Creatingbranches))
and insert it into the commit message before editing.

It assumes that you are using a [commit template](https://robots.thoughtbot.com/better-commit-messages-with-a-gitmessage-template),
and have the following line in it:

```
# References:
```

## spell-check-commit-message
Analyses the commit message once we have made a commit, and print out any
misspelt words to `stderr`. Use `git commit --amend` to fix the message.

## link-ycm-extra-conf
Creates a symbolic link `.ycm_extra_conf.py` to the one in this repository
should there exist a `CMakeLists.txt` file in the project's root.

This configuration file is optimised to analyse the `compile_commands.json`
generated in the `build` folder of the project.
