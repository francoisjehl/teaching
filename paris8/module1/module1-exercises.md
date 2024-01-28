# Module 1

# Exercise 1: Your own key-value store

1. Create a bash script named `mydb.sh`. This script accepts three parameters, `make`, `set` and `get`:
    1.  `./mydb.sh make [database]` creates a `database` (actually an empty file in the current directory with the name supplied)
        - 💡 you could use `touch`
    2.  `./mydb.sh set [database] [key] [value]` inserts a record with the supplied `key` and `value` and stores it on a line in the `database` file
        - 💡 you should use `>>`
    3.  `./mydb.sh get [database] [key]` returns the current record with the supplied `key` in the `database`. If multiple records exist with the same key, it should only return the **last one**. If none exist, it should return `NULL`
        - 💡 you should use `grep`, `sed` and `tail`
2. Insert some records in a database and check the functionality
    - What is the worst-case complexity of each operation? 
    - Explain.
3. Implement a new endpoint: `./mydb.sh del [database] [key]` that deletes the record with the supplied `key` in the `database` so it will appear as `NULL` the next time you `get` it.
    - What could be at least two different approaches to implement this?
        - 💡do you **really** need to **actually** delete the data?
    - What would be their performance characteristics?
4. Benchmark your implementation in terms of average operations per sec for get, set and del
    - 💡you can use commands such as `openssl rand -hex 16` to generate random strings


# Exercise 2: Setup your development environment