# MySQL8_InnoDB_Master-Slave
This guide provides step-by-step instructions for creating backups using MySQL Enterprise Backup (MEB) and performing point-in-time recovery (PITR) in MySQL Enterprise Edition.


## Create Backup User for MySQL Enterprise Backup

```bash
mysql -u root -p

CREATE USER 'mysqlbackup'@'localhost' IDENTIFIED BY 'baCKup#y2233';

GRANT SELECT, BACKUP_ADMIN, RELOAD, PROCESS, SUPER, REPLICATION CLIENT ON *.*
TO 'mysqlbackup'@'localhost';

GRANT CREATE, INSERT, DROP, UPDATE ON mysql.backup_progress TO
'mysqlbackup'@'localhost';

GRANT CREATE, INSERT, DROP, UPDATE, SELECT, ALTER ON mysql.backup_history
TO 'mysqlbackup'@'localhost';
FLUSH PRIVILEGES;

# create directory for backup
mkdir -p /db_backup/MEB/
```

#### Take The Backup & Validate

