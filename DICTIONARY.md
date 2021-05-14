# Data Dictionary
Data for the Alabama Apprenticeship Database is collected from a variety of sources. Each source and corresponding elements are described below.

## Tables

### Core Tables

#### Available Occupations (USDOL)
Field Name | Description
-------|-------
 ONET Code | The onet code is an assigned set of numbers from the Occupational Information Network's (O*NET) online database. 
 ONET Title | The name of the occupation associated with the O*NET Code.  
 RAPIDS Code | The rapids code is an assigned set of numbers/letters code from the Registered Apprenticeship Partners Information Data System (RAPIDS).
 RAPIDS Title  | The title of the occupation that is associated with a RAPIDS code. 
 Term Length | The length of an apprenticeship program in hours. Competency-based apprentice-ships do not have specific hours for the on-the-job learning term but must last at least 1 year per 29 CFR 29.4. 
 Bulletin(s) | The Bulletin(s) (i.e. regulatory specifications) associated with an apprenticeship program as identified by the Department of Labor. A complete list of all bulletins can be found here. 

#### cipcode
 Field Name | Description | Type | Constraint 
------------|------------|-------|------------
cipcode | A 10-digit code assigned to a Classification of Instructional Programs (CIP) program title. | char(10) | Primary Key 
cipcodetype | A code describing the CIP version classification code. | char(2) | Primary Key 1 
ciptitle | The instructional program title used to organize training related data, i.e., enrollments, completers, placement. | varchar(200) |  
cipdesc | A definition of the curriculum included in an instructional program. | varchar(MAX) |  
ciptitls | A short version of the CIP title used for screen display. | varchar(75) |  
ciplevel | Indicator of the hierarchical level of the CIP code. | char(1) |  
