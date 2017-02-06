# Apartment Database

- Create a database called `apartments`

<!-- CREATE DATABASE apartments; -->
<!-- melvinmok=# \connect apartments -->

- Using this database, create two tables, one for owners and one for properties

<!-- CREATE TABLE owners (id SERIAL PRIMARY KEY, name TEXT, age INTEGER); -->
<!-- CREATE TABLE properties (id SERIAL PRIMARY KEY, name TEXT, units INTEGER, owner_id INTEGER REFERENCES owners); -->

- Keep this relationship in mind when designing your schema:
  + **One owner can have many properties**

###Part 1: Create Tables

- The owners table should consist of:
  + `id` (this should be the primary key as well as a unique number that increments automatically)
  + `name` - name of owner
  + `age` - age of owner
- The properties table should consist of:
  + `id` (this should be the primary key as well as a unique number that increments automatically)
  + `name` - name of property
  + `units` - number of units
  + `owner_id` - reference to owner table
    + Remember to create a foreign key constraint that references the owners table

###Part 2: Insert Data

* Insert the following owners
    * Donald - age 29
    * John - age 33
    * Jane - age 43
    * Add 3 more people (you choose name / age)

<!-- INSERT INTO owners (name, age) VALUES ('Donald', 29); -->
<!-- INSERT INTO owners (name, age) VALUES ('John', 33); -->
<!-- INSERT INTO owners (name, age) VALUES ('Jane', 43); -->
<!-- INSERT INTO owners (name, age) VALUES ('Tom', 24); -->
<!-- INSERT INTO owners (name, age) VALUES ('Dick', 24); -->
<!-- INSERT INTO owners (name, age) VALUES ('Harry', 24); -->

* Insert the following properties (you can pick and choose the property owners)
    * Archstone - 20 units
    * Willowspring - 30 units
    * Add 3 more properties (you choose name / units)

<!-- INSERT INTO properties (name, units, owner_id) VALUES ('Archstone', 20, 1); -->
<!-- INSERT INTO properties (name, units, owner_id) VALUES ('Willowspring', 30, 2); -->
<!-- INSERT INTO properties (name, units, owner_id) VALUES ('Oaksummer', 40, 3); -->
<!-- INSERT INTO properties (name, units, owner_id) VALUES ('Birchfall', 50, 4); -->
<!-- INSERT INTO properties (name, units, owner_id) VALUES ('Maplespring', 60, 5); -->

###Part 3: Use Your Database

Write down the following sql statements that are required to solve the following tasks.

1. Show all the data in the owners table.

<!-- SELECT * FROM owners -->

* Show the names of all owners.

<!-- SELECT name FROM owners -->

* Show the ages of all of the owners in ascending order.

<!-- SELECT * FROM owners ORDER BY age ASC; -->

* Show the name of an owner whose name is Donald.

<!-- SELECT name FROM owners WHERE name = 'Donald'; -->

* Show the age of all owners who are older than 30.

<!-- SELECT age FROM owners WHERE age > 30; -->

* Show the name of all owners whose name starts with an E.

<!-- SELECT name FROM owners WHERE name LIKE 'E%'; -->

* Change Jane's age to 30.

<!-- UPDATE owners SET age = 30 WHERE name = 'Jane'; -->

* Change Jane's name to Janet.

<!-- UPDATE owners SET name = 'Janet' WHERE name = 'Jane'; -->

* Delete the owner named Janet.

<!-- DELETE FROM owners WHERE name = 'Janet'; -->
<!-- ERROR:  update or delete on table "owners" violates foreign key constraint "properties_owner_id_fkey" on table "properties"
DETAIL:  Key (id)=(3) is still referenced from table "properties". -->

* Show the names of the first three owners in your owners table.

<!-- SELECT name FROM owners ORDER BY id ASC LIMIT 3; -->


###Bonuses

These might require you to look up documentation online, or look at the next section in the notes.

1. In the properties table change the name of the column "name" to "property_name".

<!-- ALTER TABLE properties RENAME COLUMN name to property_name; -->

* Count the total number of properties where the owner_id is between 1 and 3.

<!-- SELECT COUNT(*) FROM properties WHERE 1 < id AND id < 3; -->

* Show all of the properties in alphabetical order that are not named Archstone and do not have an id of 3 or 5.

<!-- SELECT * FROM properties WHERE id != 3 AND id !=5 AND property_name != 'Archstone' ORDER BY property_name ASC; -->

* Show the highest age of all owners.

<!-- SELECT max(age) FROM owners; -->

* List all properties sorted by the owners names

<!-- SELECT * FROM properties JOIN owners ON properties.owner_id = owners.id ORDER BY owners.name ASC; -->



---

## Licensing
1. All content is licensed under a CC-BY-NC-SA 4.0 license.
2. All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
