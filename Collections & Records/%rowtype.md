# %rowtype
  a record that represents the row in a table or view. The name and datatype 
  of the referenced table/view are inherited into the variable.
  When the datatype at table level is changed then it is automatically
  changed in the variable defined.
  For Eg: if a table has 100 rows then by using %rowtype we can fetch the data
  from all those 100 columns with jus one column.
  Syntax:
  
   ```plsql 
        v_emp_rec emp%ROWTYPE
   ```
  ##### Sample Code:

  ```plsql
 DECLARE
     v_emp_rec emp%ROWTYPE;
 BEGIN
    SELECT *
    INTO v_emp_rec
    FROM emp;
   dbms_ouptput.put_line('Name  '|v_emp_rec.ename);
   dbms_ouptput.put_line('Sal  '|v_emp_rec.esal);
END;
```

##### Possible Exceptions

1. When there is no `where` clause it gives `more than expected num of records`
2. Where is no data then  we get `no data found` exception

##### Examples
1. Inserting data from one table to another table.

``` plsql
DECLARE
    v_emp_rec emp%ROWTYPE;
BEGIN
    SELECT *
    INTO v_emp_rec
    FROM emp WHERE eno=50;
INSERT INTO emp_bkp VALUES v_emp_rec;
END;
```

2. Updating Table values

```plsql
DECLARE
    v_emp_rec emp%ROWTYPE;
BEGIN
    SELECT *
    INTO v_emp_rec
    FROM emp WHERE eno=50;
   v_emp_rec.sal:=v_emp_rec.sal+1000;
   v_emp_rec.dno:=50;

    UPDATE emp
    set row=v_emp_rec
    WHERE eno=50;
 END;
```

3. Using with Cursor

```plsql
DECLARE
    cursor c1 select ename,sal,deptno from emp where eno=50;
    lv_emp_rec emp%ROWTYPE;
BEGIN
    open c1;
    fetch c1 into lv_emp_rec;
    close c1;
    dbms_output.put_line('Name '|lv_emp_rec.ename);
    dbms_output.put_line('Sal '|lv_emp_rec.sal);
END;
```






