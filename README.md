# Gitflow

## Requirements

### Repo Requirements
- Run in an existing GIT repository
- Use SSH to clone your repo (altough you should be, HTTPs is no longer supported in GitHub). (TODO: IS THIS ACTUALLY A REQUIREMENT?)

### System Requirements
Here is the list of requirements needed:
- Bash 4 or higher.
    - Here is an [article](https://itnext.io/upgrading-bash-on-macos-7138bd1066ba) on how to update Bash in MacOS. Skip the `Set Default Shell` section, that won't be needed.
- Allow redirection to `/dev/null`.
    - Sometimes this fails with permission denied in MacOS. If so, follow what's stated [here](https://unix.stackexchange.com/questions/146633/bash-dev-null-permission-denied).
- Have GNU enhanced getopt installed
- Have the following commands installed and available:
    - `export`, `echo`, `eval`, `unset`, `exit`, `cd`, `pwd`, `which`
    - `cat`, `rm`, `mkdir`, `tty`, `shasum`, `head`, `tee`
    - `uname`, `dirname`, `realpath`, `readlink`
    - `sed`, `cut`, `grep`, `tr`, `wc`, `awk`
    - `nano`
    - `git`
    - `curl`
    - `jq` (>= 1.6)

You can check if you have everything required to run this program by running 
    `./check-requirements`
The script will only check bash version, redirection to `/dev/null`, GNU enhanced getopt installation and `jq` installation. Every other commands is assumed to exist (they come installed in MacOS).

**MacOS**

To fulfill most of the above requirements in MacOS, you can run the installation script `install`.
1. `chmod +x install`
2. `./install`
    - You may need to re-run it until you get a message `All required commands/programs have been installed`.
3. `./check-requirements`
    - You should get a message `All required commands/programs are installed!`.
4. Complete the [Setup](#setup)

**Windows**

Not supported yet, you can try if it works. Some suggestions regarding the requirements:
- From stackoverflow --> install GNU getopt with Cygwin

## Setup
To setup `gitflow`, you must do the following:
- Create a `.env` file as explained in the file `.env-example`
- Go to your terminal configuration file (eg: .bashrc, .zshrc) and add an alias pointing to the gitflow script
    - `alias gitflow="/full/path/to/gitflow`

## Configuration
You can customize `gitflow` to adjust to your project's branching model. To do so, you must edit the file `config.json`. The configurations available are the following:
- `base-branches`: array of strings with possible base branches to merge to from feature branches.
- `feature-base`: base branch to create feature branches from
- `default-config`: NOT IMPLEMENTED YET, will be used to override default configurations for features. The current repo state is the default configuration.
- `finish-steps`: array of objects with steps to follow when running `feature finish` command. If error, steps are numbered from 1 to N. Each object must contain:
    - `base`: base branch to merge feature into
    - `aux-branch`: boolean that states whether merging should be done from an auxiliar branch
    - `aux-branch-prefix`: prefix to use for the auxiliar branch. Only required if `aux-branch` is true
    - `with-pr`: boolean that states if a PR should be created or if merging should be done during execution

## Execution
Run gitflow with
    `gitflow <subcommand>`

Available subcommands are
- `feature` Manage your feature branches.

### Subcommand - Feature
Manage your feature branches. Available actions are
- `gitflow feature [help]`	--> Display available actions
- `gitflow feature list`	--> Lists existing local feature branches
- `gitflow feature start`	--> Start new feature from base
- `gitflow feature finish`	--> Finish a feature (push, PRs, etc)
- `gitflow feature publish`	--> Publish feature to origin
- `gitflow feature track`	--> Get feature branch from origin
- `gitflow feature diff`	--> Show all changes in feature branch vs base
- `gitflow feature checkout`	--> Switch to feature branch
- `gitflow feature rebase`	--> Rebase feature branch on base
- `gitflow feature pull`	--> Pull feature branch from origin
- `gitflow feature delete`	--> Delete feature branch
- `gitflow feature rename`	--> Rename feature branch
