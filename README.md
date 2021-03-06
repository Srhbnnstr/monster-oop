#<img src="https://cloud.githubusercontent.com/assets/7833470/10423298/ea833a68-7079-11e5-84f8-0a925ab96893.png" width="60"> Class-based Object Oriented Programming

Ruby <img alt="heart" src="https://em.wattpad.com/6d0355863f6ca950858ed30d2b8b9b1fe982b54c/687474703a2f2f727562792e7a69677a6f2e636f6d2f77702d636f6e74656e742f75706c6f6164732f73697465732f322f323031332f30312f7370696b655f616e645f7261726974795f5f735f68656172745f7368617065645f666972655f727562795f62795f65647761726474656e2e706e67" width="24px">'s Object Oriented Programming

##Learning Objectives

| Objectives: Students will be able to... |
|:--- |
| Distinguish between objects in JS, hashes and objects in Ruby, and classes in Ruby. |
| Create your own class and use the `initialize` method to set up initial behavior. |
| Define attributes and methods for instances, and for the class as a whole. |

##Hashes

Recall: Hashes are simple key value stores. They look a lot like JavaScript's objects.

**Hash Example**

```ruby
 ourhash = {name: "Napoleon", fav_food: "steak", skills: ["archery", "combat", "egg farming"]}

 # => {:name=>"Napoleon", :fav_food=>"steak", :skills=>["archery", "combat", "egg farming"]}
```

Recall that there are 2 notations for hashes, a colon (`:`) notation and a hash rocket (`=>`) notation.  The colon notation always results in your keys being symbols, which is usually what we want. The hash rocket notation gives you more control over the types of your keys.

##Objects

Ruby also has Objects. In fact, everything in Ruby is a BasicObject. However, we almost never use plain vanilla Objects because there are more sophisticated, specialized object types such a `String`, `Integer`, and `Hash`.


**Class Inheritance Tree**

![Class inheritance](http://i.stack.imgur.com/rvcEi.png)


**Example:**
How can we prove that the hash we just created is a `BasicObject`, through `Hash` and `Object`?


```ruby
ourhash.class
# => Hash  

Hash < Object     
# => true

Object < BaseObject
# => true

# or a shortcut:
ourhash.is_a? BasicObject
# => true
```


##Classes

Ruby uses **classes** for object-oriented programming.  Classes are data types used to create more data.  They are similar to the object types we manipulated with constructors and prototypes in JavaScript.  Classes are more common among programming languages than prototypes, so we'll go into more depth about OOP with Ruby than we did with JavaScript. (Also, JavaScript has classes as of its latest version: ECMAScript 6.)

> **Challenge:** create a `Monster` class and an instance of `Monster`.
> *Hint: you'll have to use the Ruby reserved words `class` and `new`.*


## `initialize`

> **Challenge** Update the `Monster` class so that a monster goes "Rawr!" when it's first initialized.

![monster rawr gif](https://s-media-cache-ak0.pinimg.com/originals/8e/dd/5d/8edd5de39a2c832745df9f8dfca15547.jpg)


## Instance Variables

What should we do if we want to set attributes on the monster, such as its `habitat`?

Since each monster will probably have a different habitat, this is a good candidate for an instance variable. Remember Ruby classes mark instance variables with `@`.

> **Challenge:**
Add a `habitat` instance variable and any instance methods needed to your Monster class to enable this code...

> ```ruby
rabbit = Monster.new
# Rawr
rabbit.habitat = "Cave of Caerbannog"
rabbit.habitat
# => "Cave of Caerbannog"
```

> *Hint: Use the methods `attr_accessor`, `attr_reader`, and/or `attr_writer`*

> *Stretch: Don't use any of the  methods listed in the last hint*

<br>

>**Challenge:** Add a `threat_level` instance variable to the Monster class. Allow the user to specify a threat level when the monster is created.

>```ruby
dalek = Monster.new(:high)
dalek.threat_level
=> :high
```
> *Hint*: use `initialize`

<br>

> **Challenge:** Allow the user to create an instance of `Monster` without specifying a threat level. The default threat level for a new monster should be `:medium`.

>```ruby
teletubby = Monster.new
teletubby.threat_level
=> :medium
```

##Instance Methods

**Challenge:** Create a `habitat?` instance method for `Monster` that tests whether the monster's habitat matches an argument that is passed in.

> ```ruby
yeti = Monster.new
# Rawr!
yeti.habitat = "tundra"
yeti.habitat?("swamp")
# => false
yeti.habitat?("tundra")
# => true
```

> *Hint: use `def` to define a new method inside the class*

##Class Variables and Class Methods

What if I wanted a running count of all the Monsters ever created?  Let's keep track with a class variable and print a message each time a new monster spawns.

> **Challenge:** Add a class variables to enable this code...

> ```ruby
predator = Monster.new(:high)
# Rawr!
# 2 monsters now roam the world!
alien = Monster.new(:high)
# Rawr!
# 3 monsters now roam the world!
```

> *Hint: Create a class variable with `@@`*

<br>

>**Challenge:** Create a class method to get the current value of the monster count.

>```ruby
Monster.count
# => 3
```

>*Hint: Use the reserved word `self`*

**Note** Class variables are used much less often than instance variables!

>**Stretch Challenge:** Add a check so that the allowed `threat_level` values at creation are`:low`, `:medium`, `:high`, or `:midnight`.   If another value is passed in as the initial threat_level, `raise` a runtime error.

>```ruby
rubber_ducky = Monster.new(:friendly)
# /monster_stretch.rb:31:in `initialize': cannot create monster - invalid threat level friendly (RuntimeError)
#  from manual_test.rb:99:in `new'
#  from manual_test.rb:99:in `<main>'
```

<br>

>**Stretch Challenge:** Create a class constant called `THREAT_LEVELS` that is an array containing all the allowed values of `threat_level`.

>*Hint: Access the class constant with `Monster::THREAT_LEVELS`.*

>*Hint: Use `freeze` to make sure the value of `THREAT_LEVELS` isn't changed later.*

<br>

> **Challenge:** Create a `fight` class method for `Monster` that takes in two monster instances and compares their  `threat_level`s. The `fight` method should return the monster that has the higher threat level. If they're tied, let the second monster win.

<br>

> **Stretch Challenge:** Refactor `fight` to use `index` with the `THREAT_LEVELS` array. You should be able to make `fight` code shorter and simpler.

<br>

> **Stretch Challenge:** Include <a href="http://ruby-doc.org/core-2.2.3/Comparable.html">the `Comparable` mixin</a> in your `Monster` class and create a custom `<=>` method to compare monsters based on their threat levels. Refactor `fight` to use this comparison.

<br>

> **Compassion Challenge:** Give your `Monster` class a `name` instance variable with a getter and a setter.

> *Hint: only modify `initialize` as a stretch (solution not provided). If you modify `initialize` so it takes a `name` argument, update the tests to give each monster instance a name.  Wondering how you could make the `name` argument optional like `threat_level`? Look up Ruby's "keyword arguments" syntax.*


<img alt="monster" src="http://blog.spoongraphics.co.uk/wp-content/uploads/2009/furry-monster/monster.jpg" width=300px>

## Quick Review

  * What is a class?
    - What is an attribute?
    - What is a method?
  * What is the difference between:
    - an instance variable
    - a class variable
  * What is the difference between:
    - an instance method
    - a class method
  * Why do we use classes?
  * Looking ahead: What is inheritance?


  ## Head over to [Part 2](part2.md)
