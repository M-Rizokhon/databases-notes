# Part 1
DB = collection of related data
DBMS = software managing/accessing that data

Why DBMS?
File-processing systems cause:

1. Redundancy → duplicated facts
2. Inconsistency → copies disagree
3. Difficult querying → custom program per new request
4. Data isolation → scattered formats/files
5. Integrity problems → rules hard to enforce globally
6. Atomicity problems → partial operations after failure
7. Concurrency anomalies → simultaneous correct operations interfere
8. Security problems → permissions difficult to coordinate

Core idea:
DBMS centralizes management of shared persistent data.

DBMS ≠ just "tables".
It provides querying + constraints + concurrency +
transactions + recovery + security + storage management.

A DBMS centralizes common data-management responsibilities so every application does not have to solve them independently.





# Part 2
Data abstraction = hide unnecessary DB details.

3 levels:

View:
- what a specific user/application sees
- may expose only part of DB

Logical:
- what data exists
- attributes + relationships + constraints

Physical:
- how data is actually stored/accessed
- files, pages, indexes, storage structures

Schema = database design/structure
Instance = database contents at one moment

Schema changes rarely
Instance changes frequently

Physical data independence:
change physical storage
without changing logical schema/apps

Logical data independence:
change logical schema
without changing external views/apps    


# Part 3
Data model:
conceptual tools for describing
- data
- relationships
- semantics
- constraints

Main models:
- Relational -> tables/relations
- ER -> entities + relationships; mainly design
- Object-based
- Semistructured -> flexible structure

Data model ≠ schema
model = general framework
schema = specific design

DDL:
defines schema/structure
CREATE, ALTER, DROP

DML:
manipulates data
SELECT, INSERT, UPDATE, DELETE

Query language:
retrieval part of DML

Procedural DML:
specify WHAT + HOW

Declarative DML:
specify WHAT
DBMS decides HOW

SQL is largely declarative.

Key idea:
logical query != physical execution plan

Data model = vocabulary/framework for structuring data.
Schema = one specific database design built using that model.



# Part 4
DBMS internals:

Query Processor
- DDL interpreter
- DML compiler
- optimizer
- query evaluation engine

Storage Manager
- file manager
- buffer manager
- authorization/integrity manager
- transaction manager

Transaction Manager
- concurrency control
- recovery

Storage structures
- data files
- data dictionary
- indexes

Users
- naïve/end users
- application programmers
- sophisticated users
- specialized users
- DBA

Two-tier:
client -> DB

Three-tier:
client -> application server -> DB

Do NOT confuse:
data abstraction levels
with
application tiers

Recovery = correctness after failure.
Concurrency control = correctness under simultaneous execution.



# Part 5
Transaction:
set of operations forming ONE logical unit

Atomicity:
all or nothing

Consistency:
valid DB state -> valid DB state

Durability:
committed changes survive failure

Recovery:
handles failures

Concurrency control:
handles transaction interference


History:
files/tapes
 -> hierarchical/network DBs
 -> relational model
 -> modern relational/distributed/specialized DBs

Relational breakthrough:
separate WHAT from HOW

Strength:
high-level declarative querying

Challenge:
DBMS must choose efficient execution plan

Course big picture:

Logical side:
- relational model
- SQL
- RA/calculus
- design

Physical/system side:
- query processing
- optimization
- storage
- indexes
- hashing











