# dotlocaldotbashrc

`.local.bashrc` files that are sourced in a clean bash process when entering
the directory.

*Replaces the [projector](https://github.com/bas080/projector) project.*

## Features

- Makes a simple to define env variables, aliases and functions for a specific
  project directory.
- Creates an bash history that is a separate from the root bash history.
  - Makes it easier to keep and find commands that are related to that project.
  - Doesn't fill up the root bash history.
- Inherits exported env variables of root process.
- Does not inherit env variables of other `.local.bashrc` directories.

## Setup

Add the following to your `.bashrc`.

```bash
# Required
curl 'https://raw.githubusercontent.com/bas080/dotlocaldotbashrc/master/dotlocaldotbashrc > "$HOME/.dotlocaldotbashrc"
echo 'source "$HOME/.dotlocaldotbashrc"' >> ~/.bashrc

# Optional: show .bashrc directory name in prompt.
PS1="(bashrc:$BASHRC_HOME)$PS1"

# Optional: add .local.* to your .gitignore
```

## Usage

```
$ cd projects/bashrc/
dotlocaldotbashrc: open /home/ant/projects/bashrc
$ cd nested/
dotlocaldotbashrc: exit /home/ant/projects/bashrc
dotlocaldotbashrc: open /home/ant/projects/bashrc/nested
$ cd
dotlocaldotbashrc: exit /home/ant/projects/bashrc/nested
$
```

> Notice that navigating to the home directory resulted in only a bashrc bash
> session being exited. We just use the initial bash process that was started
> when bashrc and the rest of the interactive shell was bootstrapped.

You can source the local .local.bashrc at anytime with `dotlocaldotbashrc` function.

```bash
$ dotlocaldotbashrc
bashrc: source '/home/ant/.local.bashrc'
$
```

## License

GPLv3
