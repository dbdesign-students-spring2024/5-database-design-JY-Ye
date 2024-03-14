# Data Normalization and Entity-Relationship Diagramming

## Original Table 

| assignment_id | student_id | due_date | professor | assignment_topic                | classroom | grade | relevant_reading    | professor_email   |
| :------------ | :--------- | :------- | :-------- | :------------------------------ | :-------- | :---- | :------------------ | :---------------- |
| 1             | 1          | 23.02.21 | Melvin    | Data normalization              | WWH 101   | 80    | Deumlich Chapter 3  | l.melvin@foo.edu  |
| 2             | 7          | 18.11.21 | Logston   | Single table queries            | 60FA 314  | 25    | Dümmlers Chapter 11 | e.logston@foo.edu |
| 1             | 4          | 23.02.21 | Melvin    | Data normalization              | WWH 101   | 75    | Deumlich Chapter 3  | l.melvin@foo.edu  |
| 5             | 2          | 05.05.21 | Logston   | Python and pandas               | 60FA 314  | 92    | Dümmlers Chapter 14 | e.logston@foo.edu |
| 4             | 2          | 04.07.21 | Nevarez   | Spreadsheet aggregate functions | WWH 201   | 65    | Zehnder Page 87     | i.nevarez@foo.edu |
| ...           | ...        | ...      | ...       | ...                             | ...       | ...   | ...                 | ...      


## Not Satisfied 4NF
The original table has multi-valued dependencies because it mixes together details about assignments, professors, classrooms, and grades in one place. This mix-up can cause duplicate information and problems with keeping the data accurate and organized.
The table also doesn't separate different kinds of information well. For example, details about professors, where classes happen, and students' grades are all jumbled together. These details should be kept in separate spaces to make managing and understanding them easier.

### New Tables
| professor_id | professor_name | professor_email |
|--------------|----------------|-----------------|
| 1            | Melvin         | l.melvin@foo.edu |
| 2            | Logston        | e.logston@foo.edu |
| 3            | Nevarez        | i.nevarez@foo.edu |

| classroom_id | classroom_name |
|--------------|----------------|
| 1            | WWH 101        |
| 2            | 60FA 314       |
| 3            | WWH 201        |

| assignment_id | assignment_topic                | relevant_reading    |
|---------------|---------------------------------|---------------------|
| 1             | Data normalization              | Deumlich Chapter 3  |
| 2             | Single table queries            | Dümmlers Chapter 11 |
| 3             | Python and pandas               | Dümmlers Chapter 14 |
| 4             | Spreadsheet aggregate functions | Zehnder Page 87     |

| course_id | course_name                   | professor_id | classroom_id |
|-----------|-------------------------------|--------------|--------------|
| 1         | Database Systems              | 1            | 1            |
| 2         | Introduction to Programming   | 2            | 2            |
| 3         | Advanced Excel                | 3            | 3            |

| grade_id | student_id | assignment_id | grade |
|----------|------------|---------------|-------|
| 1        | 1          | 1             | 80    |
| 2        | 7          | 2             | 25    |
| 3        | 4          | 1             | 75    |
| 4        | 2          | 3             | 92    |
| 5        | 2          | 4             | 65    |

## ER Diagram

[label](images/ERD.drawio)


## Description
To make the dataset follow 4NF rules, I split the information into separate tables. This way, I got rid of overlapping information and made sure each table only talks about one kind of thing or how different things are connected.