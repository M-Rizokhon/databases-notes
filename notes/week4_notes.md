## Part 1
NORMALIZATION — WHY?

Bad design:
- same fact stored multiple times
- redundancy → possible inconsistency

Anomalies:
1. update anomaly
   one fact change → many rows must change

2. insertion anomaly
   cannot store fact A without also having fact B

3. deletion anomaly
   deleting fact A accidentally deletes fact B

Fix:
- decompose relation into smaller relations
- BUT arbitrary decomposition can be lossy

Lossy decomposition:
- joining decomposed tables does NOT recover exactly
  the original information
- may create spurious tuples

Core principle:
store each independent fact in the proper relation

Normalization asks:
"What determines what?"
→ functional dependencies



## Part 2
FD: X → Y
same X value ⇒ same Y value
for EVERY legal instance

Important:
- X → Y does NOT imply Y → X
- FD ≠ causation
- current data pattern ≠ schema constraint

Composite FD:
AB → C may hold even if
A ↛ C and B ↛ C

Superkey:
K → all attributes of R

Candidate key:
minimal superkey

Primary key:
chosen candidate key

Trivial FD:
X → Y where Y ⊆ X

FDs come from real-world/business rules,
not merely observed data.



## Part 3

# 3.1
LOGICAL IMPLICATION

F ⊨ X → Y
means:
every legal relation satisfying F
must also satisfy X → Y

F+:
all FDs logically implied by F


ARMSTRONG'S AXIOMS

1. Reflexivity
   if Y ⊆ X
   then X → Y

2. Augmentation
   if X → Y
   then XZ → YZ

3. Transitivity
   if X → Y and Y → Z
   then X → Z

Properties:
- sound
- complete


Derived rules:

Union:
X → Y, X → Z
⇒ X → YZ

Decomposition:
X → YZ
⇒ X → Y and X → Z

Pseudotransitivity:
X → Y, WY → Z
⇒ WX → Z


# 3.2
ATTRIBUTE CLOSURE X+

X+ = all attributes functionally
determined by X under F.

Algorithm:
result = X

repeat:
    for each Y → Z in F:
        if Y ⊆ result:
            result = result ∪ Z
until no change

Uses:

1. Superkey:
   X is superkey iff X+ = R

2. Test implied FD:
   X → Y follows from F iff
   Y ⊆ X+

3. Candidate key:
   X+ = R
   AND no proper subset of X
   has closure R

Important:
F+ = set of implied FDs
X+ = set of determined attributes

Useful heuristic:
attribute never appearing on RHS
must occur in every candidate key.


Finding all candidate keys:

1. Identify attributes absent from every RHS.
   → They must occur in every candidate key.

2. Start with these mandatory attributes.

3. Add other attributes until closure = R.

4. Test minimality:
   Can any attribute be removed while
   still obtaining closure = R?

5. Prove completeness:
   Show that no other minimal keys are possible.

Remember:
- Attribute sets have no order: AB = BA.
- X+ contains attributes.
- F+ contains functional dependencies.
- A superkey need not be minimal.



# 3.3
CANONICAL COVER Fc

Goal:
Simplify F without changing its meaning.

Requirement:
Fc+ = F+

Properties:
- No extraneous attributes
- Unique left-hand sides
- Equivalent to original F

Simplifications:
1. Remove redundant FDs.
2. Remove extraneous LHS attributes.
3. Remove extraneous RHS attributes.
4. Combine FDs with identical LHS.

LHS test for X → Y:
Remove attribute a from X.
Check if Y ⊆ (X - {a})+ under F.

RHS test for X → Y:
Temporarily remove a from Y to form F'.
Check if a ∈ X+ under F'.

Canonical cover may not be unique.



## Part 4

# 4.1
1NF:
- Atomic attribute domains.
- Does not eliminate all redundancy.

BCNF:
For every X -> Y in F+:
  Y ⊆ X (trivial)
       OR
  X is a superkey.

To check X -> Y:
1. Is it trivial? If yes, OK.
2. Otherwise compute X+.
3. If X+ = R, OK.
4. Otherwise, BCNF violation.

Key idea:
Nontrivial determinants should be superkeys.

BCNF violation often signals redundancy
and update/insertion/deletion anomalies.



# 4.2
3NF: For every X -> A in F+,
at least one must hold:

1. A belongs to X (trivial FD)
2. X is a superkey
3. A is a prime attribute

Prime attribute:
Belongs to at least one candidate key.

Non-prime attribute:
Belongs to no candidate key.

BCNF is stronger than 3NF.

BCNF => 3NF
3NF does not imply BCNF.

Motivation:
BCNF may sacrifice dependency preservation.
3NF permits lossless, dependency-preserving
decomposition in all cases.



# 4.3
NORMAL FORMS

BCNF => 3NF => 2NF => 1NF

1NF:
Atomic attribute domains.

2NF:
1NF + no partial dependency of a
non-prime attribute on any candidate key.

3NF:
For every nontrivial X -> A:
  X is a superkey OR A is prime.

BCNF:
For every nontrivial X -> A:
  X must be a superkey.

Partial dependency:
Non-prime attribute determined by
a proper subset of a candidate key.

Transitive-dependency problems:
Often detected by 3NF violations.

Strategy:
1. Find all candidate keys.
2. Identify prime attributes.
3. Test normal-form conditions.
4. State the highest form satisfied.



## Part 5
- unfinished tbh
- preparing for quiz now, i don't think this part will be important.

