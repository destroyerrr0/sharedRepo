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
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=
```
%%