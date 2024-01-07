SQL Notes
----

# Setting up PostgreSQL

The start the server on WSL, run: 
```bash
sudo service postgresql start
```

## Initial preparation of database

The example Country Club database can be added by creating a new database and running the script:
```bash
createdb -U postgres country_club
psql -U postgres -f country_club_db.sql country_club
```
Note that the `-f` flag indicates a script to be run. Scripts can also be run inside the client with `\i script.sql`. The `-U` flag signals the user: `postgres` is the default admin. If the role of the system user has been updated with write privileges, the script can be run without `-U`.

Note that to access the database through PSQAlchemy, it is necessary to add the system user name as a role in the database:
```bash
psql -U postgres country_club
```
Then, within the PSQL command line:
```sql
-- if role not yet created
CREATE ROLE mark LOGIN; -- replace as necessary
GRANT pg_read_all_data, pg_write_all_data TO mark;
```