# TYPE
To define RECORD we need a name and the list of fields.

```plsql
DECLARE
    TYPE emp_rec_type IS RECORD( empnama VARCHAR2(100),sal NUMBER);
    emp_rec emp_rec_type;
BEGIN
```

#### Assigning Values to Record
1. by directly assiging them to variables

```plsql
DECLARE
    TYPE emp_rec_type IS RECORD( empnama VARCHAR2(100),sal NUMBER);
    emp_rec emp_rec_type;
BEGIN
    emp_rec.empname:='RAJ';
    emp_rec.sal:=1000;

    dbms_output.put_line('Name '|| emp_rec.ename);
    dbms_output.put_line('Salary ' || emp_rec.sal);
END;
```
