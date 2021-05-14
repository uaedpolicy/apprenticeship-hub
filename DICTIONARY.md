# Data Dictionary
The *Alabama Apprenticeship Database (AAD)* is a standardized database structure developed for the storage and dissemination of local, state, regional, and national workforce information on the economy, industry, labor supply and demand, and other aspects of and areas affected by, or that have an effect on our workforce (especially those which relate to apprenticeship).

## Data Tables
Data for the AAD is collected from a variety of sources. Each source and corresponding elements are described below.

*Note:* Tables come in four types: 

1. Lookup Tables – these define the codes used to describe data types in data tables
2. Data Tables – these contain the data for various sources
3. Crosswalk Tables – these relate different data structures
4. Admin Tables – these describe the tables in the database

Core (required) tables have complete content, but non-standard (not required) tables may not.

### Core Tables
#### areatype
A table containing identifiers for the geographic type, e.g.. MSA, SDA, county, city, township, etc.
#### availableocc
Field Name | Description
-------|-------
 ONET Code | The onet code is an assigned set of numbers from the Occupational Information Network's (O*NET) online database. 
 ONET Title | The name of the occupation associated with the O*NET Code.  
 RAPIDS Code | The rapids code is an assigned set of numbers/letters code from the Registered Apprenticeship Partners Information Data System (RAPIDS).
 RAPIDS Title  | The title of the occupation that is associated with a RAPIDS code. 
 Term Length | The length of an apprenticeship program in hours. Competency-based apprentice-ships do not have specific hours for the on-the-job learning term but must last at least 1 year per 29 CFR 29.4. 
 Bulletin(s) | The Bulletin(s) (i.e. regulatory specifications) associated with an apprenticeship program as identified by the Department of Labor. A complete list of all bulletins can be found here. 
#### geocode 
A table of the levels of precision possible for the geocode.
#### geog
A table containing geographic area descriptor records.
#### license
Table of individual licenses authorized by a state.
#### occproj
Table of occupational employment projections by geographies. *Note: stfips : char(2); primary key 1, 2, 3.*
#### programs
Table that contains information about occupational training. 
#### schools
Table of training providers in the state.
#### subgeog
A table of substate geographic areas and the larger areas that contain the areas.

### Classification Tables
#### careercluster
A table containing a list of the Department of Education Career Clusters.
#### careerpathways
A table of the Department of Education Career Pathways.
#### cipcode
A table of the current Classification of Instructional Programs (CIP) codes, including 2, 4 and 6-digit codes.
 Field Name | Description | Type | Constraint 
------------|------------|-------|------------
cipcode | A 10-digit code assigned to a Classification of Instructional Programs (CIP) program title. | char(10) | Primary Key 
cipcodetype | A code describing the CIP version classification code. | char(2) | Primary Key 1 
ciptitle | The instructional program title used to organize training related data, i.e., enrollments, completers, placement. | varchar(200) |  
cipdesc | A definition of the curriculum included in an instructional program. | varchar(MAX) |  
ciptitls | A short version of the CIP title used for screen display. | varchar(75) |  
ciplevel | Indicator of the hierarchical level of the CIP code. | char(1) |  
 *Foreign Key (cipcode.cipcodetype) references (occtypes.codetype)*
 *Use triggers on INSERT, UPDATE or DELETE of cipcode to maintain occcodes.(statelst.stfips,
cipcode.codetype, cipcode.cipcode, cipcode.ciptitle) maintains (occcodes.stfips, occcodes.codetype,
occcodes.code, occcodes.codetitle)*
#### naicscode
A table of North American Industry Classification System (NAICS) codes.
#### occtypes
The table of occupation and training code types used in the database.
#### onetcode
A table of ONET codes and their descriptions.
#### soccode
A table of the current Standard Occupational Classification (SOC) 2018 codes.

### Administrative Tables
#### indcodes
Master table of industry code type/code combinations, allowing multiple classification systems to be used. *Note: INDCODES is normally loaded by triggers. If triggers are not used, content for this table should be appended from the related lookup tables: CENIND, SICCODE and NAICCODE.*
#### occcodes
Master table of occupation or training code type/code combination, allowing multiple codes systems to be used. *Note: OCCCODES is normally loaded by triggers. If triggers are not used, content for this table should be appended from the related lookup tables: CENSCODE, CIDSCODE, CIPCODE, CLUSCODE, DOTCODE, OCCDIR, OESCODE, ONETCODE, SOCCODE and STPROGCD.*
#### statelist
This table contains the state (Alabama) for which there is data stored in the database, used by triggers of lookup tables.
#### tablelist
This table contains one record for each table in the database.
#### tablesource
Table describing the data source(s) used to populate each table in the database.
