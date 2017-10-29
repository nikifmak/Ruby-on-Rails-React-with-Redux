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

### reverse, upcase

```ruby
puts "string".methods.sort
```

## Methods Name Conventions

## to_something

Methods that are used for type convertion. `to_<something>`.

```ruby
p 3 # 3
p 3.to_s # "3"
p "3".to_i # 3
p "3".to_f # 3.0

p "120 bananas".to_i # 0 
```

### Method +

```ruby
puts "2" + 5

# Error
no implicit conversion of Fixnum into String
```

The `+` sign actually is a method of the string "2", `.+`. When we write `puts "2" + 5`, it actually is:

```ruby
puts "2".+(5)

# fixed
puts "2".to_i + 5
```

And that is because we get the type error.

## ! Dangerous methods

Methods with an `method_name!` at the end of their name have a **safe** version with the name `method_name`.

<u>Safe method example:</u>

```ruby
vigilante = "Batman"
vigilante.upcase

p vigilante # "Batman
```

> The initial variable remains the same.

Dangerous method:

```ruby
vigilante = "Batman"
vigilante.upcase!

p vigilatnte # "BATMAN"
```

> It changes the variable.

So Dangerous methods are impure thus they have side effects.

## ? Boolean methods

These methods return `true` or `false`.

```ruby
p vigilante.nil? # false

p nil.nil? # true

p "Batman".include?("B") # true

p vigilante.empty? # true

p " ".empty? # false
```

## Optional Arguments

```ruby
def sum(x, y)
  x + y
end

p sum(1, 2 ,3) # wrong number of arguments (given 3, expected 2)
```

We can define the function with default arguments so when we pass less than the number we have defined arguments then ruby replaces them with the default defined values.

```ruby
def sum(x, y=0, z=0)
  x + y + z
end

p sum(6) # 6
p sum(1, 2, 3) # 6
```

## Scopes

We can use the same variable name in different parts of our program and the reason we can do that is because of a concept called "Scope".

We can think about scope as the context in which a variable means the same thing.

```ruby
def my_house
  dog = "ermis"
end

puts dog #undefined local variable or method `dog'
```

```ruby
bananas = 0 

def pick_banana
  bananas += 1
end

pick_banana # undefined method `+' for nil:NilClass
```

Inside the method `pick_banana` the is no reference to the `bananas` variable. To fix this we need to define an `instance variable`.

```ruby
# instance variable
@bananas = 0
```

Now `@bananas` is an instance variable that belongs to `Main` object

```ruby
@bananas = 0 

def pick_banana
  @bananas += 1
end

pick_banana # 1 
```

## Better to use the smallest possible scope

```ruby
@bananas = 0 # instance variable

def pick_banana
  @bananas += 1
end

pick_banana # 1

bananas = 23 # local variable

def tally_me_banana
  puts "You've picked #{@bananas} bananas"
end

def tally_me_banana(fruit)
  puts "You've picked #{fruit} bananas"
end

tally_me_banana(bananas) # You've picked 23 bananas
```

