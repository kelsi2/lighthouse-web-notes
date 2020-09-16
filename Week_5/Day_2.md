# Database Design

## Topics
### Intro to Creating ERDs
### Data Modeling using ERDs
### Architecting Data Principles
### Many-to-many Relationships
### Normalized database design (why and how)

[Notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w05d02)
[Lecture here](https://us02web.zoom.us/rec/play/GMW2A75W-ziKw8_TTZZuxZcOzYA_sSv2GUw5CuI29PCAzRugoSsuZm2QjF3WIET5VRUHgvH8_zFZU7Yy.66WbPp1fqf4qToUY?startTime=1600187140000&_x_zm_rtaid=xB1yUh41T26Em9HYCgXslA.1600216389989.cd2cb1abe08af3c42948f25172081297&_x_zm_rhtaid=576)

### Primary Key/Foreign Key
* PK: Uniquely identify a record
* Can be any data type or a combination of fields
  * Use autoincrementing primary key (serial) to avoid complications
    * Users change their user name so it's best not to make that a PK, best to use an integer that has nothing to do with the record itself. It will never change
* FK - Have to be same data type as PK

### Naming Conventions
* Table names and field names are lowercase / snake_case
* Table names are always plural (a collection of individual entities like arrays)
* PK === id
* FK === singular of parent table name _id (ex. users === user_id)

### Data Types
* Each field must have a data type declared
* On record creation the db sets aside room in memory for every field, even if they are null (ex. no picture uploaded, there is still space for this)
* Used to be a big concern because we needed to tell the database how much room to save (data was very expensive so there were arguments about how much to store, now data is cheap so it doesn't matter as much)
  * Now we use varchar for everything (normally 255 max characters for strings), int, bigint, boolean, JSON
  * postal_codes, phone_numbers => varchar/char/string
    * leading zeroes lead to truncation in numbers so best to store them as strings

### Relationships
* One-to-one: one record in the first table is related to only one record in the second table
  * Pretty much useless to create this relationship, fields should just be moved into the original table
  * The only time this might be useful is if you're trying to save space in your database (such as usernames and passwords)
* One-to-many: One record in the first table is related to one or more records in the second
  * Most common relationship type, when in doubt use this
  * Difficulty is the direction
* Many-to-many: One or more records in the first table are related to one or more records in the second table
  * Need a third table to represent this (join/junction table that sits in between the other two tables)
  * Each of the tables will be in a one-to-many relationship with the bridging table 
**One-to-Many is really the ONLY relationship type we need to be concerned about!!**

### Design Concepts
* Required - What the initial state of the record is (what do we actually need when the record is first created?)
* Default values - Use intelligent defaults where you can (timestamp => NOW() so we don't need the user to specify this)
* Don't use calculated fields - value can be derived from one or more other fields (full name === first_name + ' ' + last_name) 
  * Danger of storing this when users change their information. We would need to run a script to change the calculated fields so it's better to just not store it this way
  * Should have a single source of truth because we might end up with different answers and can't tell which is right
* Try not to delete anything, it's important to have a record
  * 'active' boolean => default to true so you can do a soft delete (set boolean to false)
