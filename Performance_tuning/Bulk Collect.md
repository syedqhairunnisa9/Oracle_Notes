# Bulk Collect
   There are 2 engines  one is PLSQL Engine and other is SQL Engine. All the procedural statements like IF clause are sent to PLSQL Engine and 
   other SQL statements like select are sent to SQL Engine for their excution .
   Once the excution is done at SQL Engine it is sent back to PLSQL Engine.
   This assigning to PLSQL variables from SQL statments is called Binding. 
## Context Switching
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
  
