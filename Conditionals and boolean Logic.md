# Conditionals and boolean Logic

```ruby
if condition
  puts "it was true"
else
  puts "it was false"
end
```

## Else if

```ruby
if x > y
  puts "#{x} is greater than #{y}"
elseif x == y
  puts "#{x} is equal to #{y}"  
else
  puts "#{x} is less than #{y}"  
end
```

## Case

```ruby
case door_number
when 1, "one"
  puts "1"
when 2, "two"
  puts "2"
else
  puts "else"
end
```

## One line ifs

```ruby
box = "bananas"
box = "apples"

if box == "bananas" then puts "my bananas have arrived!"
end
```

can be changed to

```ruby
puts "my bananas have arrived!" if box == "bananas"
```

as a function

```ruby
box = "bananas"

def check_for_bananas(box)
  return false if box != "bananas"
  puts "yeap bananas"
end

check_for_bananas(box)
```

## Ternary Operator/Expression

```ruby
def max(x, y)
  x > y ? x : y
end

```

## Case with multiple variables

```ruby
case [p_move, c_move]
when ['rock', 'scizzors'], ['paper','rock'], ['scizzors', 'paper']
when ...
when ['rock', 'rock'], ...
else
  puts "unexpected input"
end
```

another way to do it

```ruby
win_scenarios = [
  ['rock', 'scizzors'], 
  ['paper','rock',], 
  ['scizzors', 'paper']
]

lose_scenarios = [
  ['scizzors', 'rock'], 
  ['rock', 'paper'], 
  ['paper', 'scizzors']
]

game = [p_move, c_move]

if p_move == c_move
  puts "it's a tie"
elseif win_scenarios.include?(game)
  puts "you win"
elseif lose_scenarios.include?(game)
  puts "you lose"
else
  puts "unexpected input"
end
```

## Conditional Assignment 

We assign a value to a variable, only if the variable is currently falsey (nil, false)

```ruby
baby_name = baby_name || "Robert"
```

Can be written also:

```ruby
baby_name ||= "Robert"
```

