# Bulk Collect
   There are 2 engines  one is PLSQL Engine and other is SQL Engine. All the procedural statements like IF clause are sent to PLSQL Engine and 
   other SQL statements like select are sent to SQL Engine for their excution .
   Once the excution is done at SQL Engine it is sent back to PLSQL Engine.
   This assigning to PLSQL variables from SQL statments is called Binding. 
## Context Switching
  this Switching between the engines is called Context Switching and it consumes lot of performance. 
  For Eg: if there a loop like 
