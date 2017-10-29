# Methods

**Methods** are something an object can do. We can ask the object to do a method like this.

```ruby
"Knight".reverse # "thginK"
```

>  `"Knight"` is the receiver of the method `reserve` or we could say that we are calling/running/invoking the method `reverse` on `"Knight"`.

```ruby
3.next # 4
```

```ruby
puts "batman".upcase # BATMAN

return_value = "Hello World".swapcase
puts return_value

"Hello World".include?("Hell") # true

puts "Hello World".insert(6, "!!") # Hello !!World
```

## Parenthesis

Parenthesis ( ) are optional. If you have an argument, you use them. If you don't have any arguments, omit them.

```Ruby
p 3.next()
p 3.next
```

## Kernel Methods

Kernel methods can be called without a receiver.

```ruby
puts("Superman")
Kernel.puts("Spiderman")
```

All objects have `puts, p, print` are private methods.

```Ruby
3.puts("hello") # Error
# private method `puts' called for 3:Fixnum
```

## Function with argument as object

```ruby
return_value_p = p 3 # 3
return_value_puts = puts 3

p return_value_p # 3
p return_value_puts # nil
```

## Definition of functions

We define functions with the keywords `def` and `end`. Theses keywords are reserverd so assigning them a value with cause a syntax error.

````ruby
def say_hello
  puts "Hello"
end
````

We run this script we get:

````Ruby
:say_hello
````

Where `:` symbol is representing the method name. When we want to refer to a method without calling it we use the `:` symbol like this : `:method`.

To call the method we simply write:

```ruby
say_hello # Hello
```

Let's define a method with parameters which prints something with string interpolation.

```ruby
def greet(name)
  puts "Hello, #{name}!" 
end

greet("nikif") # Hello, nikif!
```

Example 2:

```ruby
def sum(x, y)
  return x + y
end

puts sum(3, 4) # 7

puts sum("hello", "world") # "helloworld"
```

## Implicit Return

We can omit the `return` keyword because ruby uses implicit return namely it returns the last expression or the result of evaluating the last expression.

```ruby
def product(x, y)
  x * y
end

puts product(12 ,6) # 72
```

## Early return

```ruby
def exit_early
  return "la la la"
  puts "This string never prints"
end

p exit_early # "la la la"
```

## Methods' return values

All methods have a return value (even sometimes `nil`)

Some methods have side effects e.g. outputting text to console or changing a value of a pass parameter.

## Function

Like a method, but it belongs to no object.

## Pure Function

A function that has no side effects. It just returns a value without changing something.

## Main Object

Even these methods defined at the top level belong to an object (`main`) available everywhere call them without a receiver.

## Programming Paradigms:

- object-oriented vs Functional

Ruby is object oriented but defining methods at the top level we can simulate functional programming.

## Chaining methods

Chaining methods is calling methods right after each other.

```ruby
"Surfer Dude".swapcase # "sURFER dUDE"

def square_sum(x ,y)
  x**2 + y**2
end

square_sum(20, 10) # 500
```

## Pass the return value as an argument. Call a method on the return value.

```ruby
other_return_value = "Bod Dylan".downcase
other_return_value.reverse # "nalyd dob"
```

Becomes:

```Ruby
"cool guy".reverse.update.insert(4, "ooo")
```

Or

```ruby
puts square_sum(20 , square_sum(2, 4))
```

## User input with chaining

```ruby
puts "enter the code word"
input = gets.chomp.strip.downcase
```

- `gets` *gets* a line of text, *including* a line break at the end. 
- `gets` returns that line of text as a string value.
- Calling `chomp` on that value removes the line break.
- `strip` returns a copy of *str* with leading and trailing whitespace removed.

```ruby
"hello\n".chomp         #=> "hello"
"    hello    ".strip   #=> "hello"
"\tgoodbye\r\n".strip   #=> "goodbye"
```

## Built-in methods

### reverse

