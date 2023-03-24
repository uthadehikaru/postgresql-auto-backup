# PostgreSQL Auto Backup

## description

this script is based on postgresql wiki [here](https://wiki.postgresql.org/wiki/Automated_Backup_on_Linux)

i modified the script to easy configuration like only selected databases to backup.

## requirement

- to make this script running, you need to make this script running without password confirmation.

You have four choices regarding the password prompt:

1. set the PGPASSWORD environment variable. For details see the manual:
http://www.postgresql.org/docs/current/static/libpq-envars.html
2. use a .pgpass file to store the password. For details see the manual:
http://www.postgresql.org/docs/current/static/libpq-pgpass.html
3. use "trust authentication" for that specific user:
http://www.postgresql.org/docs/current/static/auth-methods.html#AUTH-TRUST
4. use a connection URI that contains everything:
http://www.postgresql.org/docs/current/static/libpq-connect.html#AEN42532

## How to Use

- clone this repository `git clone https://github.com/uthadehikaru/postgresql-auto-backup`
- copy file pg_backup.config.example to pg_backup.config
- edit pg_backup.config based on your preference
- execute `./pg_backup.sh` or `./pg_backup_rotated.sh`

## Cron Job (Optional)

if you want to run the backup process automatically, you can use cron job to execute the script.

this is the example that run auto backup rotated daily at 23:00
0 23 * * * /root/postgresql-auto-backup/pg_backup_rotated.sh > /root/postgresql-auto-backup/output.log 2>&1
