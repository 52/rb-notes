## `extend` là gì?
Dùng `extend` để mở rộng hành vi của một **object** thông qua module.
Ví dụ:
```ruby
class Person
end

module Talkable
  def hello
    puts "Hello, world!"
  end
end

p = Person.new
```
```ruby
p.extend Talkable
p.hello # => Hello, world!
```
Việc dùng `extend` như trên tương đương với việc `include` module `Talkable` trong **singleton class** của object `p`:
```ruby
class << p
  include Talkable
end
```
tương đương với:
```ruby
class << p
  def hello
    puts "Hello, world!"
  end
end
```
tương đương với:
```ruby
def p.hello
  puts "Hello, world!"
end
```
**Tóm lại:**
Khi object `p` `extend` module `M`, thì tất cả các methods trong module `M` trở thành **singleton methods** của object `p`.
## So sánh`extend` với `include`/`prepend` 
Cả 2 đều dùng để mở rộng hành vi thông qua **module**.
Tuy nhiên:
- `extend` mở rộng hành vi cho một đối tượng (**object**)
- `include`/`prepend` mở rộng hành vi cho một lớp các đối tượng (**class**)

Ví dụ về `include`:
```ruby
class Person
  include Talkable
end
p1 = Person.new
p2 = Person.new
p1.hello # => Hello, world!
p2.hello # => Hello, world!
```
Khi class `C` `include` module `M`, thì tất cả các methods trong module `M` trở thành **instance methods** của class `C`.

Ví dụ về `extend`:
```ruby
class Person
  extend Talkable
end

Person.hello # => Hello, world!

p = Person.new
p.hello # => undefined method `hello`
```
Khi class `C` `extend` module `M`, thì tất cả các methods trong module `M` trở thành **class methods** của class `C`.

### Tại sao?
- Class `C` là object của class `Class`: 

```ruby
C.instance_of? Class # => True
```
- Khi **class object** `C` `extend` module `M`, thì tất cả các methods trong module `M` trở thành **singleton methods** của **class object** `C`.
- **singleton methods** của **class object** `C` chính mà **class methods** của class `C`.