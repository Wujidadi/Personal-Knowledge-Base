# PostgreSQL

## 使 Serial Sequence 恢復由 1 開始

```sql
ALTER SEQUENCE "sequence_name" RESTART WITH 1
```

上面的 `sequence_name` 改成你的 sequence 名稱
