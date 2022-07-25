# dotconf
Use Git to manage dotfiles.

## Names

```
# What directory's dotfiles do you want to manage?
DOTCONF_MANAGED_PATH=$HOME
# Where to put the Git repo?
DOTCONF_GIT_DIR=$DOTCONF_MANAGED_PATH/.dotfiles/.git

# Defines dotconf alias. Recommend eventually copying this to your shell config.
alias dotconf='git --git-dir=$DOTCONF_GIT_DIR --work-tree=$DOTCONF_MANAGED_PATH'
```

## New repo

```
mkdir -p $DOTCONF_GIT_DIR
dotconf init
dotconf config --local status.showUntrackedFiles no
```

## Existing repo

```
git clone --bare <existing repo> $DOTCONF_GIT_DIR
dotconf config --local status.showUntrackedFiles no

# WARNING: Overwrites any files in DOTCONF_MANAGED_PATH that are defined in your
# existing repo with the files in your existing repo.
dotconf checkout -f
```
