## Config file
- C:\Program Files\ManageEngine\PAM360\pgsql\data
   * postgresql.conf
   * pg_hba.conf
   * pgdata (Main Database)
 
 ---------------------------------------------------------------------------------------------------
 ## Export and Import Database
- remove password in config file and after that
 * cd C:\Program Files\ManageEngine\PAM360\pgsql
```
psql -U postgres -h localhost -p 3456
```
- show list database
```
psql -U postgres -p 3456 -l
```
- Export:
```
pg_dump -U postgres -p 3456 -F c -b -v -f "D:\pam360_backup.dump" PAM360
```

- Import in new server:
  * copy export file in d:\
  * cd C:\Program Files\ManageEngine\PAM360\pgsql
```
pg_restore -U postgres -p 3456 -d PAM60 -v "D:\pam360_backup.dump"
```
  
