# Ruby Cheat-sheet

## Printing to screen
```ruby
print "prints something"
puts "prints something with new line"
```

## Comments
Single
```ruby
# some comment
```
Multiline
```ruby
=begin
 some comment
=end
```

## Receiving input from the user:
```ruby
print "What's your first name?"
first_name = gets.chomp
print first_name
```

## Variables
```ruby
name = name.capitalize

# same as
name.capitalize!
```

* `!` at the end of a method mutates the variable itself.

## Conditional Assignment
If we want to to assign a variable if it hasn’t already been assigned we use `||=` instead of `=`
```ruby
animal = nil
puts animal # nothing

animal ||= "Cat"
puts animal # prints: Cat

animal ||= "Dog"
puts animal # prints: Cat

animal = "Horse"
puts animal # prints: Horse
```

## String functions
```ruby
# To downcase
string.downcase

# To uppercase
string.upcase

# Global string substition:
string.gsub!(/s/, "th")

# Check if the string includes some other string
string.include? "something"

# String literal:
"#{var_a}: #{var_b}"

# Accessing string char array:
"abcde"[0] # will return: "a"
"abcde"[0..-1] # -1 is same as string.length. Will return "abcde"
"abcde"[1..-1] # -1 is same as string.length. Will return "bcde"
```

## Symbol
In Ruby, symbols are immutable names primarily used as hash keys or for referencing method names.
```ruby
 puts "string".object_id # 21541180
 puts "string".object_id # 21540920

 puts :symbol.object_id # 802268
 puts :symbol.object_id # 802268
```

## .respond_to?
`.respond_to?` takes a `symbol` and returns `true` if an object can receive that method and false otherwise. 
```ruby
age = 26
age.respond_to?(:next) # will return true since "next" can work on integers
```

## If statement
```ruby
if 4 > 2
  print "hey"
end

#Else/Else if
if x < y 
  puts "x is less than y!"
elsif x > y
  puts "x is greater than y!"
else
  puts "x equals y!"
end
```

## Unless
Sometimes you want to use control flow to check if something is false, rather than if it’s true. <br/>You could reverse your if/else, but Ruby will do you one better: it will let you use an unless statement.
```ruby
hungry = false
unless hungry
  puts "I'm writing Ruby programs!"
else
  puts "Time to eat!"
end
```

## Shortened
```ruby
ruby_is_eloquent = true
ruby_is_ugly = false

puts "Ruby is eloquent!" if ruby_is_eloquent
puts "Ruby's not ugly!" unless ruby_is_ugly
```

## Ternary
```ruby
puts 2 > 1 ? "True" : "False"
```

## Switch case
```ruby
case choice
 when 'add'
  # do something
 when 'remove'
  # do something
 else
  # some default
end 

# Same, but return is on the same line

case choice
 when 'add' then # do something
 when 'remove' then # do something
 else # some default
end 
```
## Concatenation operator
```ruby
alphabet = ["a", "b", "c"]
alphabet << "d"
# Same as alphabet.push("d")

caption = "Some text and "
caption << "even more text!"
# Same as caption += "even more text!"
```

## While
```ruby
counter = 1
while counter < 11
  puts counter
  counter = counter + 1
end
```

## Until
```ruby
counter = 1
until counter == 10
  puts counter
  counter = counter + 1
end
```

## For
```ruby
for num in 1...10
  puts num
end
# Three dots -> Will print 1 to 9

for num in 1..10
  puts num
end
# Two dots -> Will print 1 to 10
```

## Loop do
```ruby
i = 20
loop do
  i -= 1
  print "#{i}"
  break if i <= 0
end
```

## Breaking out of loops or loop steps
```ruby
# skip a step:
next if
# Break from the loop
break if
```

## Block syntax
Block syntax uses either do..end or curly braces ({}), like so:
```ruby
[1, 2, 3].each do |num|
  puts num
end
# ==> Prints 1, 2, 3 on separate lines

[1, 2, 3].each { |num| puts num }
# ==> Prints 1, 2, 3 on separate lines
```

## .each Iterator
```ruby
array = [1,2,3,4,5]
 
array.each { |x| 
  x += 10
  print "#{x}"
}
```

## .times Iterator
Runs a piece of code X times
```ruby
10.times { print "Chunky bacon!" }
```

## upto/downto Iterator
```ruby
"L".upto("P") { |letter| print letter } # will print LMNOP
100.downto(97) { |num| print "#{num}, " } # will print "100, 99, 98, 97, "
```

## Hash
```ruby
my_hash = { "name" => "Eric",
  "age" => 26,
  "hungry?" => true
}
puts my_hash["name"]
puts my_hash["age"]
puts my_hash["hungry?"]
```

Creating an empty hash:
```ruby
my_hash = Hash.new
#or
my_hash = {}
```
By default hash will return `nil` when requesting for a non existing key. But we can set another default:
```ruby
my_hash = Hash.new("Some default")
```

Deleting a key:
```ruby
 someHash.delete(key)
```

Ruby 1.9 syntax (With this syntax, each key is automaticly a symbol)
```ruby
new_hash = { 
  one: 1,
  two: 2,
  three: 3
}

puts new_hash["one"] // nothing
puts new_hash[:one] // 1
```

Iterating over a hash:
```ruby
someHash.each { |key, value| puts "#{key}: #{value}" }
```

Iterating over a hash keys:
```ruby
someHash.each_key { |key| puts key }
```

Iterating over a hash values:
```ruby
someHash.each_value { |value| puts value }
```

## sort
```ruby
 my_array = [3, 4, 8, 7, 1, 6, 5, 9, 2]
 my_array.sort!
 puts my_array # will return [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Ruby Combined Comparison Operator <=>
In Ruby, the combined comparison operator, <=>, also known as the spaceship operator is used to compare two objects. <br/>It returns 0 if the first operand equals the second, 1 if the first operand is greater than the second, and -1 if the first operand is less than the second.

```ruby
puts "Keanu" <=> "Adrianna" # The first letters of each word are compared in ASCII order. "k" > "a" so it will print 1

puts 2 <=> 1 # 1
puts 1 <=> 2 # -1
puts 3 <=> 3 # 0
```

## sort (custom)
```ruby
someArray.sort! { |a, b| a <=> b }
```

## .sort_by 
```ruby
someHash = {
 "b" => 5,
 "c" => 3,
 "a" => 2
}

# sorting by key
arrayOfArrays = someHash.sort_by do |key, value|
  key
End
# arrayOfArrays = [["a", 2], ["b", 5], ["c", 3]]

# sorting by value
arrayOfArrays = someHash.sort_by do |key, value|
  value
End

# arrayOfArrays = [["a", 2], ["c", 3], ["b", 5]]
```

## .select (filters a data structure)
```ruby
movie_ratings = {
  memento: 3,
  the_matrix: 5,
  lion_king: 3.5
}

good_movies = movie_ratings.select { |name, rating| rating>3 }
```

## .collect/.map 
Returns a new array based on a callback function called upon each item
```ruby
 my_nums = [1, 2, 3]
 my_nums.collect { |num| num ** 2 }
 # ==> [1, 4, 9]
```
If we want to mutate the original array, we can use `!` (`my_nums.collect! { |num| num ** 2 }`)

## Conversion
```ruby
# To array (Will return: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
  puts (1..10).to_a

# To string (Will return: 5)
  puts 5.to_s

# To Integer (# Will return: 5)
  puts "5".to_i
  
# To Symbol (converts a string to a symbol)
 string.to_sym
# can also be done with .intern
 str.intern
```

## Methods
```ruby
# No paramters
def someFunc:
  puts "Hello"
end
 
# With parameters
def someFunc(name):
  puts "My friend is " + name + "."
end

# Paramters with default value
def someFunc(param1, param2=false)
  ...
end
 
# With rest param
def someFunc(greeting, *friends)
  friends.each { |friend| puts "#{greeting}, #{friend}!" }
end

# With return
def add(a,b)
  return a + b
end

# Ruby’s methods will return the result of the last evaluated expression, so this is the same:
def add(a,b)
  a + b
end
```

* A question mark at the end of a Method's name indicates it will return a boolen. `def willReturnBool?`

## yield
Why do some methods accept a block and others don’t? It’s because methods that accept blocks have a way of transferring control from the calling method to the block and back again. We can build this into the methods we define by using the yield keyword.

```ruby
def block_test
  puts "We're in the method!"
  puts "Yielding to the block..."
  yield
  puts "We're back in the method!"
end

block_test { puts ">>> We're in the block!" }
```
Will print:
```
We're in the method!
Yielding to the block...
>>> We're in the block!
We're back in the method!
```

## yield with parameters
```ruby
def yield_name(name)
  puts "In the method! Let's yield."
  yield("Kim")
  puts "In between the yields!"
  yield(name)
  puts "Block complete! Back in the method."
end

yield_name("Eric") { |n| puts "My name is #{n}." }
```
Will print:
```
In the method! Let's yield.
My name is Kim.
In between the yields!
My name is Eric.
Block complete! Back in the method.
```

## Proc
Proc allows us to store and reuse blocks of codes. Proc will also turn a block to an object.

```ruby
multiples_of_3 = Proc.new do |n|
  n % 3 == 0
end

print (1..9).to_a.select(&multiples_of_3)

# will print: [3, 6, 9]
```

yield + Proc
```ruby
def greeter
  yield
end

phrase = Proc.new { puts "Hello there!" }
greeter(&phrase)
```

### .call
.call let's us invoke a Proc
```ruby
hi = Proc.new {puts "Hello!"}
hi.call
```

### Symbols as procs
```ruby
numbers_array = [1, 2, 3, 4, 5]

strings_array = numbers_array.map(&:to_s)

puts strings_array # Will print ["1", "2", "3", "4", "5"]
```

## Lambda
Like procs, lambdas are objects. The similarities don’t stop there: with the exception of a bit of syntax and a few behavioral quirks, lambdas are identical to procs.
```ruby
def lambda_demo(a_lambda)
  puts "I'm the method!"
  a_lambda.call
end

lambda_demo(lambda { puts "I'm the lambda!" })
```
will print
```
I'm the method!
I'm the lambda!
```

More examples:
```ruby
# Example A
strings = ["leonardo", "donatello", "raphael", "michaelangelo"]
symbolize = lambda{|param| param.to_sym}
symbols = strings.collect(&symbolize)
print symbols # [:leonardo, :donatello, :raphael, :michaelangelo]

# Example B
my_array = ["raindrops", :kettles, "whiskers", :mittens, :packages]
symbol_filter = lambda {|item| item.is_a? Symbol}
symbols = my_array.select(&symbol_filter)
puts symbols # [:kettles, :mittens, :packages]
```

## Lambdas vs. Procs
1. lambda checks the number of arguments passed to it, while a proc does not. 
This means that a lambda will throw an error if you pass it the wrong number of arguments, whereas a proc will ignore unexpected arguments and assign nil to any that are missing.
<br/><br/>
2. When a lambda returns, it passes control back to the calling method; 
When a proc returns, it does so immediately, without going back to the calling method.

```ruby
def proc_example
  some_proc = Proc.new { return "A!" }
  some_proc.call
  "B!"
end

puts proc_example
# Will print "A!"

def lambda_example
  some_lambda = lambda { return "A!" }
  some_lambda.call
  "B!"
end

puts lambda_example
# Will print "B!"
```

# Object oriented

## Class
```ruby
class Person
  def initialize(name) # same as constructor in JS
    @name = name
  end
end

brian = Person.new("Brian")
```

## Scoping:
$ - global variable that can be accessible outside of the class
<br/>@ - variable belongs to the instance
<br/>@@ - variable belongs to the Class
```ruby
class Computer
  $manufacturer = "Mango Computer, Inc."
  @@files = {hello: "Hello, world!"}
  
  def initialize(username, password)
    @username = username
    @password = password
  end
  
  def current_user
    @username
  end
  
  def self.display_files
    @@files
  end
end

# Make a new Computer instance:
hal = Computer.new("Dave", 12345)
puts "Current user: #{hal.current_user}" # @username belongs to the hal instance.
puts "Manufacturer: #{$manufacturer}" # $manufacturer is global! We can get it directly.
puts "Files: #{Computer.display_files}" # @@files belongs to the Computer class.
```

### Class variable
```ruby
class Person
  @@people_count = 0
  
  def initialize(name)
    @name = name
    @@people_count += 1
  end
  
  def self.number_of_instances
    return @@people_count
  end
end

matz = Person.new("Yukihiro")
dhh = Person.new("David")

puts Person.number_of_instances # Will print: 2
```

### Public/Private methods
```ruby
  class Dog
    def initialize(name, breed)
      @name = name
      @breed = breed
    end

    public
    def bark
      puts "Woof!"
    end

    private
    def id
      @id_number = 12345 
    end
  end
  
  rexy = Dog.new("Rexy", "Labrador")
  rexy.bark # ok
  rexy.id # will throw an error
```

### Reading and writing to instance variables (attr_reader/attr_writer)

```ruby
# attr_reader/attr_writer saves us the time from writing seter and geter functions
class Person
  attr_reader :name
  attr_writer :job
  def initialize(name, job)
    @name = name
    @job = job
  end
end

# So it's the same as this:
class Person
  def initialize(name, job)
    @name = name
    @job = job
  end
  
  def name
    @name
  end
  
  def job=(new_job)
    @job = new_job
  end
end

```

### attr_accessor
If we want to both read and write a particular variable, there’s an even shorter shortcut than using attr_reader and attr_writer. 
We can use attr_accessor to make a variable readable and writeable in one fell swoop.

```ruby
class Person
  attr_reader :name
  attr_accessor :job
  
  def initialize(name, job)
    @name = name
    @job = job
  end
end
```

## Inheritance
```ruby
class DerivedClass < BaseClass
  # Some stuff!
end
```

### Overiding a method
```ruby
class Creature
  def initialize(name)
    @name = name
  end
  
  def fight
    return "Punch to the chops!"
  end
end

class Dragon < Creature
  def fight
    return "Breathes fire!"
  end
end

viserion = Dragon.new("Viserion")
puts viserion.fight # prints "Breathes fire!"
```
### super - adding to a method, instead of overriding
```ruby
class Dragon < Creature

  def fight
    puts "Instead of breathing fire..."
    super
  end
end
viserion = Dragon.new("Viserion")
puts viserion.fight # prints "Instead of breathing fire... Punch to the chops!"
```

## Module
You can think of a module as a toolbox that contains a set methods and constants.
Modules are similar to classes, only modules can’t create instances and can’t have subclasses. They’re just used to store things.
```ruby
module Circle
  PI = 3.141592653589793
  
  def Circle.area(radius)
    PI * radius**2
  end
  
  def Circle.circumference(radius)
    2 * PI * radius
  end
end
```

## Ruby namespace
In Ruby, the term `namespace` refers to a module the contains a group of related objects. An example of a Ruby namespace is the `Math` module.
``` ruby
#To retrieve a constant from the Math module, the scope resolution operator (::), should be used.

puts Math::PI
# => 3.141592653589793

#In this example, Ruby is targetting the PI constant from the Math module using the scope resolution operator, (::), and printing its value to the console.
```

## require
In Ruby, the require keyword is used to fetch a certain module which isn’t yet presented in the interpreter. It is best practice to place this at the beginning of your code.

```ruby
require 'date'

puts Date.today
# => 2020-04-16
```

## include
Any class that includes a certain module can use those module’s methods.
A nice effect of this is that you no longer have to prepend your constants and methods with the module name. Since everything has been pulled in, you can simply write PI instead of Math::PI.

```ruby
class Angle
  include Math
  attr_accessor :radians
  
  def initialize(radians)
    @radians = radians
  end
  
  def cosine
    cos(@radians) # No need to type the module: Math::cose
  end
end
```

## Mixins - Modules + Classes

### include
`include` mixes a module’s methods in at the instance level (allowing instances of a particular class to use the methods)
```ruby
module Action
  def jump
    @distance = rand(4) + 2
    puts "I jumped forward #{@distance} feet!"
  end
end

class Rabbit
  include Action
  attr_reader :name
  def initialize(name)
    @name = name
  end
end

class Cricket
  include Action
  attr_reader :name
  def initialize(name)
    @name = name
  end
end

peter = Rabbit.new("Peter")
jiminy = Cricket.new("Jiminy")

peter.jump
jiminy.jump
```

### extend
`extend` keyword mixes a module’s methods at the class level. 
This means that class itself can use the methods, as opposed to instances of the class.
```ruby
module ThePresent
  def now
    puts "It's #{Time.new.hour > 12 ? Time.new.hour - 12 : Time.new.hour}:#{Time.new.min} #{Time.new.hour > 12 ? 'PM' : 'AM'} (GMT)."
  end
end

class TheHereAnd
  extend ThePresent
end

TheHereAnd.now
```
