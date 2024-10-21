
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

# Right Join

# Full Join
