#paterns
I is a pattern that is used mostly to make application more clean
the main idea is to divide all operations to commands and queries

**Command** Change System state and not return any data
**Query** do not change system state and used to return some data

but by default it is quite difficult to separate all your operations this way just because sometimes when you create an entity you want to return an Id and etc.

As a result it is acceptable to mark as **command** al operations where you CREATE | UPDATE | DELETA some data  And as a **query** Operations where you just Select some data 

NAMING examples
``` c#
//Comand
public class CreateNewUserCommand
//Query
public class GetAllUsersQuery
```