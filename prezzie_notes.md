# Title

#### By:
#### Jesse Akozbek and Austin Jones

<!-- # Title -->

# Overview

### Concepts
#### Concepts that we think are intrinsic to working with the terminal.

### Tools (common/essential)
#### A run down of some of the tools that make ends meet.

### Examples
#### Examples of how a terminal workflow has made life easier.

### Takeaways
#### Closing thoughts etc.

<!-- # Overview -->

# Concepts
#### Concepts that we think are intrinsic to working with the terminal.

<!-- AJ -->
### Your terminal is your friend.
#### You should get to know your friend.

<!-- JA -->
### How you flow through your work.

<!-- AJ -->
### Small Composable Tools
####  A fundamental perk to working from the terminal.

<!-- JA -->
### Shell is a language

<!-- # Concepts -->

<!-- AJ -->
## Your terminal is your friend.

- You should get to know your friend.
  The terminal is a main line to your computer -- an effective tool.
- It's all there.
  The terminal is one box for most of your tools.
- Your friend wants to help you. You have to know how to ask it for help.

<!-- ## Your terminal is your friend. -->

<!-- JA -->
## How you flow through your work.

- I can't willingly do something my computer can do better.
- Homogeneous workflows increase productivity.
  - Ex PRs
  - Humans suck at context switching.
- Less mouse is better.
- Less seams in a workflow.

<!-- ## How you flow through your work. -->

<!-- AJ -->
## Small Composable Tools
TEMP
<!-- ## Small Composable Tools -->

<!-- JA -->
## Shell is a language

Your shell `(zsh/bash/sh)` is a programming language -- not a means to
navigation. It can work for you just as well as python, in some cases
better.

<!-- ## Shell is a language -->

# Tools (common/essential)

### Really Nice
#### Tools that make the terminal feel like an extension of your brain.

### Essential

<!-- # Tools (common/essential) -->

<!-- JA -->
## Really Nice

- `tmux`
- `nvim`/`vim`
- `fzf`

<!-- ## Really Nice -->

<!-- Handoff to Austin -->
<!-- AJ -->
## Essential

### `builtin` (ls, cd, etc.)

These come with your shell.

### Standard GNU utilities

- `sed` (helper)
- `awk`
- `vi`
- `find`
- `grep`

### gnu replacements

- `fd-find`
- `ripgrep`
- `exa`

<!-- ## Essential -->

# Examples
TEMP
<!-- # Examples -->

<!-- AJ -->
## Austin Examples

## sed for changing repo name

```sh
sed '/hotwallet-${short_name}/ s/main/<Current Working Branch>/' Cargo.toml
```

## awk for command frequency

```sh
$ cat ~/.zsh_history | \
  sed "s/:[ ]*[0-9]*:0;[* ]*//" | \
  tr "|" "\n" | \
  sed 's/^ //' | \
  awk '{ dict[$1]++; }
       END \
       { for (key in dict) print dict[key] ": " key }' | \
  sort -nr | \
  head
```
```
307: ls
153: vim
133: cargo
129: cd
108: sed
103: gst
69: cat
64: awk
58: git
56: echo
```

## awk for scaling time test

```sh
$ cat mutex_test.txt | \
  sed "s/s$//" | \
  awk ' { sum += $6; count += 1 } END { print 'mutex' sum / count} '
$ cat url_test.txt | \
  sed "s/s$//" | \
  awk ' { sum += $6; count += 1 } END { print 'url' sum / count} '
```
```
mutex 23.1128
url 22.369
```

## Quickly compare files with a friend

- for loop + md5

```sh
$ for f in */Cargo.toml; do \
  md5 -r $f; \
done;
```
```
8499ff4505a176f78212079f7effb674 common/Cargo.toml
253327530cbfbc0d6bdf8c38669cc075 communicator/Cargo.toml
2db895d65e5dc764a979d64c348b2c09 manager/Cargo.toml
aa16baf0012fa188e1a88b8225591131 worker-grpc/Cargo.toml
```

<!-- ## Austin Examples -->

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

<!-- ### Jesse Example Ideas -->


# Conclusion

### VEMO

### Where to start?

<!-- # Conclusion -->

## VEMO
TEMP
<!-- ## VEMO -->

## Where to start?

If you run into a problem fix it programmatically.
<!-- ## Where to start? -->
