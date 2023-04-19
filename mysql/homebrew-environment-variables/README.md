# macOS 上以 Homebrew 安裝的 MySQL 參考環境變數

## .zshrc

```bash
export PATH="/opt/homebrew/opt/mysql-client/bin:$PATH"
export LDFLAGS="-L/opt/homebrew/opt/mysql-client/lib"
export CPPFLAGS="-I/opt/homebrew/opt/mysql-client/include"
```
