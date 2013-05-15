# ActiveRecord
---

## Types of Associations

``` ruby
belongs_to
has_one
has_many
has_many :through
has_one :through
has_and_belongs_to_many
```

## Methods for migrations

``` ruby
add_column
add_index
change_column
change_table
create_table
drop_table
remove_column
remove_index
rename_column
```

## Supported Types

``` ruby
:binary
:boolean
:date
:datetime
:decimal
:float
:integer
:primary_key
:string
:text
:time
:timestamp
```

## Methods for retrieving objects from the database

``` ruby
where
select
group
order
reorder
reverse_order
limit
offset
joins
includes
lock
readonly
from
having
```

## Methods & Validations

### These methods trigger validations, & will save the object to the database **only if the object is valid**

``` ruby
create
create!
save
save!
update
update_attributes
update_attributes!
```

### These methods skip validations, & will save the object to the database **regardless** of its validity.

``` ruby
decrement!
decrement_counter
increment!
increment_counter
toggle!
touch
update_all
update_attribute
update_column
update_counters
```

## Migrations

### Transformations

#### Available Transformations

- **create_table**(name, options)
    - Creates a table called name and makes the table object available to a block that can then add columns to it, following the same format as add_column. See example above. The options hash is for fragments like "DEFAULT CHARSET=UTF-8" that are appended to the create table definition.
- **drop_table**(name)
    - Drops the table called name.
- **rename_table**(old_name, new_name)
    - Renames the table called old_name to new_name.
- **add_column**(table_name, column_name, type, options)
    - Adds a new column to the table called table_name named column_name specified to be one of the following types
    - :string, :text, :integer, :float, :decimal, :datetime, :timestamp, :time, :date, :binary, :boolean. A default value can be specified by passing an options hash like { :default => 11 }. Other options include :limit and :null (e.g. { :limit => 50, :null => false }) -- see ActiveRecord::ConnectionAdapters::TableDefinition#column for details.
- **rename_column**(table_name, column_name, new_column_name)
    - Renames a column but keeps the type and content.
- **change_column**(table_name, column_name, type, options)
    - Changes the column to a different type using the same parameters as add_column.
- **remove_column**(table_name, column_names)
    - Removes the column listed in column_names from the table called table_name.
- **add_index**(table_name, column_names, options)
    - Adds a new index with the name of the column. Other options include :name, :unique (e.g. { :name => "users_name_index", :unique => true }) and :order (e.g. { :order => {:name => :desc} }</tt>).
- **remove_index**(table_name, :column => column_name)
    - Removes the index specified by column_name.
- **remove_index**(table_name, :name => index_name)
    - Removes the index specified by index_name.- **

#### Creation

``` ruby
class CreateUsers < ActiveRecord::Migration
  def change
    create_table :users do |t|
      t.string :name
      t.string :email
      t.string :password

      t.timestamps
    end
  end
end
```

#### Addition

``` ruby
class AddUserNameToUsers < ActiveRecord::Migration
  def change
    add_column :users, :user_name, :string
    add_column :location, :tweets, :string, :limit => 30
    add_colum :show_location, :tweets, :boolean, :default => false
  end
end
```



## References
- [RoR Guides](http://guides.rubyonrails.org/)
    - [Associations](http://guides.rubyonrails.org/association_basics.html)
    - [Migrations](http://guides.rubyonrails.org/migrations.html)
    - [Query Interface](http://guides.rubyonrails.org/active_record_querying.html)
    - [Validations & Callbacks](http://guides.rubyonrails.org/active_record_validations_callbacks.html)
- [RoR Docs: ActiveRecord::Migration < Object](http://api.rubyonrails.org/classes/ActiveRecord/Migration.html)
