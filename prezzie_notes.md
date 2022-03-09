# The Terminal is your friend.

#### By:
#### Jesse Akozbek and Austin Jones

<!-- # Title -->

# Overview

### Concepts
#### Concepts that we think are intrinsic to working with the terminal.

### Tools

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
### Workflows
#### How using the terminal can make your development smoother

<!-- AJ -->
### Small Composable Tools
####  A fundamental perk to working from the terminal.

<!-- JA -->
### Shell is a language
#### It seems like 'the thing you do in the terminal', but it is more than that

<!-- # Concepts -->

<!-- AJ -->
# Your terminal is your friend.

- You should get to know your friend.
  The terminal is a main line to your computer -- an effective tool.
- It's all there.
  The terminal is one box for most of your tools.
- Your friend wants to help you. You have to know how to ask it for help.

<!-- ## Your terminal is your friend. -->

<!-- JA -->
# How you flow through your work.

- Don't spend a lot of time doing something that your computer can do better
- Homogeneous workflows increase productivity.
  - Humans suck at context switching.
  - Later Example: PRs
- Less mouse is better.
- Less seams in a workflow.

<!-- ## How you flow through your work. -->

<!-- AJ -->
# Small Composable Tools

- The Unix philosophy is built around small tool that can chain.
- Monolithic solutions are locked into solving problem that were foreseen.
- Smaller tools can build into surprisingly dynamic tools.

<!-- ## Small Composable Tools -->

<!-- JA -->
# Shell is a language

It's not just the thing you use in your terminal!

Your shell `(zsh/bash/sh)` is a programming language -- not a means to
navigation. It can work for you just as well as python, in some cases
better.

```
DEMO -->
```

<!-- ## Shell is a language -->

# Tools

### Really Nice
#### Tools that make the terminal feel like an extension of your brain.

### Essential
#### The tools that you won't be able to not use.

<!-- # Tools (common/essential) -->

<!-- JA -->
# Really Nice
#### Think less, program more!

- `tmux`
- `nvim`/`vim`
- `fzf`

```
DEMO ->
```

<!-- ## Really Nice -->

<!-- Handoff to Austin -->
<!-- AJ -->
# Essential

### Built In's (ls, cd, etc.)

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

### Austin's Examples

### Jesse's Examples

<!-- # Examples -->

<!-- AJ -->
# Austin's Examples

### sed for changing repo name
#### Easy command for fixing dependencies in a file.

### awk for command frequency
#### Something I used while making this presentation.

### awk for scaling time test
#### How this workflow helped me do my job.

### Quickly compare files with a friend
#### A nifty solution to debugging build differences.

<!-- # Austin Examples -->

# sed for changing repo name

```sh
sed '/hotwallet-${short_name}/ s/main/<Current Working Branch>/' Cargo.toml
```

# awk for command frequency

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

Output:
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

# awk for scaling time test

```sh
$ cat mutex_test.txt | \
  sed "s/s$//" | \
  awk ' { sum += $6; count += 1 } END { print 'mutex' sum / count} '
$ cat url_test.txt | \
  sed "s/s$//" | \
  awk ' { sum += $6; count += 1 } END { print 'url' sum / count} '
```

Output:
```
mutex 23.1128
url 22.369
```

# Quickly compare files with a friend

- for loop + md5

```sh
$ for f in */Cargo.toml; do \
  md5 -r $f; \
done;
```

Output:
```
8499ff4505a176f78212079f7effb674 common/Cargo.toml
253327530cbfbc0d6bdf8c38669cc075 communicator/Cargo.toml
2db895d65e5dc764a979d64c348b2c09 manager/Cargo.toml
aa16baf0012fa188e1a88b8225591131 worker-grpc/Cargo.toml
```

<!-- Handoff -->
<!-- JA -->
# Jesse's Examples
#### Have an alias to edit and apply your aliases

```sh
alias edza="vim $ZDOTDIR/.zsh_aliases; exec zsh"
```

#### Git push, account for upstream branch missing

```sh
git_push_account_for_tracking = function() {
    tracking=$(git status -sb | grep origin/)

    if [[ $tracking = "" ]]; then
        git push -u origin $(git branch --show-current)
    else
        git push
    fi
}

alias gp="git_push_account_for_tracking"
```

# Jesse's Examples

#### Delete local branches that have been deleted upstream
```sh
alias gbr="git branch --v | awk '/\[gone\]/ {print \$1}' | xargs git branch -D"
```

#### Github create PR + JIRA CLI
```sh
get_jira_issue_summary = function() {
    jira issue list --plain --columns key,summary > temp_jira_issues;

    echo $(cat temp_jira_issues | rg $(git branch --show-current) | cut -f2)

    rm temp_jira_issues
}

alias ghpr='gh pr create --base main --reviewer $DEFAULT_REVIEWER --title "$(git branch --show-current): $(get_jira_issue_summary)" --body '
```

#### Docker find container id of running container using awk
```sh
docker ps | grep communicator | grep 1_1 | awk '{print $1}' | xargs docker logs
```

<!-- ### Jesse Example Ideas -->


# Conclusion

### VEMO

### Where to start?

<!-- # Conclusion -->

# VEMO
#### It's a vim demo
<!-- ## VEMO -->

# Where to start?

#### Learn VIM for the last time
#### The Primeagen (Note: contains vulgar language)

If you run into a problem fix it programmatically.
<!-- ## Where to start? -->
