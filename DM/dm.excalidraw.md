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

Relational database should manage everything only using relational capabilities ^iTz56xoU

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
```
%%