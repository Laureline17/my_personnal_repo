# Documentation

The work for week 5 consists to explain 6 rules of clean code and give some example. 


## First rule

To make sure your code is understandable, you hate to comment it. 
You have to use recognised commenting conventions. They have to be clear and place at the good place.
For example, before a function or next to a complicate part of the code or next to names to describe what they are used for.

```
    // Class for managing the SQLite database for SystemType
    public class SystemTypeDatabase
    {
```

In my code you can see that before coding my class I put a comment to describe why I made it and what it will do. 
My comment is place correctly because it just before what it comments, so people reading my code understand what I am talking about. 
And also my comment is clear, descriptive and not to long. 

## Second rule

Another important rule is to use appropriate names for variables, functions and class. 
It's usefull when you have to read again your code or when someone else have to read it because they have to know what's the variables is made for.
You have to describe what are their functions and use camelCase. 

```
    public class SystemTypeDatabase
    {
````

My class is named "SystemTypeDatabase" so it use appropriate name. In fact it is written in camelCase so it is readable. 
Just with the name you can understand what will the class will be used for. 

## Third rule

To have a clean code you have to make it simple and use the "KISS" rule. KISS stand for "Keep It Simple, Stupid". 
In order to follow this rule you have to avoid complexity that often lead to confusion, bugs, and maintenance difficulties.
The use of the word "stupid" is a reminder that code should not try to be overly clever or complex.

```
// Save a SystemType record to the database (either insert or update)
public async Task<int> SaveSystemTypeAsync(SystemType systemType)
{
    if (systemType.Id != 0)
    {
        // Update an existing SystemType record in the database
        return await _database.UpdateAsync(systemType);
    }
    else
    {
        // Insert a new SystemType record into the database
        return await _database.InsertAsync(systemType);
    }
}
```

In this part of my code, we can observe that I respected the KISS principe. 
In fact, this part directly performs two operations instead of having two separate methods to insert and update records.
So the code is more simple and more readable.

## Fourth rule 

In the continuity of the third rule, you have to not repeat yourself to simplify your code. This rule is named "DRY", "Don't Repeat Yourself". 
The DRY principle is all about minimizing redundancy in your codebase and promoting a more efficient and maintainable software development process.

```
// Save a SystemType record to the database (either insert or update)
public async Task<int> SaveSystemTypeAsync(SystemType systemType)
{
    if (systemType.Id != 0)
    {
        // Update an existing SystemType record in the database
        return await _database.UpdateAsync(systemType);
    }
    else
    {
        // Insert a new SystemType record into the database
        return await _database.InsertAsync(systemType);
    }
}
```
I choose to take the same example for this rule because thanks to this part of code I don't repeat my self. 
Instead of doing two part with the same operations, I have gathered this two part in one. 
Like that my code is shorter. 

## Fifth rule

The fifth rule has also for aim to reduce codes. It's "YAGNI" rule witch stand for "You Aint Gonna Need It".
It's a principle that advises developers to avoid adding features or functionality to their codebase until those features are actually needed.
Like that you have a more simple and understable code and also you don't waste your time.

```
// Save a SystemType record to the database (either insert or update)
public async Task<int> SaveSystemTypeAsync(SystemType systemType)
{
    if (systemType.Id != 0)
    {
        // Update an existing SystemType record in the database
        return await _database.UpdateAsync(systemType);
    }
    else
    {
        // Insert a new SystemType record into the database
        return await _database.InsertAsync(systemType);
    }
}
```
I am using again the same example because it show that every part of my code is used. 
This part is making differents operations so whenever there are an operation needed, this is this part of the code that is being used.
So this part is always necessary. 

## Sixth rule 

The last rule that I would like to talk about consists in clear and consistent layout and formatting. 
This rule is really important for readability. 
For example you have to make sure that you respect identation, the spacing between elements and other principle.
Sometimes your code works even if you don't respect that rule but if you want to have a clean and understable code you have to respect it. 

```
 // Delete a SystemType record from the database
 public async Task<int> DeleteSystemTypeAsync(SystemType systemType)
 {
    return await _database.DeleteAsync(systemType);
 }
```
Like you can see on this part of code, I respect identation and the spacing between elements.
After a parenthese you have to pay attention to the identation


# Doxygen comments

```
using System;
using System.Collections.Generic;
using System.Linq;
using SQLite;
using Microsoft.Maui.Controls;

namespace UNDAC_App
{
    /// <summary>
    /// Class for managing the SQLite database for system types.
    /// </summary>
    public class SystemTypeDatabase
    {
        readonly SQLiteAsyncConnection _database;

        /// <summary>
        /// Initializes a new instance of the SystemTypeDatabase class.
        /// </summary>
        /// <param name="dbPath">The path to the SQLite database.</param>
        public SystemTypeDatabase(string dbPath)
        {
            _database = new SQLiteAsyncConnection(dbPath);

            // Create the SystemType table if it doesn't already exist.
            _database.CreateTableAsync<SystemType>().Wait();
        }

        /// <summary>
        /// Retrieves a list of all SystemType records from the database.
        /// </summary>
        /// <returns>A list of SystemType records.</returns>
        public async Task<List<SystemType>> GetSystemTypesAsync()
        {
            return await _database.Table<SystemType>().ToListAsync();
        }

        /// <summary>
        /// Saves a SystemType record in the database (insertion or update).
        /// </summary>
        /// <param name="systemType">The SystemType record to save.</param>
        /// <returns>The number of affected records (1 for success, 0 for failure).</returns>
        public async Task<int> SaveSystemTypeAsync(SystemType systemType)
        {
            if (systemType.Id != 0)
            {
                // Update an existing SystemType record in the database.
                return await _database.UpdateAsync(systemType);
            }
            else
            {
                // Insert a new SystemType record into the database.
                return await _database.InsertAsync(systemType);
            }
        }

        /// <summary>
        /// Deletes a SystemType record from the database.
        /// </summary>
        /// <param name="systemType">The SystemType record to delete.</param>
        /// <returns>The number of affected records (1 for success, 0 for failure).</returns>
        public async Task<int> DeleteSystemTypeAsync(SystemType systemType)
        {
            return await _database.DeleteAsync(systemType);
        }
    }
}

```
"Class for managing the SQLite database for system types" is the actual summary or description of the class. 
It explains that this class is used to manage an SQLite database for system types.

```
 /// <summary>
 /// Initializes a new instance of the SystemTypeDatabase class.
 /// </summary>
 /// <param name="dbPath">The path to the SQLite database.</param>
```
This is the constructor for the SystemTypeDatabase class.
"Initializes a new instance of the SystemTypeDatabase class" is the actual description, stating that the constructor initializes a new instance of the SystemTypeDatabase class.
"<param name="dbPath">" : This tag is used to describe the parameters of the constructor.
"The path to the SQLite database" is the description of the dbPath parameter, explaining that it represents the path to the SQLite database.


```
   /// <summary>
   /// Retrieves a list of all SystemType records from the database.
   /// </summary>
```
"Retrieves a list of all SystemType records from the database" is the actual description of what the method does.
Which is to retrieve a list of all SystemType records from the database.

```
   /// <returns>A list of SystemType records.</returns>
```
"<returns>" This tag describes what the method returns.
"A list of SystemType records" is the description of the return value, stating that it's a list of SystemType records.

