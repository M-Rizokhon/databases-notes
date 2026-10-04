## Part 1
Database design starts with understanding real-world requirements.

Conceptual design: entities, relationships, attributes and constraints.

Logical design: translate the conceptual schema into a relational schema.

Physical design: decide how data is organized and accessed.

Redundancy → duplicated information and possible update anomalies.

Incompleteness → inability to represent certain required facts.

Design the meaning of the data before choosing its SQL representation.


## Part 2
# Lesson 2.1
Entity = an individual distinguishable object.

Entity set = collection of entities of the same type.

Extension = actual collection of entities at a particular time.

Attribute = descriptive property; domain = permitted values.

Simple/composite describes an attribute's internal structure.

Single/multivalued describes how many values an entity can have.

Derived attributes are calculated from other information.

Null may mean missing, unknown or not applicable.

Entity sets need not be disjoint: one person may be both a student and an instructor.

Key design principle: Model the information required by the real-world system, not simply whatever seems convenient to put into a table.


# Lesson 2.2
Relationship = a specific association among entities.

Relationship set = collection of associations of the same type.

Degree = number of participating entity sets.

Binary: two participating entity sets.

Recursive: the same entity set participates in different roles.

Ternary: three entity sets participate in one association.

Descriptive attribute = information about a particular relationship instance.

For M:N relationships, attributes determined by the participating pair belong to the relationship.

Conceptual E-R model: Enrollment is a relationship between Student and Section.

Relational implementation: Enrollment can be represented by a separate table containing foreign keys and its own descriptive attributes.


# Lesson 2.3
Recursive relationship: an entity set participates more than once, in different roles.

Roles distinguish the function of each participant.

Ternary relationship: one association among three participating entity sets.

Independent binary relationships do not necessarily preserve ternary associations.

Reconstructing an improperly decomposed ternary relationship can produce spurious combinations.

A ternary relationship can be replaced by an entity representing the complete association, together with appropriately constrained binary relationships.

Relationship attributes describe a particular association, not necessarily any participating entity alone.




## Part 3
# Lesson 3.1
Mapping cardinality = maximum number of entities associated through a relationship.
1:1 → each side associates with at most one on the other side.
1:N → one A can relate to many B; each B to at most one A.
N:1 → same relationship viewed in reverse.
M:N → both sides may relate to many.
Always analyze the relationship in both directions.
Cardinality is about maximum participation, not whether participation is required.
“Exactly one” combines cardinality + participation.
- a minimum of 1 indicates total participation, while a maximum of 1 indicates “at most one.” The two dimensions are separate.

# Lesson 3.1 & 3.2 & 3.3
Cardinality = maximum number of related entities.
Participation = whether participation is mandatory.
min = 1 → total participation.
min = 0 → partial participation.
max = 1 → at most one.
max = * → many allowed.
M:N relationship key → union of participating entity keys.
1:N or N:1 relationship key → key of the many side.
1:1 relationship → either side’s key can serve.
Relationship descriptive attributes do not determine relationship identity.



## Part 4
# Lesson 4.1
Strong entity → has its own primary key.
Weak entity → lacks a full key of its own.
Owner/identifying entity → strong entity that helps identify weak entity.
Discriminator/partial key → distinguishes weak entities belonging to the same owner.
Weak entity key = owner PK + discriminator.
Identifying relationship is many-to-one from weak entity to owner.
Weak entity has total participation in identifying relationship.
“Weak” refers to identification, not importance.



# Lesson 4.3
Specialization = top-down: superclass → subclasses.
Generalization = bottom-up: subclasses → superclass.
ISA means every subclass entity is also a superclass entity.
Subclasses inherit superclass attributes.
Subclasses also inherit superclass relationship participation.
Disjoint = at most one subclass.
Overlapping = multiple subclasses allowed.
Total = every superclass entity belongs to a subclass.
Partial = some superclass entities may belong to none.
Disjoint/overlapping and total/partial are independent constraints.

Aggregation is an abstraction where an existing relationship, together with its participating entities, is treated as a higher-level entity-like object so it can participate in another relationship.



## Part 5
Rectangle = entity set
Diamond = relationship set
Underline = primary key
Double line = total participation
Double diamond = identifying relationship for weak entity
Relationship attributes belong to the relationship
Cardinality tells max participation
Participation tells minimum participation
Build diagrams from requirements in this order:1. entities
2. attributes
3. keys
4. relationships
5. cardinality
6. participation



## Final notes
E-R model = conceptual database design.
Entity set = type of real-world object.
Relationship set = association among entity sets.
Attributes can be simple, composite, multivalued, or derived.
Cardinality = maximum association: 1:1, 1:N, N:1, M:N.
Participation = minimum association: total or partial.
Weak entity = needs owner PK + discriminator for identification.
Relationship attributes describe a specific association.
Repeated events with the same participants may need their own entity.
Specialization/generalization = ISA hierarchy + inheritance.
M:N → separate relation.
1:N → FK usually placed on N side.
Weak entity → owner PK becomes FK and part of PK.
Composite attributes → flatten.
Multivalued attributes → separate relation.
Derived attributes → usually not stored.


