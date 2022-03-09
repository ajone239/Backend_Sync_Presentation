<!-- JA -->
# Title

#### By:
#### Jesse Akozbek and Austin Jones

# Overview

### Concepts

#### Concepts that we think are intrinsic to working with the terminal.

### Tools (common/essential)

#### A run down of some of the tools that make ends meet.

### Examples

#### Examples of how a terminal workflow has made life easier.

<!-- ## Takeaways? -->

# Concepts

<!-- AJ -->
## Your terminal is your friend.

- You should get to know your friend. The terminal is a main line to
  your computer -- an effective tool.
- It's all there. The terminal is one box for most of your tools.
- Your friend wants to help you. You have to know how to ask it for
  help.

<!-- JA -->
## How you flow through your work.

- I can't willingly do something my computer can do better.
- Homogenous workflows increase productivity.
  - Ex PRs
  - Humans suck at context switching.
- Less mouse is better.
- Less seams in a workflow.

<!-- AJ -->
## Unix philosophy / Small Composable Tools

<!-- JA -->
## Shell is a language

Your shell `(zsh/bash/sh)` is a programming language -- not a means to
navigation. It can work for you just as well as python, in some cases
better.

# Tools (common/essential)

### Really Nice
#### Tools that make the terminal feel like an extension of your brain.

<!-- JA -->
## Really Nice

- tmux
- nvim/vim
- fzf

<!-- Handoff to Austin -->
<!-- AJ -->
## Essential

### standard gnu utils

- sed (helper)
- awk
- vi
- find
- grep

### builtin (ls, cd, etc.)

These come with your shell.

<!-- AJ -->
## Other

This is a class of tools that aren't necessary, but are groovy.

### gnu replacements

- fd-find
- ripgrep
- exa

### Cute

- neofetch
- figlet
- toilet
- cowsay


# Examples

<!-- AJ -->
## Austin Examples
- for loop + md5 situ
- awk for command frequency
- awk for scaling time test
- sed for changing repo name

## EX 1

<!-- Handoff -->
<!-- JA -->
### Jesse Example Ideas
#### Have an alias to edit and apply your aliases

```sh
alias edza="vim $ZDOTDIR/.zsh_aliases; exec zsh"
```

- Git push, but account for possibility that an upstream tracked branch doesn't exist yet
- awk Docker find name of running container using awk
- Delete local branches that have been deleted upstream
- Github create PR + JIRA CLI

# Conclusion

## VEMO

## Where to start?

If you run into a problem fix it programmatically.
