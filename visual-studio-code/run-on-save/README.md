# Run on Save 插件 (`emeraldwalk.runonsave`) 的使用方式

在設定檔的 `settings` 項加入以下設定，即可**在存檔時自動執行自訂指令**：
> 範例為存檔時自動執行專案根目錄下的 `.vscode-php-cs-fix` 以進行 PHP CS Fixer 格式化
```json
"emeraldwalk.runonsave": {
    "autoClearConsole": true,
    "commands": [
        {
            "match": ".php$",
            "isAsync": true,
            "cmd": "${workspaceFolder}/.vscode-php-cs-fix '${file}'"
        }
    ]
}
```

## 用 `tasks` 執行自訂指令並綁定快捷鍵

1. 在設定檔加入 `tasks` 項，或在現有的 `tasks` 項中加入以下設定：
   ```jsonc
   "tasks": {
       "version": "2.0.0",
       "tasks": [
           {
               "label": "PHP CS Fixer",
               "type": "shell",
               "command": "${workspaceFolder}/.vscode-php-cs-fix",
               "args": [
                   "${file}"
               ],
               "presentation": {
                   "clear": true,     // 自動清理
                   "close": true,     // 執行完畢自動關閉
                   "reveal": "silent" // 靜默執行（從頭到尾不會在 console 顯示）
               }
           }
       ]
   }
   ```
2. 然後在 `keybindings.json` 加入以下設定：
   ```json
   {
       "command": "workbench.action.tasks.runTask",
       "args": "PHP CS Fixer",
       "key": "shift+cmd+f shift+cmd+s",
       "when": "editorTextFocus && !editorReadonly"
   }
   ```

注意設定檔 `tasks` 的 `label` 和 `keybindings.json` 的 `args` 是一致的  
如此便可用 `shift + cmd + f` 及 `shift + cmd + s` 組合鍵執行當前檔案的 code standard fixing

若在別的專案 or Workspace 下按這組快捷鍵，也不會報錯，而是會因為未設定 `PHP CS Fixer` 這個 task，prompt 問你要執行哪一個 task  
若當前檔案非 PHP 檔案，也不會報錯，而是靜靜地完成存檔
