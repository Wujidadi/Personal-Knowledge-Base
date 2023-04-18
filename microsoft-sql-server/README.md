# Microsoft SQL Server

## 從 bak 檔還原資料庫

> From [Timmy Chao](https://github.com/Timmy0618), 2022-03-24 14:03 in Skype PChome 倉庫科窗

1. 把 bak 檔放進 SQL Server volume 可以讀取的地方
2. 進入 SQL Server 容器
3. `touch /var/opt/mssql/data/agroup.mdf`
4. `touch /var/opt/mssql/data/agrouplog.ldf`
5. `chmod -R 777 /var/opt/mssql`
6. 執行以下 SQL (`file_path` 記得換成你的 bak 檔路徑)：
   ```sql
   RESTORE DATABASE [agroup]
     FILE = N'bpwms_pc_Data'
     FROM
       DISK = N'file_path'
     WITH
       REPLACE,
       NOUNLOAD,
       STATS = 5,
       FILE = 1,
       MOVE N'bpwms_pc_Data'
       TO N'/var/opt/mssql/data/agroup.mdf',
       MOVE N'bpwms_pc_Log'
       TO N'/var/opt/mssql/data/agrouplog.ldf'
   ```
7. 匯入完畢後再執行以下 SQL：
   ```sql
   ALTER DATABASE agroup SET AUTO_SHRINK OFF
   ```
