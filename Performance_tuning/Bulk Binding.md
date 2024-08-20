# Bulk Binding
## Defination
   There are 2 engines  one is PLSQL Engine and other is SQL Engine. All the procedural statements like IF clause are sent to PLSQL Engine and 
   other SQL statements like select are sent to SQL Engine for their excution .
   Once the excution is done at SQL Engine it is sent back to PLSQL Engine.
   This assigning to PLSQL variables from SQL statments is called Binding. 
### Context Switching
  this Switching between the engines is called Context Switching and it consumes lot of performance. 
  For Eg: if there a loop like 

  ```plsql
  DECLARE name varchar(200);
  BEGIN
      FOR i in 1..1000 LOOP
      SELECT  ename INTO name
      FROM emp
      WHERE empno=20
  END LOOP;
  END;
```
In the above code for every iteration of i which is 1000 times code is being switched between the engines which decreases the performance

So now 1000 times variables are binded to PLSQL.
So instead of switching one by one , the binding is done for all the variable at once or in less number of switching, This is called `Bulk Binding/Bulk Collect`

## Types of Binding

##### In-Bind
 Values from PLSQL engine is assigned to SQl Engine
 Eg: INSERT, UPDATE,MERGE
 ###### FOR ALL
 In-Bind can be achieved using FOR ALL statement. Using the it converts collection into a table format

 ```plsql
FOR ALL I in lv_num_list.first .. lv_num_list.last
          INSERT INTO A values (lv_num_list(I));
```

##### Out-Bind
Values from SQLengine returned back to PLSQL Engine
Eg: RETURNING INTO

```plsql
  UPDATE emp SET sal=sal+100
  RETURNING sal INTO lv_num_list;
```



##### Define
when SELECT OR FETCH statement from SQL assigns/holds the value to PLSQL

```plsql
DECLARE
  type t_num_list_type is table of number
  lv_num_list t_num_list_type :=t_num_list_type();
BEGIN    
   SELECT sal
   BULK_COLLECT INTO lv_num_list
   FROM emp



` A query that used bulk SQL can return any number of rows without using a FETCH statement for each row`




