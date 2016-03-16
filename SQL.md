# Random SQL command snippets

* Select only the last 10 rows from a table:

`SELECT $id FROM $table ORDER BY $id DESC LIMIT 10;`
`SELECT * FROM fraud_requests ORDER BY date_added DESC LIMIT 10;`

* Backup a database:

`mysqldump -u root -p --all-databases > alldb_backup.sql`

* Backup a database and compress the backup:

`mysqldump -u [uname] -p[pass] [dbname] | gzip -9 > [backupfile.sql.gz]`

* For IVR Backups, also use --single-transaction flag and specify the (Docker) host (will probably need to mount a volume in the Docker too):

`mysqldump -u root -p -h mysql.service.consul --all-databases --single-transaction > alldb_backup.sql`

* Restore a backup (again, specify host/-h if it's in a Docker (and will also probably need to mount a volume)):

`mysql -u [uname] -p[pass] [db_to_restore] < [backupfile.sql]>`
`mysql -u root -p -h mysql.service.consul < backupfile.sql`
