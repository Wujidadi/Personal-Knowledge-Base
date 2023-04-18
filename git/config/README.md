# `.git/config` 參考配置

```gitconfig
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = false
    autocrlf = false
    precomposeunicode = true
[user]
    name = 你的username
    email = 你的email
[remote "origin"]
    url = 你的Git倉庫URL
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "main"]
    remote = origin
    merge = refs/heads/main
```
