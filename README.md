# Sqlite middleware
This package removes all the annoying boilerplate code you have to write when using `sqlite3`. Instead, use the methods this package provides, and easily manage your sqlite database in your python project.

# Db class:
All the functionality of this package is in the `Db` class.
When creating a new instance of this class, you should specify following parameters:
- **database**: (str) name of the sqlite file

Example usage:
```python
db = Db("demo.db")
```

When an instance of `Db` is deleted, the `__del__` magic method will close the connection.

## Methods
Here are all the methods that the `Db` class provides:
- [select_all](#select-all)
- [select_by_id](#select-by-id)
- [create_table](#create-table)
- [save_object](#save-object)
- [update_object](#update-object)
- [delete_object](#delete-object)

## Select all
This method will retrieve and return all objects of a certain class from the sqlite database.

Parameters:
- **cls**: (Class) class of the objects you want to retrieve

Example usage:
```python
db.select_all(Person)
```

## Select by id
This method will retrieve and return an object with certain id and class from the database.

Parameters:
- **cls**: (Class) class of the object you want to retrieve
- **id**: (int) id of the object you want to retrieve

Example usage:
```python
db.select_by_id(Person, 2)
```

## Create table
This method will create a table in the database for objects of a certain class.

Parameters:
- **object**: (Instance) instance of the class you want to create a new table for.

Example usage:
```python
db.create_table(Person())
```

## Save object
This method will save an object in the database.

It will also create a table if it doesn't exist yet.

Parameters:
- **object**: (Instance) object you want to save in the database.

Example usage:
```python
person = Person("John Doe")
db.save_object(person)
```

## Update object
This method will update an existing object in the database.

Parameters:
- **id**: (int) id of the object you want to update.
- **object**: (Instance) object containing new values you want to save in the database.

Example usage:
```python
person = Person("John Doe")
db.save_object(person) # Say this is the first person, and gets id 1

person.set_name("Michael Myers")
db.update_object(1, person)
```

## Delete object
This method will delete an object from the database.

Parameters:
- **cls**: (Class) class of the object you want to delete.
- **id**: (int) id of the object you want to delete

Example usage:
```python
person = Person("John Doe")
db.save_object(person) # Say this is the first person, and gets id 1

db.delete_object(Person, 1)
```