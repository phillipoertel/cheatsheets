# show tables

\dt

# use database

\c[onnect] DBNAME

# drop db with connections
UPDATE pg_database SET datallowconn = 'false' WHERE datname = 'mydb';
-- ALTER DATABASE buzzn_staging CONNECTION LIMIT 100;
SELECT pg_terminate_backend(pid)
FROM pg_stat_activity
WHERE datname = 'buzzn_staging';
DROP DATABASE buzzn_staging;
# like

- use single quotes
... like '%foo%'

# regex

- ~ '(foo|bar)'
- !~ '(foo|bar)'

# select into outfile

\o /tmp/page_paths.txt

# terminate / kill query

SELECT pg_cancel_backend(7345);
SELECT pg_terminate_backend(7345)

# list current queries

SELECT * from pg_stat_activity

