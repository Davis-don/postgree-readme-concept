
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

 ## Third Normal Form
 * A relation will be in 3NF if it is in 2NF and not contain any transitive partial dependency.
 * 3NF is used to reduce the data duplication. It is also used to achieve the data integrity.
 * If there is no transitive dependency for non-prime attributes, then the relation must be in third normal form.

 ## Boyce Codd Normal Form
 * BCNF is the advance version of 3NF. It is stricter than 3NF.
* A table is in BCNF if every functional dependency X → Y, X is the super key of the table.
* For BCNF, the table should be in 3NF, and for every FD, LHS is super key.

 ## Fourth Normal Form
 * A relation will be in 4NF if it is in Boyce Codd normal form and has no multi-valued dependency.
 * For a dependency A → B, if for a single value of A, multiple values of B exists, then the relation will be a multi-valued dependency.
 