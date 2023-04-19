# Node.js 使用 `@` 指代特定路徑

以專案目錄下的 `resources` 為例，在 Workspace 設定檔（`*.code-workspace`）的 `settings` 項加入以下設定：
```json
"path-intellisense.mappings": {
    "@": "${workspaceFolder}/resources"
}
```
