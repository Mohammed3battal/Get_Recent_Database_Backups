## Script: Get_Recent_Database_Backups.sql

**Description**:
This script retrieves detailed metadata about recent database backups from the `msdb` system tables. It includes backup type, size, location, timing, and recovery model — helping DBAs track backup activity and validate backup health.


---

### Output Columns:

| Column              | Description                                           |
|---------------------|-------------------------------------------------------|
| `database_name`     | Name of the backed-up database                        |
| `backup_start_date` | When the backup started                               |
| `backup_finish_date`| When the backup completed                             |
| `BackupTypeCode`    | Code: `D`=Full, `I`=Differential, `L`=Log             |
| `BackupType`        | Readable description of the backup type               |
| `BackupSizeMB`      | Backup size in megabytes                             |
| `BackupLocation`    | Physical location of the backup file                  |
| `server_name`       | Name of the SQL Server instance                       |
| `recovery_model`    | Recovery model of the database during the backup      |

---

### Use Case:
- Verify recent backups by size, type, or date
- Check which databases are being backed up and how often
- Identify missing or unusually large/small backups
- Use for compliance and reporting

---

### 💡 Tips:
- To show only **full backups**, uncomment:
  ```sql
  -- bs.type = 'D'
  ```
- To list backups for **just one database**, add:
  ```sql
  AND bs.database_name = 'YourDatabase'
  ```


