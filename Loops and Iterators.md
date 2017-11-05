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



