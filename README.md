Keys in association
=================


Composite Key

    class Membership < ActiveRecord::Base
      # self.primary_keys *keys - turns on composite key functionality
      self.primary_keys :user_id, :group_id
      belongs_to :user
      belongs_to :group
      has_many :statuses, :class_name => 'MembershipStatus', :foreign_key => [:user_id, :group_id]
    end


    class MembershipStatus < ActiveRecord::Base
      belongs_to :membership, :foreign_key => [:user_id, :group_id]
    end

http://compositekeys.rubyforge.org/


Alias attribute in model

    class User < Activerecord::Base
      alias_attribute :new_column_name, :real_column_name
    end


Alias methode 

     class Microwave
       def on
         puts "The microwave is on"
       end
     
       alias :start :on
     end
     
     m = Microwave.new
     m.start # same as m.on
 
 
