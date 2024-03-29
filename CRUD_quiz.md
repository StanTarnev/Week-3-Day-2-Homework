# CRUD Quiz

Use the solution to this afternoon's Property Tracker lab to answer the following questions. Please write your answers under each question, push the file to GitHub, and submit in the usual way.

## MVP Questions

In our Property Tracker application:

Q1. Where are we instantiating instances of the `Property` class?

  In the console.rb file.

Q2. Where are we defining the SQL that enables us to save the ruby `Property` object into the database?

  sql = "INSERT INTO properties(address, value, bedrooms, build) VALUES ($1,$2,$3,$4) RETURNING id"
  values = [@address, @value, @bedrooms, @build]

Q3. In `console.rb`, which lines modify the database?

  Property.delete_all()
  property1.save()
  property2.save()
  property3.save()
  property1.delete()

Q4. Why do we not define the id of a `Property` object at the point we instantiate it (‘new it up’)?

  Because the id is dynamic, not permanent for the object.

Q5. Where and how do we assign the id (that is generated by the database) to the ruby `Property` object?

  @id = db.exec_prepared("save", values)[0]["id"].to_i

Q6. Why do we put a guard (an `if` clause) on the `@id` attribute in the constructor?

  Because it is secondary to the other attributes, a result of of the creation of the object.

Q7. Why are some of the CRUD actions represented by instance methods, and others by class methods?

  Because some methods perform actions on particular instances of the class, while others affect the whole class.

Q8. What type of data structure is returned by calls to `db.exec_prepared()`?

  A hash.

In the `save` method, how do we access the id from the returned data structure?

  It is stored as an instance variable.

Q9. Why do we use prepared statements when performing database operations?

  They help against SQL injection.

## Extension Questions

Look at the `find_by_id` and `find_by_address` methods in the `Property` class.

Q10. What do they take in as their arguments?

  The parameters used to search by, i.e. id or address.

Q11. What are their return values?

  New Property objects.
