# Exercise 1: Are you still good at SQL?

1. Given those two simple tables:

| Animal   |
| -------- |
| Dog      |
| Lion     |
| Elephant |

| Animal |
| ------ |
| Cat    |
| Tiger  |
| Dog    |

Which query would give the following output?

| Animal   | Animal |
| ---------|--------|
| Dog      | Dog    |
| Lion     | `NULL` |
| Elpehant | `NULL` |
| `NULL`   | Cat    |
| `NULL`   | Tiger  |

2. Let's define an `ExamResults` table

| Student  | Ewam  | Pass?   |
| ---------|---------|-------|
| Steve    | Maths   | true  |
| Steve    | Physics | true  |
| Steve    | English | false |
| Steve    | CS      | true  |
| Eleanor  | CS      | false |

Knowing that to pass in next year, students have to pass all the exams in the `MandatoryExams` table:
| Exam     |
| -------- |
| Maths    |
| Physics  |
| CS       |

How can you output the list of distinct students, with a boolean indicated that they passed their year or not?
(There are **many** solutions here)


3. A query to debug

The following query is producing "wrong results": users complain that some clients do not show up. Moreover, the average_order_amount value is different that in another query that uses the `AVG()` function.
FInally "cost" metric is also completely **wrong**.
How would you fix it?

```
SELECT
  customer_name
  SUM(o.amount) / COUNT(0) AS average_order_amount,
  SUM(o.shipping_cost + o.cost) AS cost
FROM
  customers c
  LEFT JOIN orders o
  ON o.customer_id = c.customer_id
WHERE 
  o.amount < 10000
  AND
  c.country IN ('France', 'UK', NULL)
GROUP BY
  customer_name
```

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