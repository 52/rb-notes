### Why we should use `lambda` instead of  `Proc.new`
#### `Proc.new`
A block created with `Proc.new` behaves like it’s **a part of the calling method** when `return` is used within it, and returns from both the block itself as well as the calling method.
```ruby
def a_method
 Proc.new {return "we just returned from the block"}.call
 return "we just returned from the calling method"
end

puts a_method
# => we just returned from the block
```
#### `lambda`
A block created with `lambda` behaves like a method when you use `return` and simply exits the block, handing control back to the calling method.
```ruby
def a_method
 lambda {return "we just returned from the block"}.call
 return "we just returned from the calling method"
end

puts a_method
# => we just returned from the calling method
```
---
As a consequence, `Proc.new` is something that’s hardly ever used to explicitly create blocks because of these surprising return semantics. It is recommended that you avoid using this form unless absolutely necessary.

Source: [RubyMonk](https://rubymonk.com/learning/books/4-ruby-primer-ascent/chapters/18-blocks/lessons/64-blocks-procs-lambdas)


