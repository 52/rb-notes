`refine` giúp thay đổi hành vi của một class một cách tạm thời và trong một phạm vi giới hạn.
```ruby
module Shout
  refine String do 
    def shout
      self.upcase + "!!!"
    end
  end
end

class Person
  using Shout
  attr_accessor :name

  def say_hello
    puts "hello, my name is #{name.shout}"
  end
end

p = Person.new
p.name = "Dean"

p.say_hello
# => hello, my name is DEAN!!!

```