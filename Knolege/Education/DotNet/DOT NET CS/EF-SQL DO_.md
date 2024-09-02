#net #questions
## <span style="color:#caa641">Part 2</span>
---------------------------------------------------------
### 1. <span style="color:#fdd052">What is the transaction</span>
### 2. <span style="color:#fdd052">ACID</span>
- Atomicity (atomicity ensures that each individual transaction must be completed successfully or rolled back )
- Consistency (This property follows from the previous one. Due to the fact that a transaction does not allow intermediate results, the base remains consistent. There is such a definition of a transaction: "An ordered set of operations that move a database from one consistent state to another". That is, the database remains consistent before and after the transaction is executed.)
- Isolation (means that transactions should not affect each other )
- Durability (means that if something went in a wrong way this changes will be rolled back)
### 3. <span style="color:#fdd052"> what may happens in case you run several transactions the same time</span>
- read dirty (transaction read data that was changed or created via other transaction)
- Non-repeatable Read (occurs when during the transaction you read the same data several times  but within that range, you change the data.)
- phantom read (occurs in case other transaction removes some data during transaction time)
### 4. <span style="color:#fdd052">Isolation levels</span> 
##### read Uncommitted (loves isolation level, transaction can read data from other transaction even if they was not fixed yet)
- 1. include dirty read, Non-repeatable read and phantom read
##### read committed (default level, transaction can read data that is fixed already)
- 1.include phantom read Non-repeatable read
##### Repeatable read (transaction sees the same data every time it reads them data can not be changed via other transactions)
- 1.include phantom read 
- 2. exclude Non-repeatable and dirty read
##### Serializable (the Highest  isolation level transactions are executed one by one)
### 5. <span style="color:#fdd052">Transaction syntax</span>
```sql
BEGIN TRANSACTION; 
-- SOme operations inside the transaction

UPDATE accounts SET balance = balance - 100 WHERE account_id = 1; 
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2; 

-- Apply transaction
COMMIT; 

-- Rollback transaction
ROLLBACK;
```
----
### 6. <span style="color:#fdd052">How to run transaction in EF</span>
[How to use transactions](https://learn.microsoft.com/en-us/ef/core/saving/concurrency?tabs=data-annotations)

[How to use transactions](https://learn.microsoft.com/en-us/ef/core/saving/concurrency?tabs=data-annotations)

```C#
using var context = new BloggingContext(); 
using var transaction = context.Database.BeginTransaction(); 
//or you can specify isolation level
//DbContext.Database.BeginTransaction(IsolationLevel.Snapshot);

try { 
context.Blogs.Add(new Blog { Url = "https://devblogs.microsoft.com/dotnet/" }); context.SaveChanges();

transaction.CreateSavepoint("BeforeMoreBlogs");

context.Blogs.Add(new Blog { Url = "https://devblogs.microsoft.com/visualstudio/" }); 
context.Blogs.Add(new Blog { Url = "https://devblogs.microsoft.com/aspnet/" });

context.SaveChanges();
transaction.Commit();
} 
catch (Exception) 
{ 
// If a failure occurred, we rollback to the savepoint and can continue the transaction 

transaction.RollbackToSavepoint("BeforeMoreBlogs");

// TODO: Handle failure, possibly retry inserting blogs }
```
---
```c#
 public enum IsolationLevel
 {
   Serializable,
   RepeatableRead,
   ReadCommitted,
   ReadUncommitted,
   Snapshot,
   Chaos,
   Unspecified,
 }

```
## <span style="color:#d9c07a">QUESTIONS</span>
 1. How to start transaction
 2. tell about ACID
 3. describe isolation levels and differences between them
 4. describe Dirty read
 5. describe non-repeatable read
 6. describe phantom read
 7. How to start transaction in EF
## <span style="color:#d9c07a">Extra QUESTIONS</span>
1. what for we use AsNoTracking()
2. What for we use AsSpitQuery()
3. What for we use DefaultIfEmpy()
4. DbContext.users.DefaultIfEmpty()
   vs
   SomeArray.DefaultIfEmpty().