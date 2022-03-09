# Title

#### By:
#### Jesse Akozbek and Austin Jones

# Overview

### Concepts

#### Concepts that we think are intrinsic to working with the terminal.

### Tools

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

<!-- Handoff -->
<!-- JA -->
## Jesse's Examples
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

## Jesse's Examples

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

# Conclusion

## VEMO

## Where to start?

#### Learn VIM for the last time
#### The Primeagen (Note: contains vulgar language)

If you run into a problem fix it programmatically.
