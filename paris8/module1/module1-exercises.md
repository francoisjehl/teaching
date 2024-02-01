# Module 1

# Exercise 1: PosgtreSQL Pages

1. Connect to your instance with **pgadmin** and create a database
2. Create a table containing only one `VARCHAR` column, insert `'Hello World!'` in this table.
    - 💡 do not forget to `CHECKPOINT`!
3. Query the `pg_database` table to find the OID (Object Identifier) of your database
4. Exec into your database container. Go to `/var/lib/postgresql/data/base/` and find the folder containing your database. What is inside?
5. Find the file for your table using `pg_relation_filepath()`. Use the `du -sb` command to check its size in bits. What is this size? Why?
6. Install `hexdump` in the container using `apt update && apt install bsdmainutils`
7. Run `hexdump -C` on your table file. What do you see?
8. Insert another value in the table. Check again.
    - 💡 do not forget to `CHECKPOINT`!
9. Same question with a `NULL` value
10. Now delete the whole table and check again. What is happening? How could you fix this?

# Exercise 2: Statistics
1. Connect to your instance with **pgadmin** and create a database or use an existing one
2. Create a table. Insert many records in the table using the `generate_series()` function.
3. Check the estimated cardinality of your table with 

```SELECT reltuples AS estimate FROM pg_class where relname = '<your_table>';```

4. Check the collected statistics in the `pg_stats` table
5. Run `ANALYZE <your_table>`
6. Check again the previous queries. Try again the entire flow to see how often things are updated.

## Questions
- What is the purpose of the `ANALYZE` command?
- What is inside `pg_stats`? How does this help for query execution?

# Exercise 3: The Write-Ahead Log (WAL)

1. Connect to your instance with **pgadmin** and create a database or use an existing one
2. Install the extension `pg_walinspect` with `CREATE EXTENSION`
3. Create a table of any structure
4. Write down the current LSN with `SELECT pg_current_wal_lsn()`
5. Interact with your table: insert a few lines for example.
6. Note the new LSN with `SELECT pg_current_wal_lsn()`
7. Use the `pg_get_wal_records_info()` function to get all the WAL records between the two LSNs you noted.
8. Try different operations (insertions, deletions, updates). 

## Questions

- Describe the output of the `pg_get_wal_records_info()` function. What information does it extract from the WAL?