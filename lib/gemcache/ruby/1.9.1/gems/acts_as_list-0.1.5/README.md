# ActsAsList

## Description

This `acts_as extension` provides the capabilities for sorting and reordering a number of objects in a list. The class that has this specified needs to have a `position` column defined as an integer on the mapped database table.


## Example

    class TodoList < ActiveRecord::Base
      has_many :todo_items, :order => "position"
    end
    
    class TodoItem < ActiveRecord::Base
      belongs_to :todo_list
      acts_as_list :scope => :todo_list
    end
    
    todo_list.first.move_to_bottom
    todo_list.last.move_higher
    
## Notes
If the `position` column has a default value, then there is a slight change in behavior, i.e if you have 4 items in the list, and you insert 1, with a default position 0, it would be pushed to the bottom of the list. Please look at the tests for this and some recent pull requests for discussions related to this.

## Contributing to `acts_as_list`
 
- Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet
- Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it
- Fork the project
- Start a feature/bugfix branch
- Commit and push until you are happy with your contribution
- Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
- Please try not to mess with the Rakefile, version, or history. If you want to have your own version, or is otherwise necessary, that is fine, but please isolate to its own commit so I can cherry-pick around it.

## Copyright

Copyright (c) 2007 David Heinemeier Hansson, released under the MIT license
