## Part 1
RELATIONAL MODEL

relation ≈ table
tuple ≈ row
attribute ≈ column

Relation = SET of tuples
→ row order irrelevant
→ pure relation has no duplicate tuples

tuple = relationship among values
relation = collection/set of such relationships

r ⊆ D1 × D2 × ... × Dn

degree/arity = # attributes
cardinality = # tuples

"relational" comes from mathematical RELATION,
NOT simply because tables are related.

Relational model = logical representation of data;
physical storage hidden by DBMS.


## Part 2
SCHEMA vs INSTANCE

schema = logical structure/design
instance = current data at one moment

relation schema ≈ type
relation instance ≈ variable value

schema changes rarely
instance changes often


DOMAIN

domain = set of allowed values for attribute

SQL type != full conceptual domain
INTEGER may still need CHECK constraints


ATOMICITY

attribute values treated as indivisible units

atomic does NOT mean physically unsplittable
depends on how DB treats the value

collection/list/set inside one attribute
→ usually nonatomic in classical relational model


NULL

NULL = special marker for unknown / nonexistent / not applicable

NULL ≠ 0
NULL ≠ ''
NULL ≠ 'NULL'

causes logical complications
later -> TRUE / FALSE / UNKNOWN

NOT NULL can prohibit missing values



## Part 3
Keys and entity integrity

Superkey = attributes guaranteed to identify tuples uniquely.

If K is a superkey, every superset of K is also a superkey.

Candidate key = minimal superkey; no unnecessary attributes.

Minimal does not necessarily mean the fewest attributes among all candidate keys.

Primary key = one candidate key chosen as the principal identifier.

Composite key = key containing multiple attributes.

Key validity comes from business rules, not accidental uniqueness in sample data.

Primary keys must be unique and non-NULL.

A candidate key must guarantee uniqueness in every valid instance.

Minimality means removing any attribute destroys that guarantee.

The entire tuple is unique in a pure relation, but that doesn't mean a subset of its attributes is necessarily unique.

Business rules determine which attribute combinations are keys.

Attribute semantics matter: Fall and Fall 2025 convey different identifying information.



## Part 4
Foreign keys and referential integrity

A foreign key references a key in another relation (or the same relation).

Referencing relation = contains the foreign key.

Referenced relation = contains the referenced key.

Foreign-key values may repeat.

Foreign keys may allow NULL unless prohibited.

Composite foreign keys must match the entire referenced key combination.

Referential integrity ensures references point to existing tuples.

An FK from A to B does not automatically require every tuple in B to be referenced by A.

Deleting or updating referenced tuples may be restricted, cascaded, or handled by setting referencing values to NULL or defaults.

Entity integrity vs referential integrity

Primary keys identify tuples within their own relation.

Foreign keys establish references to keys in another relation or the same relation.

A valid foreign key must match an existing referenced key, unless permitted to be NULL.

Composite foreign keys match combinations of values.

Primary-key uniqueness and foreign-key validity are separate constraints.

A foreign key from A to B doesn't ensure every tuple in B is referenced by A.

Deleting referenced rows may be rejected or trigger an explicitly configured action.



### Part 5

## Stage 1
Selection (σ)

Filters tuples according to a predicate.

Preserves every attribute of the input relation.

Example: σ
credits=4
	​

(Course).

Projection (π)

Retains specified attributes.

Eliminates duplicate resulting tuples in pure relational algebra.

Example: π
dept_name
	​

(Course).

Composition

The output of a relational operation is another relation.

Operations can therefore be nested.

An outer operation can only use attributes that remain in its input relation.

SQL ordinarily retains duplicates; DISTINCT removes them.


## Stage 2
Cartesian product R×S: all possible pairs of tuples.

Cardinality: ∣R×S∣=∣R∣×∣S∣.

Join: combines tuples satisfying a matching condition.

Equijoin: join using equality conditions.

Natural join: matches all identically named attributes and retains one copy of each.

Natural join can produce unintended results when unrelated attributes have the same name.

A foreign key validates references; a join combines data during querying.

Cartesian product combines every tuple of one relation with every tuple of another.

Equijoin = Cartesian product followed by an equality-based selection.

Natural join matches all attributes that share a name.

Natural join merges the shared attributes into single result columns.

Identically named attributes can have different meanings, producing unintended matches.

Foreign keys enforce valid references; joins retrieve and combine information.

Relational operations can be composed to express complex queries.



