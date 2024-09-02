#paterns

- **Purpose:** The Repository pattern is used to abstract the data access logic and provide a collection-like interface for accessing domain entities. It acts as a middle layer between the domain and data mapping layers, which makes the domain model more testable and decouples the business logic from the persistence logic.
- **Common Use Cases:** It's often used in applications following Domain-Driven Design (DDD), where the repository provides a way to access aggregate roots and other domain entities.


### **When Repository Becomes an Anti-Pattern:**

1. **Over-Abstraction:**
    
    - If the repository pattern is used in simple CRUD applications where the data access logic is straightforward, it can add unnecessary complexity and abstraction without much benefit. This is especially true if you're using an ORM (Object-Relational Mapping) that already provides a high-level abstraction over the database.
2. **Leaky Abstraction:**
    
    - When the repository tries to do too much, such as handling complex queries or integrating business logic, it can lead to a "leaky abstraction." This makes the repository hard to maintain and defeats the purpose of separation of concerns.
3. **Anemic Domain Model:**
    
    - If the repository pattern is used in a way that reduces the richness of the domain model (e.g., by exposing data-centric operations rather than behavior-driven methods), it can lead to an anemic domain model, where the domain entities are just data containers without meaningful business logic.
4. **Redundancy with Modern ORMs:**
    
    - In some frameworks, modern ORMs (like Entity Framework in .NET or Hibernate in Java) provide repositories or unit of work patterns out of the box. Manually implementing the repository pattern on top of these can result in redundant code.

The main idea is to create file named repository that encapsulate logic how work to a specific entity

Example
```c#
//repository class
class UserRepositroy{
private readonly DbContext dbContext;
//Constructor
public UserRepositroy(DbContext dbContext){
	this.dbContext = dbContext;
}

//sample methods
public User GetUserById(Guid id){
//logic
}

public User GetAllUsersAsync(CancelationToken cancelationToken = default){
//logic
}
}
```