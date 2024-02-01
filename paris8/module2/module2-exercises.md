# Exercise 1: Statistics
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