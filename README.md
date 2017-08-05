# Introduction to Databases

This repo is designed as a guide for Founders and Coders mentors so they can give an introduction to databases to beginner developers who are not familiar with the concept.
this README is accompanied with slides to help explain the materials. (These slides are based on @stevehopkinson 's slides and talk on databases).

## What's a database, why use it in an application and when is it useful?

*slides 1-5*

### When and why to use a database?

- Apps that we use in real life, save data, for example if an app has users then it'll save their login details.
- This data has to be saved somewhere, a "data center" where we save new data, fetch it or edit it.
- This "data center" is called a database.
- You can simplify this concept by saying that a database is a chunk of memory dedicated for the app's data.

### In which applications is it useful to have a database?

- Ask the students this question to see if they have understood.
- Then ask which applications would not need a database.

### Example of a database

- The example would be about users and posts (a small facebook).
- You can start by explaining that the app has users where each user has a username and a password, whereas each post has a user reference and a post id.
- Before writing this on the board, ask the students how they expect each data would be represented, as in which data does a user have and what does a post have, don't mention the concept of tables yet.


## How to structure a database and how to separate it into tables?

*slide 6*
- After explaining what data you need, you can start talking about tables.
- A table is a specific type of data, ask the students how would they separate the
types of data in the example.
- If the answer was that you should put the posts in the users table, explain that you shouldn't repeat the same information more than once and it would indicate the need for a new table, otherwise ask them to explain why they wouldn't put the posts next to a user's details.
- Draw the tables on the board, explain what each column means and that each row is a data entry for a specific user/post.
- Explain the need of an id: every table has a unique and not null (not empty) column which is the id of that entry, useful for referencing a specific row, when you have multiple tables.
- The tables that you would use would look like this:

Users table:

|user_id|username|password|
|-------|--------|--------|

Posts table:

|post_id|text|user_id|
|-------|----|-------|


## A taste of Schemas and Relationships

*slides 7-8*

- Explain that a schema is the way we divide the database into tables, this doesn't have to be detailed since there is a research topic on schemas.
- so in the example the schema is the users table and the posts table.

*slide 9*

- Give another example of a database and ask the students to build the schema: a pets database, the database will have the pet owners with their name, address and phone number and their pets with the name and what type of animal is it.
- Do these examples
  - one pet per person, simple and intuitive, same as the example before.

Owners table:

  |id|name|address|phone number|
  |--|----|-------|------------|

  Pets table:

  |id|name|type|owner_id|
  |--|----|----|--------|

  - multiple pets per person, same table as before.

  - one pet can be owned by more than one person

Owners table:

|id|name|address|phone number|pet_id|
|--|----|-------|------------|------|

  Pets table:

  |id|name|type|
  |--|----|----|

  - multiple owners can have multiple pets (shared custody), this would require a new table for connecting the first two.

Owners table:

  |id|name|address|phone number|
  |--|----|-------|------------|

  Pets table:

  |id|name|type|
  |--|----|----|

  Ownership table:

  |id|owner_id|pet_id|
  |--|--------|------|


## Basic commands for selecting and inserting.

- Assuming you have a database ready with some data in it, how would you get the data from the database, explain the structure of a select query:

  Select [columns (separated by a comma)] From [table];

  and if it's too easy, add the where constraint
  SELECT [column1, column2, column3, ...] FROM [table_name] WHERE [condition];

  *note* the semicolon at the end of the query indicates where it ends, forgetting the semicolon would give you no error.

- Explain the structure of an insert:
INSERT INTO [table_name] [column1, column2, column3, ...]
VALUES [value1, value2, value3, ...];

- explain how both queries with an example.
