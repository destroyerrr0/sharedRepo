---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Data Modeling ^hYydzSZt

how data should be structured, related, and constrained before storing or using it. ^cYGKvWHW

Represent what we have ^ranbZcrD

structure what we have ^cviZfQrZ

store what we have ^wWDs9XLl

Some data models ^rjY0t7gN

What ^s5uDmr5c

Mindmap ^KvuaJVik

Engineering model is 
simplified representation of real world systems 
use to analyze, design and understand
real world systems ^DlNEfver

Why ^jaz3ZXdP

Real things are
1. messy
2. expensive
3. big
4. does not exists ^GJi6MBc6

Engineering model : Real system :: Data model : Real-world data ^WcXNrgST

Bad requirements / specifications 
=> Bad engineering model

-> soln -> conceptual modeling ^E9FO3EYe

Meta and entity schema ^2ikLwKXG

a process of abstracting data into meaningful concepts from the domain and structuring them using specific notations ^iWaKigj2

collection of concepts 
to help model data ^67IAMuCa

avoid direct interaction with
data as much as possible
done using terminologies and
notations ^6lmO3xwr

structural desc. of data created
using concepts and notations defined
in a particular data model
eg relational schema -> relational data model ^p2jeGDjy

Database design is realized using a schema

Database design includes:
        •        Requirement analysis
        •        Conceptual modeling (ER)
        •        Logical modeling
        •        Normalization
        •        Physical design (indexes, storage)
        •        Performance planning
 ^nUOIEKZN

Database is the repository that stores data

The structure of the repository conforms with a particular database design ^20atPk2h

converting 1 types of schema to another
eg - er schema -> relational schema ^Jx4XCTCm

Visual Modeling ^FgcDS12u

Engineering designs/models can be very hard to communicate

eg- Entity has attributes, 
attributes may be composite, 
relationships have cardinality, 
constraints are defined at meta level… ^JMPIgmFT

Soln -> Visual Modeling ^hu9GppEH

---> ER or UML diagrams can help ^Tcyr6CNf

---> Student ——(1..*)—— enrolls ——(0..*)—— Course

Visual Modeling exposes missing cardinalitites, cycles, wrong participation, orphan entities ^meIRtQmg

Textual Modeling ^kBHXGa9M

Errors can also be hard to detect when expressed in words

eg- Student must enroll in at least one course.
Course may have zero students. ^zvLnToJp

- Process of abstracting reality into pictures ^vG63zdAs

- We use visual modeling as a debugging tool ^XWzL4E1P

- if you can't draw your model clearly, you don't understand it clearly ^QxletVQv

Element of data Modeling ^N49s9jX4

A complete data model must define: ^gQWiLudN

Structure, Operations, Mapping / transformation ^NfBZBFE2

1. Terminology (structure + sematics) ^CXmM7z39

- vocab or grammar of the modeling language
- defines what is an entity, attribute, relation,     
  primary or foreign key ^ZlEfhJAM

2. Working of Data (Operations) ^0xZKvnBU

- what operations we can perform 
- or, how do we manipulate the data
- DDL, DML etc ^MqQYUHEC

3. Data transformations (mapping rules) ^ceZXETeq

- how to move from one model to another
- mapping or transformation rules between 
  different data models
- ER -> Relational (ER-to-Relational Mapping),
  Relational -> Physical schema, 
  OO -> Relational ^7GJyuuNX

4. Abstraction (Physical, Logical, Conceptual) ^GHBd1jzE

- Physical -> Storage stucts, indexes, files
- Logical -> Schema
- Conceptual -> ER diagrams ^dVXjQ39S

5. Implementation differences ^6ckRxacl

- Each model has its strengths based on its implementation.

- Relational :-
    - strong -> Consistency, Structure
    - struggles -> deeply nested data, graph-heavy relationships 

- Graph :-
    - strong -> traversal, deep networks
    - struggles -> joins, unions

- Document model :-
    - strong -> flexible schema, hierarchical data
    - struggles -> constraints ^bw7UEVF6

Why not 1 universal data model? ^tbRTapnB

Russian doll ^TJ3R9qEm

single global element ^IAlOjeQ1

less coupling, no namespace problem ^7Evy9AWu

no-reusability ^k6HbxETW

Salami slice ^IZjDn2tB

all global elemeent, combined using ref ^cg3tlJwk

more coupling, namespace problem ^oIRU3C19

high reusability ^vniPRJU0

Venetian blind ^ckCKJkgu

1 global element and all global types ^yOMS2zwm

less coupling, no namespace problem, high reusability ^IqbERYCs

View level → How users see specific parts of data ^4YaJ6Urj


Logical level → How data is structured (tables, rows, columns) ^ZirJZkcP

Users should not care how it is implemented internally. ^rjLKooHn

At physical level we care for speed, optimization, performance and indexing. Hence we use internal structure like hash tables B+ trees, pointers, etc. Relational Model separates - Physical Level and Logical level - Physical Data Independence. Internal storage can be anything for performance-change storage format, indexing and file organization. Users must interact with only tables. ^YjGqQI7i

Physical level → How data is actually stored internally.
 ^CB88K8Ap

Why at only at logical level?  ^And5cwES

Rule-0: “For any system that is advertised as, or claimed to be, a relational database management system, that system must be able to manage databases entirely through its relational capabilities.”  ^GSdoddfe

If a system claims to be RDBMS it must allow user to create tables, insert data, update data, delete data and query data using only relational concepts. It must not require non-relational concepts like file handling, pointer manipulation and procedural tricks to manage database. ^sivB7dUA

Rule-2: Guaranteed Access Rule
“Each and every datum (atomic value) in a relational data base is guaranteed to be logically accessible by resorting to a combination of table name, primary key value and column name.”  ^D09GMLnJ

Reach any cell logically without physical details.
Ensures-
No hidden navigation
No dependence on physical storage 
No pointer chasing ^5xFaf9Ne

Rule-3: NULL Values
"Null values (distinct from the empty character string or a string of blank characters and distinct from zero or any other number) are supported in fully relational DBMS for representing missing information and inapplicable information in a systematic way, independent of data type.”  ^uWVw1NMg

NULL values represent missing or inapplicable information independent of data type.
Without NULL:
Missing data would mix with actual values.
Data Integrity Issue. (eg. Rahul's salary is not known but we stored 0. Avg salary calculations go wrong. Reports show employee earning 0 salary.  --> Incorrect values affect results.)
NULL!=NULL 
 ^9WOYhIEf

Rule-5: Data Sublanguage
"A relational system may support several languages and various modes of terminal use (for example, the fill-in-the-blanks mode). However, there must be at least one language whose statements are expressible, per some well­ defined syntax, as character strings and that is comprehensive in supporting all of the following items: 
-Data definition 
-View definition 
-Data manipulation (interactive and by program) 
-Integrity constraints 
-Authorization 
-Transaction boundaries (begin, commit and rollback)”  ^5wkaBBKx

A relational DB must have at least one complete relational language(like SQL) that  supports DDL, DML, views, constraints, authorization and transactions. ^hzP8sJT0

Rule-4: Online Catalogue
"The database description is represented at the logical level in the same way as ordinary data, so that authorized users can apply the same relational language to its interrogation as they apply to the regular data.”  ^iOdIvTz7

The database description(metadata) must be stored at logical level just like normal data so users can query it using same relational language(SQL).
Metadata includes-Table names, column names, data types, constraints, keys, views. This info is stored in System Catalogue/ Data Dictionary.
DB becomes self-describing. ^PpfvYJzo

Rule-1: The information Rule
“All information in a relational database is represented explicitly at the logical level and in exactly one way — by values in tables.”  ^IxcSwsKp

If RDBMS everything is stored in tables. Data is stored as rows(tuples), columns(attributes) and cells. There should be no hidden storage structure like LL, pointers, file paths or object references. Also at logical level everything must appear as tables only.
Ensures- Uniform structure, no hidden data, easy SQL querying ^jnAk4nI1

What vendors were doing  ^vGykXP84

- Claimed to be RDBMS
- But required pointer navigation
- Or required procedural access
- Or required special file commands ^hrh5KVg4

What it solved ^8ypocHSX

- Provide full SQL support
- Not rely on non-relational backdoors
- Respect abstraction ^IjjmNO4Y

Relational database manage everything only using relational capabilities ^iTz56xoU

What vendors were doing  ^EXOBtHKs

- Some data stored in tables
- Some stored in system files
- Some stored in pointers
- Some hidden in metadata structures ^Vgoi1f34

What it solved ^pV0tbMmb

- Uniform data representation
- No hidden structures
- Simpler querying
- Logical clarity ^85yKRXSK

All Information at logical level represented in one way => by values in table ^CWihrZj0

What vendors were doing  ^RIEEYAFj

- Navigation though pointers
- Traversal through structures
- Know physical path ^OmwElNhx

What it solved ^OU8bwh1Q

- No pointer chasing
- No physical dependency
- Logical data independence
- True abstraction ^Hqe5OatP

All the data should be logically accessible using table name, pk and column name  ^37f6Qo4S

What vendors were doing  ^tQjUAjoU

- 0, Blank string
- Special codes like -999
- Fake values ^VuH7aeUO

What it solved ^26rjMALm

- Represent missing or inapplicable information
- Be independent of data type
- Be distinct from 0, blank, empty string ^gHiIAALg

NULL values only represent missing info and inapplicable info, independent of the data type ^FbeYNTp7

What vendors were doing  ^Bwh3C3l0

- Stored in hidden files
- Accessible only through special commands
- Not queryable using relational language ^RGhiwn7K

What it solved ^iXbiBbrF

- Database becomes self-describing
- Uniform access
- No hidden structures
- Tools can introspect schema ^j8R3OdLM

At logical level Meta-data should be represented, accessed and manipulated like the normal data  ^EAqvbZBb

What vendors were doing  ^zx227QyT

- Had SQL for querying
- But separate tools for DDL
- Separate commands for transactions ^Ao3h4903

What it solved ^dinNz2ZB

- Uniform system control
- Transaction safety
- Logical completeness
- No fragmentation of operations ^FbOgXyEa

There must be at least one language tht supports, DDL, DML, DCL, view, constraints and transactions ^XuDsMlU1

Rule-8: Physical Data Independence
"Application programs and terminal activities remain logically unimpaired whenever any changes are made in either storage representations or access methods.”  ^97EJQlVJ

Users work at logical level. Storage happens at physical level. If we change file structure, indexing methods, storage formats, hashing techniques then application code and SQL should not change. These two level should be independent.  ^vMzzwGFh

Rule-6: View Updating Rule
"All views that are theoretically updatable must also be updatable by the system.”  ^FmivGrCk

If a view is logically safe to update without ambiguity then DBMS must allow-insert, update, delete. Rule is controversial-No algorithm exists that can decide for every possible view whether it is updatable.
Without this rule-
Developers must always update base tables directly. views becomes read-only. This reduces abstraction power.
 ^0lxgucTi

Rule-7: Full DML
"The capability of handling a base relation or a derived relation as a single operand applies not only to the retrieval of data but also to the insertion, update and deletion of data.”  ^fQOLVA2W

Operations Should work on set of rows(entire relations)- not one row at a time. This applies to-SELECT, INSERT, UPDATE and DELETE. Relational Model is set-based, not record by record. You should not need loops to update multiple rows.
Without this rule-
-Performance issues
-Procedural Complexity
-Loss of relational abstraction(You say WHAT you want, not HOW you want.)
-Becomes navigation-based DB
 ^S9YP0NZW

Rule-9: Logical Data Independence
Application programs and terminal activities remain logically unimpaired whenever information-preserving changes of any kind that theoretically permit unimpairment are made to the base tables.
'The physical and logical independence rules permit database designers for relational DBMS to make mistakes in their designs without the heavy penalties levied by nonrelational DBMS. This, in turn, means that it is much easier to get started with a relational DBMS because not nearly as much performance-oriented planning is needed prior to "blast-off".' 
 ^TXQew355

If we change the logical structure of tables
(but do NOT lose information-doesn't delete data, doesn't change meaning, only reorganizes structure),
Applications and queries should continue to work.



Logical data independence is harder because applications directly depend on the logical schema, while physical details are hidden by the DBMS.

Physical changes happen below the logical model.
Logical changes happen inside the logical model —
and applications directly depend on it.

So hiding logical change is much more complex. ^HguDME2D

Why Logical Independence is Harder than Physical Independence? ^Vo6PZk6k

What vendors were doing  ^4Tt094Y4

- Read-only views
- But not updatable views ^m3tzUEj2

What it solved ^XJh6iqaV

- Preserved abstraction
- Allowed logical data independence
- Encouraged use of views safely ^6pbbLkaC

One should be able to update the views which are theoretically updatable ^QTPYVCZl

What vendors were doing  ^WPkvi2XU

- One row at a time
- Record-by-record loops
- Procedural updates ^gRdSwFjv

What it solved ^yOoxZMHG

- True set-based processing
- Performance optimization
- Declarative power
- No procedural dependence ^EgpSBuTG

DML operations should process in a single go similar to data retrieval operations ^oi831Dle

What vendors were doing  ^woYNL3VG

Changes to these broke the sytem
- File structure 
- Index
- Storage format ^K51w6mZD

What it solved ^HBYpcMDi

- Flexibility
- Scalability
- Performance tuning without rewriting apps ^AfywH464

Changes at physical level should not affect mechanisms at logical levels ^iQd4w7q8

What vendors were doing  ^mvqa1yvp

Applications broke when
- Add column
- Split table
- Normalize schema ^smmSoEKc

What it solved ^Rdi3eGv1

- Reduced Application Fragility
- Strengthened Abstraction
- Enabled Schema Evolution ^RHRcTDTY

Changes(restructuring) at logical level should not affect applications and queries at view level ^3JCoC3OE

Rule-10: Integrity Independence
Integrity constraints specific to a particular relational data base must be definable in a relational data sub-language and storable in the catalog, not in the application programs. 
'In addition to the two integrity rules (entity integrity and referential integrity) that apply to every relational database, there is a clear need to be able to specify additional integrity constraints reflecting either business policies or government policies.' 

 ^2j2fBqTF

Integrity Constraints-metadata(rules that keep data valid and correct) must be definable in relational language and stored in system catalogue-not inside application programs.
Entity Integrity-PK, Referential Integrity-FK, Business Constraint- salary>0, Gov Constraint-age>=18 all must be stored in system catalogue.
Without this rule-
-business logic scattered in multiple apps
-no central control ^gNTVhX4D

Rule-11: Distribution Independence
A relational DBMS has distribution independence. 
By distribution independence I mean that the DBMS has a data sub­language that enables application programs and terminal activities to remain logically unimpaired: 
when data distribution is first introduced (if the originally installed DBMS manages non-distributed data only); 
when data is redistributed (if the DBMS manages distributed data)' 


 ^hugNnyrq

A relational DBMS must ensure that applications remain unaffected when data is distributed across multiple locations. Users should not know where the data is physically stored.

If data is:
Moved to another server, Partitioned across sites, Replicated, Sharded
Application programs should NOT change.
Users should not know where the data is physically stored.
Applications should think: “Data is in one database”
 ^5cekLdwV

Rule-12: Non-subversion Rule
If a relational system has a low-level (single-record-at-a-time) language, that low level cannot be used to subvert or bypass the integrity rules and constraints expressed in the higher level relational language (multiple­records-at-a-time). 



 ^9Ge62Knr

If the DBMS provides:
-High-level SQL (set-based)
-AND some low-level access (record-by-record, internal APIs, storage-level access)

The low-level access must NOT break rules like: PRIMARY KEY, FOREIGN KEY, CHECK, NOT NULL, Authorization.

How Low-Level Utilities Could Bypass Constraints- ^ZAqkCLje

## Embedded Files
44b157e4151388209140dc0c196f2403548cdafa: [[Pasted Image 20260211082451_202.png]]

4f6ac3b63ada564e81506ed71b7ae5e7b4d28946: [[Pasted Image 20260211082451_216.png]]

5681e34c085b7cc18e2210df95ce019f1ec2ed73: [[Pasted Image 20260211082551_407.png]]

5f32f1665ef16979b05b9c496150838d19771374: [[Pasted Image 20260211084153_722.png]]

c47a13ecf54717cc6c9bc872d2eebc7872af5dc9: [[Pasted Image 20260211084351_905.png]]

5980d6c108edd970fc4d854e04231df3f096df62: [[Pasted Image 20260211085153_931.png]]

767a338bb99d01ebe0cfb32682e79de45d87ab5b: [[Pasted Image 20260211085414_573.png]]

fd4143b79371969d91c238e0555df4d7ad9debd8: [[Pasted Image 20260211095249_171.png]]

a87771e45c7d0423837f92d78fee50e7b0cd5877: [[Pasted Image 20260211095956_660.png]]

4b60dea3664e7957cf07832828ae44df9417649a: [[Pasted Image 20260211103718_788.png]]

f4656815b469ce239dba3d6731b88ea04403d0a7: [[Pasted Image 20260211105706_408.png]]

c9d54f13c7f51c9f21ed61b8084790df1a62c277: [[29f9ddd6b0656a22099cef4c2b288df31eb4efad717bfb294717939229a5b21f.png]]

901f06eda0f979f83ee8f8a5e8c3fe42d5675a87: [[01c48b0cbf45a4e3c57984f420a6ba2b101d265c1ea8998697921aaf545f94d7.png]]

352c3324ad7b7b1bebc1dcf76a228ca2435dc7f6: [[0f403c6b6d18b5ca66ee7f8f4e540f9b754d6a37bd19bb8b8e9a6fc4a89196ab.png]]

be8b22153a4a1048b94d6c9b917aabfda686071d: [[984a237eb7e7ba75e38ae61ad388d4156824962ad93a14e6f8d0bc9da15c86dc.png]]

594a03b6811fe0d35ff17dbb0a033ed17d601e70: [[7af4eae7cb018b368ebb3f83e1c0ec8a50c160016cb4beccc12edf7746d7e2a9.png]]

1c8add45c8949d1c5872a83e9a2e2fbfe6b19d82: [[0f5c0593c2204feb856d54b9063ba459d4e364cb82172a39ad4671a3ea8ba7c6.png]]

115b21a67c75ebbb7781b394b6d05d438eef7d30: [[ca5ae2b426e9aa25e23644be3fa08288eb2c7e9f503e7b6caaa8081626580c6d.png]]

ad63569ebf0c126932936630c8f3a5d87fee0809: [[Pasted Image 20260212054907_038.png]]

55b48a26532f0e69383759b4dc6ba8c9d4c81147: [[Pasted Image 20260212061429_587.png]]

ae75dba6567779984a6009060a57653f43e64b0c: [[Pasted Image 20260212163659_537.png]]

dcd57305579393e3d4785ea75077a090801eefd0: [[Pasted Image 20260212180931_801.png]]

da4c26014e95bbf66aa7018dbe0a457940eaaa48: [[Pasted Image 20260212180814_344.png]]

77de0d3513cbce68e3edbb1d9218665570f78335: [[Pasted Image 20260216100501_492.png]]

fc3777d7dc4520a631b5ef79f98ac873b2551683: [[Pasted Image 20260216100521_194.png]]

6593bbcc7e8a87eaf9ea275fa69b9fee0cf3ab13: [[Pasted Image 20260216102557_993.png]]

396eb6d22859415a427b572a8603520d88dfdb8d: [[Pasted Image 20260216112918_732.png]]

c1c40d8c519cb9929fdf92db8156f70255a9e6c9: [[Pasted Image 20260216113028_103.png]]

9cee44b95d0fff88e15e5b0d7a0a5060b55c545c: [[Pasted Image 20260216113107_661.png]]

344b51a1fc7c9c0c257e1b81b5053c9314f117ef: [[Pasted Image 20260216113136_367.png]]

%%
## Drawing
```compressed-json
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

LSxxS+wGgEQ4DMqF1QwwKecALgFkBAAA
```
%%