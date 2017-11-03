# Collections

## Arrays

Arrays are a type of collection. Its an object that holds/points to other objects, like a variable but it holds more that one object.

```ruby
fruits = [
  "orange",
  "apple",
  "kiwi"
]
```

```ruby
threes = [3, 3.0, '3', '3.0', 'three', :three]

puts threes
p threes
```

## Reverse look up

```ruby
fruits.index("orange") # 0
```

## Hashes 

A map to Key - value object

```ruby
prices = {
  "eggs" => 3.0,
  "milk" => 2.0,
  "bacon" => 5.0
  }

p prices["eggs"] # 3.0
```

```ruby
my_info = {
  "name" => "Nikif",
  "job" => "coding",
  "age" => 27
}
```

We use symbols as keys (when it makes sense) because are faster for ruby to look up. Symbols are like variables(lower case letters, underscores for spaces)

```ruby
contact_card = {
  :name => "Bruce Wayne",
  :email_address => "notbatman@batman.com",
  :friends => ["Ni", "Na", "SI"]
}

p contact_card[:name] # "Bruce Wayne"
p contact_card["name".to_sym] # "Bruce Wayne"
```

Trying to access the hash with a key that's not defined returns the default value (nil). But we can change the default value.

```ruby
contact_card.default = "Info not found"
p contact_card["name"] # "Info not found"
```

## Alternative Hash syntax

Instead of using the `=>` symbol if we want all our keys to be symbols we can use the following alternative syntax

```ruby
contact_card_2 = {
  name: "Alfred Pennyworth",
  email_address: "batman@batman.com"
 }

p contact_card_2[:name] # "Alfred Pennyworth"
```

## Nested hashes inside array

```ruby
contacts = [contact_card, contact_card_2]
```

```ruby
p contacts[0][:friends][0] # "Ni"
```

## Adding Values to Hashes

```ruby

```



