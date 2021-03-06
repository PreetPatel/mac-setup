# Git

What's a developer without [Git](http://git-scm.com/)? To install, run:

```bash
brew install git
```

When done, to test that it installed properly you can run:

```bash
git --version
```

And `which git` should output `/usr/local/bin/git`.

Next, we'll define your Git user \(should be the same name and email you use for [GitHub](https://github.com/)\):

```bash
git config --global user.name "Your Name Here"
git config --global user.email "your_email@youremail.com"
git config --global github.user "Your github username"
```

They will get added to your `.gitconfig` file.

To push code to your GitHub repositories, we will use the recommended HTTPS method. There are also instructions for using SSH. To prevent `git` from asking for your username and password every time you push a commit you can cache your credentials by running the following command, as described in the [instructions](https://help.github.com/articles/caching-your-github-password-in-git/).

```bash
git config --global credential.helper osxkeychain
```

## .gitconfig

These are the additional git configurations that can go under `~/.gitconfig`

```bash
[apply]
  whitespace = fix
[color]
  ui = auto
[color "branch"]
  current = yellow reverse
  local = yellow
  remote = green
[color "diff"]
  meta = yellow bold
  frag = magenta bold
  old = red bold
  new = green bold
[color "status"]
  added = yellow
  changed = green
  untracked = cyan
[merge]
  log = true
[push]
  ; "simple" avoid headaches, specially if you use `--force` w/o specifying branch
  ; see: http://stackoverflow.com/questions/13148066/warning-push-default-is-unset-its-implicit-value-is-changing-in-git-2-0
  default = simple
[url "git://github.com/"]
  insteadOf = "github:"
[url "git@github.com:"]
  insteadOf = "gh:"
  pushInsteadOf = "github:"
  pushInsteadOf = "git://github.com/"
[core]
  excludesfile = ~/.gitignore_global
  ; setting the editor fixes git commit bug http://tooky.co.uk/2010/04/08/there-was-a-problem-with-the-editor-vi-git-on-mac-os-x.html
  editor = /usr/bin/vim
[alias]
  ; show merge tree + commits info
  graph = log --graph --date-order -C -M --pretty=format:\"<%h> %ad [%an] %Cgreen%d%Creset %s\" --all --date=short
  lg = log --graph --pretty=format:'%Cred%h%Creset %C(yellow)%an%d%Creset %s %Cgreen(%cr)%Creset' --date=relative
  ; basic logging for quick browsing
  ls = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cgreen\\ [%cn]" --decorate
  ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cgreen\\ [%cn]" --decorate --numstat
  ; log + file diff
  fl = log -u
  ; find paths that matches the string
  f = "!git ls-files | grep -i"
  ; delete all merged branches
  ; dm = !git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
  ; shortcuts
  cp = cherry-pick
  st = status -s
  cl = clone
  ci = commit
  co = checkout
  br = branch
  dc = diff --cached
```

