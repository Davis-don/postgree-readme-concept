
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

# NORMALIZATION

 ## First Normal Form
 ## Second Normal Form
 ## Third Normal Form
 ## Boyce Codd Normal Form
 ## Fourth Normal Form
 