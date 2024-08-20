# Datatypes

![Screenshot 2024-08-20 152439](https://github.com/user-attachments/assets/bf50e8d6-e7f1-4016-82d1-5a976c964053)

#### Scalar Datatypes
 Can store single value in a varib;e

#### Composite Datatypes
Can store more than one value in the same  variables
  1. Record type
       stores one row of data

        - Type
        - %rowtype
      
  2. Collection
     
       - Varry
       - Nested Table
       - Associate array
 4. Reference:
    
       - REF Cursor

#### Scalar Datatype Vs Record type Example

```plsql
  declare
      v_ename varchar2(50);
      v_esal number;
  begin
       select ename,sal
       into v_ename,v_sal
       from emp
       where eno=50;
       dbms_output.put_line('EMP NAME = ' || v_ename);
       dbma_output.put_line(Emp Salary = ' || v_esal);
end;
```

Now the same above code when Record data type is used

```plsql
 declare
      v_emp_rec emp%row_type;
  begin
       select *
       into v_emp_rec
       from emp where eno=50;
     dbms_ouput.put_line('EMP Name is || v_emp_rec.ename);
     dbms_ouput.put_line('EMP Salary is || v_emp_rec.sal);
end;
```

### Collection Vs Record

it is ordered group of logically related elements and they have same data type where as in Records it can have different data types.
Internal elemenets in collection are called elemenets and in Records it is called as fields.

Eg: List of Employees, Address of employees



     
