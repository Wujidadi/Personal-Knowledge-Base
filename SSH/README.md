# SSH

> Secure Shell Protocol

## `~/.ssh/config` 設定範例

```conf
Host *
    ServerAliveInterval 60
    ServerAliveCountMax 100

Host 192.168.5.28
    HostName 192.168.5.28
    User git
    IdentityFile /Users/user/.ssh/id_rsa.mygit
    IdentitiesOnly yes

Host 125.216.124.176
    HostName 125.216.124.176
    Port 108
    User git
    IdentityFile /Users/user/.ssh/id_rsa.mygit
    IdentitiesOnly yes
```
