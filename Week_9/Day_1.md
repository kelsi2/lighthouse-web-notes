# Ruby (no lectures this week)

## Instance Variables
### Variable Review
```ruby
def with_tax(subtotal)
  tax_amount = subtotal * 0.20
  subtotal + tax_amount
end
```
* Both tax_amount and subtotal are local variables (one passed in, one defined inside the function)
  * If you try to access these outside the function they will be undefined because they are outside the scope
### Instance Variables
```ruby
class Invoice

  def initialize(subtotal)
    @subtotal = subtotal # assign subtotal to the instance variable @subtotal 
    @items = []
  end

  def with_tax
    tax_amount = @subtotal * 0.20
    @subtotal + tax_amount
  end

  def add_item(item)
    @items << item
    @subtotal += item.price
  end

end
```
* Instance variables have @ in front, local variables don't have this
  * Local variables are usually passed in
* With the above code we can now instantiate invoices using its initializer (constrcutor)
```ruby
invoice1 = Invoice.new(100)
```

## Active Record
[See full article here](https://edgeguides.rubyonrails.org/active_record_basics.html)

* Active Record (AR) is the ORM (Object Relational Mapping, aka relational database) of choice for Ruby/Rails devs
  * Developed as part of Rails with specific purpose of defining Database Models to allow web app to easily work with SQL database using Classes
  * AR Class (Model) => existing table in the database
    * Provides attributes that map to each column/field
    * Can CRUD records using that class and its instances
```ruby

×
Congrats on completing activity 'Ubuntu Package Update'!
Active Record
Reading
30 minutes
 Status
Incomplete
It's time to revisit relational databases using a full-featured, production ORM.

In this activity, you'll get introduced to the basics of Active Record (AR), the ORM of choice for Ruby/Rails devs.

Introduction
Active Record (AR) was developed as part of Rails with the specific purpose of defining Database Models to allow the web app to easily work with a SQL database using Classes.

Each AR Class aka Model corresponds to an existing table in the database and provides attributes that map to each column/field in the table. It then allows us to CRUD records in that table using that Class and its instances.

For example, the User model will automagically connect to the users table in the database. If the table has two fields name and email (along with id the Primary Key of course) then AR will allow us to get/set these on a given instance of User.

Example:

# Executes the following SELECT and returns an instance attributes for that record:
#   SELECT * FROM users WHERE email = 'bob@loblaw.com' LIMIT 1;
user = User.find_by(email: 'bob@loblaw.com')

# Reads an attribute (like an attr_reader)
user.id # => 5

# These are just like an attr_writers, performing changes in memory (no UPDATE sql)
user.name  = 'Bob'
user.email = 'bob@loblaw.org'

# Executes the following UPDATE statement:
#   UPDATE users SET name = 'Bob', email = 'bob@loblaw.org' WHERE id = 1;
# (Assuming id of record was 1)
user.save
```

* AR === M in MVC (Model View Controller)
  * Represents business data and logic (facilitates creation and use of business objectes whose data requires persistent storage to DB)
* In AR objects carry persistent data and behaviour which operates on that data

* Object Relational Mapping (ORM) connect objects to tables in RDBMS
  * Properties and relationships of objects can be stored and retrieved using SQL

* AR as ORM Framework allows us to:
  * Represent models and data
  * Represent associations between models
  * Represent inheritance hierarchies through related models
  * Validate models before they are persisted to the DB
  * Perform DB operations in object-oriented fashion

### AR Conventions
#### Naming
* Model Class: Singular, first letter of words capitalized (e.g. BookClub, LineItem)
* DB Table: Plural, underscores seperating words (e.g. book_clubs, line_items)

### Schema
* Foreign Keys: naming pattern => table_name_id (e.g. item_id, order_id)
  * AR will look for these fields when you create associations between models
* Primary Keys: default column id, automatically created when using AR Migrations
* Optional columns (these are reserved keywords, don't use them unless you need the functionality):
  * created_at: automatic current date and time of creation
  * updated_at: automatic current date and time of update (or creation)
  * lock_version: adds optimistic locking (ensures record saved will always be the most current, if an old version is updated a StaleObjectError will be thrown)
  * type: model uses Single Table Inheritance (allows columns to be sorted and retrieved by type)
  * (association_name)_type: stores type fo polymorphic associations (model can belong to multiple other models)
  * (table_name)_count: cache number of belonging objects on associations (e.g. comments_count column in Article class that has many instances of Comment will cache number of comments for each artcle)

### Creating AR Models
* subclass ApplicationRecord class to create an AR model, e.g.:
```ruby
class Product < ApplicationRecord
end
```
* This creates a Product model mapped to a products table at the DB
  * Also can map columns of each row with attributes of instances of your model
  ```sql
  CREATE TABLE products (
    id int(11) NOT NULL auto_increment,
    name varchar(255),
    PRIMARY KEY (id)
  )
  ```
  * Above schema declares table with two columns: id and name
    * Each row represents a product with both columns so you could write:
    ```ruby
    p = Product.new
    p.name = "Some book"
    puts p.name # => Some book

### Overriding Naming Conventions
* AR inherits from ActiveRecord::Base, can use ActiveRecord::Base.table_name= to specify table name that should be used, e.g.:
  ```ruby
  class Product < ApplicationRecord
    self.table_name = "my_products"
  end
  ```
  * Need to manually define class name using set_fixture_class in test definition
  ```ruby
  class ProductTest < ActiveSupport::TestCase
    set_fixture_class my_products: Product
    fixtures :my_products
    ...
  end
  ```
  * Can also override primary key column using ActiveRecord::Base.primary_key= e.g.:
  ```ruby
  class Product < ApplicationRecord
    self.primary_key = "product_id"
  end
  ```

### CRUD: Reading and Writing Data
* CRUD: Create, Read, Update, Delete
  * AR automatically creates methods to read and manipulate data stored in its tables

#### Create
* AR objects can be created from hash, block, or have attributes manually set after creation
  * New method returns new object, create returns object and saves it to the DB
  * You can also use the new method followed by <object name>.save to commit the record to the DB

#### Read
* AR provides API for accessing data in DB
```ruby
# return collection with all users
users = User.all

# return first user
user = User.first

# return first user named David
david = User.find_by(name: "David")

# find all users named David who are Code Artists and sort by created_at in reverse chronological order
users = User.where(name: "David", occupation: "Code Artist").order(created_at: :desc)
```

#### Update
* Once a record has been retrieved it can be modified and saved
```ruby
user = User.find_by(name: "David")
user.name = "Dave"
user.save

#shorthand using hash mapping 
user = User.find_by(name: "David")
user.update(name: "Dave")

# Can use update_all to update records in bulk
User.update_all "max_login_attempts = 3, must_change_password = 'true'"
```

#### Delete
* Once retrieved a record can also be destroyed
```ruby
user = User.find_by(name: "David")
user.destroy

# Can use destroy_by or destroy_all to delete mutliple records
# Find and delete all users named David
User.destroy_by(name: "David")
# Delete all users
User.destroy_all
```

### Validations
* Can validate a model before writing to the DB (attribute value not empty, is unique and not already in DB, follows specific format, etc.)
  * Save and update return false if validation fails so the DB is not affected, will give error ActiveRecord::RecordInvalid if using save! or update!
```ruby
class User < ApplicationRecord
  validates :name, presence: true
end

user = User.new
user.save # => false
user.save! # => ActiveRecord::RecordInvalid: Validation failed: Name can't be blank
```

### Callbacks
* Can attach code to certain events in model lifecycle
  * Adding behaviour by executing already existing code when creating, updating, destroying, etc.

### Migrations
* Migrations = Rails domain specific language for managing DB schema
  * Stored in files which are executed against DB that AR supports using rake
  ```ruby
  class CreatePublications < ActiveRecord::Migration[6.0]
    def change
      create_table :publications do |t|
        t.string :title
        t.text :description
        t.references :publication_type
        t.integer :publisher_id
        t.string :publisher_type
        t.boolean :single_issue

        t.timestamps
      end
      add_index :publications, :publication_type_id
    end
  end
  ```
  * To create DB run bin/rails db:migrate, to roll back bin/rails db:rollback