# Loops and Iterators

## While 

> While condition is not true do.

```ruby
counter = 0

while (counter < 10) do
  counter += 1
  puts counter
end
```

## Until

> Until the condition is to be met, do.

```ruby
bananas = 0

until bananas == 100 do
  bunch = rand(6)
  bananas += bunch
  puts "i have #{bananas} bananas."
end
```

## For object loop

```ruby
array = ['random', 'stuff', :for, 2454, 'string']

for item in array do
  puts item
end
```

## Ranges

`..` include the endpoint

```
puts 1..10
```

`… ` excludes the end point.

```ruby
array = ['random', 'stuff', 2454, 'string']

for i in (0...array.length) do
  array[i] *= 2
end

puts array # randomrandom stuffstuff 4908 stringstring
```

## Iterators over collections

Iterator are types of methods that take a block.

## Each

```ruby
object = ['stuff', 'inside', 'the', 'array']

object.each do |thing|
  puts thing.reverse
end
```

**Scope** is the context /part of the program where the variables means something.

We can replace the `for` loop with the following syntax:

```ruby
object.each { |element| puts element.reverse}
```

## Each with `…`

```ruby
(0...object.length).each do |i|
  object[i] = "evil " + object[i] 
end

p object
# ["evil stuff", "evil inside", "evil the", "evil array"]
```

## each_with_index

```ruby
dinosaurs = [
  'brachiosaurus',
  'brontosaurus',
  't-rex',
  'raptor'
]

dinosaurs.each_with_index do |dinosaur, index|
  dinosaurs[index] = "awesome " + dinosaur
end
```

## Map

`each` returns the original collection. `map` returns an altered copy of the collection that we can save to a variable. The `map` maps the collection to a new array in which each elements has been transformed according to the process specified in the block.

Example with each:

```ruby
bad_guys = [
  "Darth Vader",
  "Lex Luthor",
  "Joker"
]

opinions_about_bad_guys = []

bad_guys.each do |villain|
  opinion = "#{villain} is real bad news."
  puts opinion
  opinions_about_bad_guys << opinion
  
end
```

Mapping an array to a new array by keeping the original array the same.

```ruby
one_to_ten = 1..10
squares =[]

one_to_ten.each { |number| squares << number**2 }

p squares # [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# one_to_ten is the same
```

## Map Method

We can do the same thing with the `map` method without chaning the initial object.

```ruby
cubes = one_to_ten.map { |n| n**3 }
p cubes
```

## Map! Method

If we want to mutate the initial array we can use the `dangerous-impure` `map!` method.

```ruby
cubes = one_to_ten.map! { |n| n**3 }
p cubes
p one_to_ten
```

we get

```ruby
undefined method `map!' for 1..10:Range

Did you mean?  map
```

This is because `one_to_ten` is `Range` object and it can't be mutated. We can turn it to array to overcome this problem.

```ruby
one_to_ten = one_to_ten.to_a
cubes = one_to_ten.map! { |n| n**3 }
p cubes
p one_to_ten
```

`Map!` returns the initial object but after it has been mutated.

## Iterators for filtering data

## Select - Reject

Irerators take a block and execute the block for each member of the array.

```ruby
numbers = [1220, 320, 462, 123, 231, 7657]

numbers.each { |n| puts n.odd? }

# Return a new truth array  
numbers.map { |n| n.odd? }
```

We can filter the odd numbers with `select` iterator:

```ruby
odds = numbers.select! { |n| n.odd? } # [123, 231, 7657]
evens = numbers.reject { |n| n.odd?} # []
```

## Any?

Returns true if any of the elements meets the condition. 

```ruby
(1..10).any? { |n| n.odd? } # true
```

## All?

Returns true if all of the elements 

```ruby
doubles = (1..10).map { |n| n*2 }
doubles.all? { |n| n.even? } # true
```

Sometimes iterators execute the block for each element of the object and they stop early.

```ruby
(1..10).any? do |n|
  puts n; n.odd? # 1 stops at 1.
end
```

## Early stop

```ruby
(1..10).any? {|n| n % 7 == 0 }
```

```ruby
(1..10).any? do |n|
  puts n
  n % 7 == 0
end

# 1
2
3
4
5
6
7
=> true
```

```ruby
(1..10).all? do |n|
  puts n
  n % 7 == 0
end

# 1
=> false
```

Check the return value:

```ruby
(1..10).any? do |n|
  n % 7 == 0 # returns true
  puts n # always returns nil
end

# => false
```

## Find == detect

Get the first member for which block is true.

```ruby
puts (1..10).find {|n| n % 7 ==0 } # 7 => nil
puts (1..10).detect {|n| n % 7 ==0 } # 7 => nil
```



