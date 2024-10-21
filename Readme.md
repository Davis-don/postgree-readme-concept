
<div style="height:200px;background-color:rgb(29, 28, 28);display:flex;justify-content:center;align-items:center;">
<h1>Postgree Sql Concept</h1>
</div>

# Inner Join

<p> <span style="color:red">Inner Join</span> Key words selects records that have matching values in both tables
</p>

## patient table
<img src='./Screen shots//patient table.png'>

## Medication Table

<img src='./Screen shots//medication table.png'>

``` sql
 SELECT p_id , p_name,medication_name,dosage  
 FROM patient_tbl,
 INNER JOIN medication_tbl ON patient_tbl.p_id = medication_tbl.medication_id
```

<img src='./Screen shots/inner join.png'>

# Left Join

<p> The <span style="color:red">LEFT JOIN</span> 
 keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match
</p>

``` sql
SELECT p.p_id, p.p_name, m.medication_name, m.dosage
FROM patient_tbl p
LEFT JOIN medication_tbl m ON p.p_id = m.medication_id;

```

<img src='./Screen shots/left join.png'>


# Right Join

<p> The <span style="color:red">Right Join</span> 
 keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.
</p>

``` sql
SELECT p.p_id, p.p_name, m.medication_name, m.dosage
FROM patient_tbl p
RIGHT JOIN medication_tbl m ON p.p_id = m.medication_id;
```
<img src='./Screen shots/right join.png'>

# Full Join

<p> The <span style="color:red">Full Join</span> 
  keyword returns all records when there is a match in left (table1) or right (table2) table records.
</p>


``` sql
SELECT p.p_id, p.p_name, m.medication_name, m.dosage
FROM patient_tbl p
FULL OUTER JOIN medication_tbl m ON p.p_id = m.medication_id;

```
<img src='./Screen shots/full join.png'>

# ACID PROPERTIES
Concept of ACID properties in DBMS is necessary for maintaining data consistency, integrity, and reliability while performing transactions in the database

## Atomicity (A)
  * By this we mean Either the entire transacton takes place at once or doesn't happen at all
  

## Consistency (C)
 * This means that integrity constraints must be maintained so that the database is consistent before and after the transaction. It refers to the correctness of a database.

## Isolation (I)

* Transactions occur independently without interference. Changes occurring in a particular transaction will not be visible to any other transaction until that particular change in that transaction is written to memory or has been committed.
  
## Durability (D)
* This property ensures that once the transaction has completed execution, the updates and modifications to the database are stored in and written to disk and they persist even if a system failure occurs.

# NORMALIZATION
* Normalization is the process of organizing the data in the database.

 ## First Normal Form
* A relation will be 1NF if it contains an atomic value.
* It states that an attribute of a table cannot hold multiple values. It must hold only single-valued attribute.

<table>

<thead>
<tr>
<th>EmpId</th>
<th>EmpName</th>
<th>EmpPhone</th>
<th>EmpState</th>
</tr>
</thead>

<tbody>
<tr>
<td>14</td>
<td>John</td>
<td>7272826385,<br/>9064738238</td>
<td>UP</td>
</tr>

<tr>
<td>20</td>
<td>Harry</td>
<td>8574783832</td>
<td>Bihar</td>
</tr>
<tr>

<td>12</td>
<td>Sam</td>
<td>7390372389,<br/>8589830302</td>
<td>Punjab</td>
</tr>
</tbody>
</table>

The decomposition of the EMPLOYEE table into 1NF has been shown below:


<table>

<thead>
<tr>
<th>EmpId</th>
<th>EmpName</th>
<th>EmpPhone</th>
<th>EmpState</th>
</tr>
</thead>

<tbody>
<tr>
<td>14</td>
<td>John</td>
<td>7272826385</td>
<td>UP</td>
</tr>
<tr>
<td>14</td>
<td>John</td>
<td>9064738238</td>
<td>UP</td>
</tr>

<tr>
<td>20</td>
<td>Harry</td>
<td>8574783832</td>
<td>Bihar</td>
</tr>

<tr>
<td>12</td>
<td>Sam</td>
<td>7390372389</td>
<td>Punjab</td>
</tr>
<tr>
<td>12</td>
<td>Sam</td>
<td>8589830302</td>
<td>Punjab</td>
</tr>
</tbody>
</table>


 ## Second Normal Form
* In the 2NF, relational must be in 1NF.
* In the second normal form, all non-key attributes are fully functional dependent on the primary key

Let's assume, a school can store the data of teachers and the subjects they teach. In a school, a teacher can teach more than one subject.

<table>

<thead>
<tr>
<th>Teacher_id</th>
<th>Subject</th>
<th>Teacher_age</th>
</tr>
</thead>
<tbody>
<tr>
<td>25</td>
<td>Chemistry</td>
<td>30</td>
</tr>
<tr>
<td>25</td>
<td>Biology</td>
<td>30</td>
</tr>
<tr>
<td>47</td>
<td>English</td>
<td>35</td>
</tr>
<tr>
<td>83</td>
<td>math</td>
<td>38</td>
</tr>
<tr>
<td>83</td>
<td>computer</td>
<td>38</td>
</tr>
</tbody>

</table>


To convert the given table into 2NF, we decompose it into two tables:
### TEACHER_DETAIL table:
<table>
<thead>
<tr>
<th>Teachers_id</th>
<th>Teachers_age</th>
<tr>
</thead>
<tbody>
<tr>
<td>25</td>
<td>30</td>
</tr>
<tr>
<td>47</td>
<td>35</td>
</tr>
<tr>
<td>83</td>
<td>38</td>
</tr>
</tbody>
</table>

### TEACHER_ID table:

<table>
<thead>
<tr>
<th>Teachers_id</th>
<th>Subject</th>
<tr>
</thead>
<tbody>
<tr>
<td>25</td>
<td>Chemistry</td>
</tr>
<tr>
<td>25</td>
<td>Biology</td>
</tr>
<tr>
<td>47</td>
<td>English</td>
</tr>
<tr>
<td>83</td>
<td>Mathematics</td>
</tr>
<tr>
<td>83</td>
<td>Computer</td>
</tr>
</tbody>
</table>

 ## Third Normal Form
 * A relation will be in 3NF if it is in 2NF and not contain any transitive partial dependency.
 * 3NF is used to reduce the data duplication. It is also used to achieve the data integrity.
 * If there is no transitive dependency for non-prime attributes, then the relation must be in third normal form.
  
  ### Employee table table:

<table>

<thead>
<tr>
<th>Emp_id</th>
<th>Emp_name</th>
<th>Emp_zip</th>
</tr>
</thead>
<tbody>
<tr>
<td>222</td>
<td>Harray</td>
<td>201010</td>
</tr>
<tr>
<td>333</td>
<td>Stephen</td>
<td>02228</td>
</tr>
<tr>
<td>444</td>
<td>Lan</td>
<td>60007</td>
</tr>
<tr>
<td>555</td>
<td>Katherine</td>
<td>06386</td>
</tr>
<tr>
<td>666</td>
<td>John</td>
<td>462007</td>
</tr>
</tbody>

</table>
3rd normal form

### Employee table

<table>
    <thead>
        <tr>
            <th>EMP_ID</th>
            <th>EMP_NAME</th>
            <th>EMP_ZIP</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>222</td>
            <td>Harry</td>
            <td>201010</td>
        </tr>
        <tr>
            <td>333</td>
            <td>Stephan</td>
            <td>02228</td>
        </tr>
        <tr>
            <td>444</td>
            <td>Lan</td>
            <td>60007</td>
        </tr>
        <tr>
            <td>555</td>
            <td>Katharine</td>
            <td>06389</td>
        </tr>
        <tr>
            <td>666</td>
            <td>John</td>
            <td>462007</td>
        </tr>
    </tbody>
</table>

### Employee Zip Table

<table>
    <thead>
        <tr>
            <th>EMP_ZIP</th>
            <th>EMP_STATE</th>
            <th>EMP_CITY</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>201010</td>
            <td>UP</td>
            <td>Noida</td>
        </tr>
        <tr>
            <td>02228</td>
            <td>US</td>
            <td>Boston</td>
        </tr>
        <tr>
            <td>60007</td>
            <td>US</td>
            <td>Chicago</td>
        </tr>
        <tr>
            <td>06389</td>
            <td>UK</td>
            <td>Norwich</td>
        </tr>
        <tr>
            <td>462007</td>
            <td>MP</td>
            <td>Bhopal</td>
        </tr>
    </tbody>
</table>

 ## Boyce Codd Normal Form
 * BCNF is the advance version of 3NF. It is stricter than 3NF.
* A table is in BCNF if every functional dependency X → Y, X is the super key of the table.
* For BCNF, the table should be in 3NF, and for every FD, LHS is super key.

Let's assume there is a company where employees work in more than one department.
### Employee_table
<table>
    <thead>
        <tr>
            <th>EMP_ID</th>
            <th>EMP_COUNTRY</th>
            <th>EMP_DEPT</th>
            <th>DEPT_TYPE</th>
            <th>EMP_DEPT_NO</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>264</td>
            <td>India</td>
            <td>Designing</td>
            <td>D394</td>
            <td>283</td>
        </tr>
        <tr>
            <td>264</td>
            <td>India</td>
            <td>Testing</td>
            <td>D394</td>
            <td>300</td>
        </tr>
        <tr>
            <td>364</td>
            <td>UK</td>
            <td>Stores</td>
            <td>D283</td>
            <td>232</td>
        </tr>
        <tr>
            <td>364</td>
            <td>UK</td>
            <td>Developing</td>
            <td>D283</td>
            <td>549</td>
        </tr>
    </tbody>
</table>


The table is not in BCNF because neither EMP_DEPT nor EMP_ID alone are keys.

To convert the given table into BCNF, we decompose it into three tables:

### Emp coutry Table
<table>
    <thead>
        <tr>
            <th>EMP_ID</th>
            <th>EMP_COUNTRY</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>264</td>
            <td>India</td>
        </tr>
        <tr>
            <td>264</td>
            <td>India</td>
        </tr>
    </tbody>
</table>

### Emp Dep tbl

<table>
    <thead>
        <tr>
            <th>EMP_DEPT</th>
            <th>DEPT_TYPE</th>
            <th>EMP_DEPT_NO</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Designing</td>
            <td>D394</td>
            <td>283</td>
        </tr>
        <tr>
            <td>Testing</td>
            <td>D394</td>
            <td>300</td>
        </tr>
        <tr>
            <td>Stores</td>
            <td>D283</td>
            <td>232</td>
        </tr>
        <tr>
            <td>Developing</td>
            <td>D283</td>
            <td>549</td>
        </tr>
    </tbody>
</table>

### Emp_DEPT_MAPPING_TABLE

<table>
    <thead>
        <tr>
            <th>EMP_ID</th>
            <th>EMP_DEPT</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>283</td>
            <td>D394</td>
        </tr>
        <tr>
            <td>300</td>
            <td>D394</td>
        </tr>
        <tr>
            <td>232</td>
            <td>D283</td>
        </tr>
        <tr>
            <td>549</td>
            <td>D283</td>
        </tr>
    </tbody>
</table>

 ## Fourth Normal Form
 * A relation will be in 4NF if it is in Boyce Codd normal form and has no multi-valued dependency.
 * For a dependency A → B, if for a single value of A, multiple values of B exists, then the relation will be a multi-valued dependency.
 

 <table>
    <thead>
        <tr>
            <th>STU_ID</th>
            <th>COURSE</th>
            <th>HOBBY</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>21</td>
            <td>Computer</td>
            <td>Dancing</td>
        </tr>
        <tr>
            <td>21</td>
            <td>Math</td>
            <td>Singing</td>
        </tr>
        <tr>
            <td>34</td>
            <td>Chemistry</td>
            <td>Dancing</td>
        </tr>
        <tr>
            <td>74</td>
            <td>Biology</td>
            <td>Cricket</td>
        </tr>
        <tr>
            <td>59</td>
            <td>Physics</td>
            <td>Hockey</td>
        </tr>
    </tbody>
</table>

The given STUDENT table is in 3NF, but the COURSE and HOBBY are two independent entity. Hence, there is no relationship between COURSE and HOBBY.

In the STUDENT relation, a student with STU_ID, 21 contains two courses, Computer and Math and two hobbies, Dancing and Singing. So there is a Multi-valued dependency on STU_ID, which leads to unnecessary repetition of data.


So to make the above table into 4NF, we can decompose it into two tables:

### Student Course
<table>
    <thead>
        <tr>
            <th>STU_ID</th>
            <th>COURSE</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>21</td>
            <td>Computer</td>
        </tr>
        <tr>
            <td>21</td>
            <td>Math</td>
        </tr>
        <tr>
            <td>34</td>
            <td>Chemistry</td>
        </tr>
        <tr>
            <td>74</td>
            <td>Biology</td>
        </tr>
        <tr>
            <td>59</td>
            <td>Physics</td>
        </tr>
    </tbody>
</table>

### Student Hobby

<table>
    <thead>
        <tr>
            <th>STU_ID</th>
            <th>HOBBY</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>21</td>
            <td>Dancing</td>
        </tr>
        <tr>
            <td>21</td>
            <td>Singing</td>
        </tr>
        <tr>
            <td>34</td>
            <td>Dancing</td>
        </tr>
        <tr>
            <td>74</td>
            <td>Cricket</td>
        </tr>
        <tr>
            <td>59</td>
            <td>Hockey</td>
        </tr>
    </tbody>
</table>