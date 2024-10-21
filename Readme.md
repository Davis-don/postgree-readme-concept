
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

<img src='./Screen shots/left join.png'>


# Right Join

# Full Join
