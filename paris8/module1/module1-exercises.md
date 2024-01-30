# Module 1

# Exercise 1: How Postgres stores pages

1. Create a database
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

You can look at https://www.postgresql.org/docs/current/storage-page-layout.html if you want to know more about the storage layout.
