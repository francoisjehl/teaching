---
marp: true
theme: gaia
paginate: true
footer: 'François Jehl - Databases - Module 0'
style: |
  section {
    background-color: #fefefe;
    color: #333;
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
  blockquote {
    background: #ffedcc;
    border-left: 10px solid #d1bf9d;
    margin: 1.5em 10px;
    padding: 0.5em 10px;
    font-size: 25px;
  }
  blockquote:before {
    content: unset;
  }
  blockquote:after {
    content: unset;
  }
  section.lead h1 {
    text-align: center;
  }
  footer {
    font-size: 20px;
    font-style: italic
  }
  section::after {
    font-size: 20px;
  }
---
<!-- _class: lead -->
# **Module 0**
History of Databases

---

# **Database System**
What would be __your__ definition?

---

# **Database System**

A commonly accepted definition would be
>  **Database**: a system that can handle _arbitrary_ datasets

Any idea in which **decade** those were invented?

---

# **1960s - IDS**

**Charles Bachman** joins **General Electric** to work on what is commonly accepted as the first ever **DBMS** (**D**ata**b**ase **M**anagement **S**ystem) named  **Integrated Data Store** a.k.a. **IDS**

![bg right:33%](assets/bachman.jpg)

He received the **Turing Award** in 1973

---
# **Yes, GE was selling this in 1964 ⤵️**
![center height:400px](https://upload.wikimedia.org/wikipedia/en/thumb/a/a3/GE_210_advertisement.jpg/640px-GE_210_advertisement.jpg)

---
# **IDS**

Network Database
  _(more on this later)_

![bg right](assets/ids.png)

---
# **CODASYL**

**C**onference **O**n **DA**ta **SY**stems **L**anguages

**COBOL** developers that wanted to come out with **APIs** for data storage and retrieval

**Charles Bachman** joins them in 1965, pushing many ideas from **IDS**

---
# **Network model**
Codasyl and IDS were both using this model

![center height:350px](assets/network.png)

---
# **Hierarchical model**

At the same time, another competing approach was the so-called **Hierarchical** Model

Pushed by IBM's **Information Management System** or IMS

![bg right:33%](https://upload.wikimedia.org/wikipedia/commons/thumb/1/16/Apollo_11_Launch_-_GPN-2000-000630.jpg/480px-Apollo_11_Launch_-_GPN-2000-000630.jpg)

Any idea why this was used? (tip on the right)

---
# **Hierarchical model**
Think of an **xml**, **json** or **yaml** file

![center height:350px](assets/hierarchical.png)


---
<!-- _class: tip -->

# **Edgar Codd**

![bg right:33%](https://upload.wikimedia.org/wikipedia/en/5/58/Edgar_F_Codd.jpg)

Mathematician, working at IBM

Had the idea of an abstraction over the way data is **physically** stored

The **Relational Model**

---
# **Edgar Codd**

![bg right:33%](https://upload.wikimedia.org/wikipedia/en/5/58/Edgar_F_Codd.jpg)

 **A Relational Model of Data for Large Shared Data Banks** is published in 1970

One of the **most fundamental** papers in CS history

> 💡I strongly advise you to read it

---
# **Moving to relational in the 70s**

 **IBM** develops **System R** following Edgar Codd's work

**Michael Stonebraker** starts **Ingres** at UC Berkeley and later quits to commercialize it

**Larry Ellison** founds **Oracle**

---
# **Market overtake in the 80s**

**IBM** finally ships **DB2**

**Oracle** becomes the leader

Stonebraker comes back to Berkeley to start a new project named **Postgres**

---
# **A few events in the 90s**

**Microsoft** enters the market following some high level of drama

**PostgreSQL** is Postgres with SQL support

**MySQL** is created

**OLAP Cubes** are the brand new hot thing, following Essbase

---
# **The "Internet Era" changes everything**

Data volumes **explode** in the early 2000s

**Big Tech giants** start to look for other ways to manage data 

---
# **BigTable**

![bg right:33%](assets/dean.jpg)
**Jeff Dean** from **Google** published  _Bigtable: A Distributed Storage System for Structured Data_ in 2006

---
# **Dynamo**

**Amazon** published _Dynamo: Amazon’s Highly Available Key-value Store_  in 2007
It was meant to replace **Oracle** there

>About 70 percent of operations were of the key-value kind, where only a primary key was used and a single row would be returned. About 20 percent would return a set of rows, but still operate on only a single table.
>
>**Werner Vogels**
---
# **Dynamo-style databases**

e.g. **Cassandra**

- All nodes are equal and there is no leader
- Consistent hashing is used to ensure distribution
- Data is replicated at least once

---
# **MapReduce**

![bg right:33%](assets/dean.jpg)

**Jeff Dean** - him again ! -published _MapReduce: Simplified Data Processing on Large Clusters_ in 2004

 **MapReduce** is a programming model using two functions
```
map(k1, v2) -> list(k2, v2)
reduce(k2, list(v2)) -> list(v2)
```
---
# **Rise (and fall) of Hadoop**

**Yahoo** open sources its implementation of MapReduce.
All those projects become the Hadoop ecosystem.

![center](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Hadoop_logo.svg/664px-Hadoop_logo.svg.png)

---
# **Stonebraker disagreed**
> 💬 _MapReduce represents a **giant step backwards**. The database community has learned the following three lessons since [...] 1968_
>1. _Schemas are good_
>2. _Separation of the schema from the application is good_
>3. _High-level access languages are good_
>
>_MapReduce has learned **none** of these lessons and represents a **throw back to the 1960s**_
>
> **Michael Stonebraker** - _MapReduce: A major step backwards_ - 2008

---
# **CStore**
![bg right:60%](assets/stonebraker.png)

---
# **CStore**
Storing in columns is **way** more efficient for analytic workloads
![center height:350px](assets/columnar.png)

---
# **Massively Parallel Data Warehouses**

Stonebraker - again - leaves research to start a database company named **Vertica**

Some others will implement the same idea (e.g. **Paraccel**)

---
# **Columnar Everywhere**

**Apache Parquet** will be started by Twitter and Cloudera as a columnar filesystem for Hadoop clusters in 2013

It is still the most popular columnar file format, supported by pretty much anything

---
# **Distributed SQL**


![bg right:33%](assets/dean.jpg)

**Jeff Dean** - him again! - publishes _Spanner: Google’s Globally-Distributed Database_ - in 2012
- Multi-version
- Distributed
- Synchronously-Replicated

This led to multiple implementations 

---
# **Cloud Native**
Using object stores à la **S3**

Nodes as containers with attached disks for **caching**

Common Services - catalog and/or scheduler - hosted on **KV store**

---
<!-- _class: lead -->
# **Latest Trends**

---
# **Specialized Engines**

**Graph** databases for all use cases that require n-way joins, e.g. **Neo4J**

**Embedded Column Stores** such as **DuckDB**

**ML engines** such as **Chroma** to store Vectors / Embeddings

---
# **Relational databases aren't dead**

![center height:350px](assets/dbengines.png)

---
# **To be continued...**

![bg right:40%](assets/nosql.jpeg)


