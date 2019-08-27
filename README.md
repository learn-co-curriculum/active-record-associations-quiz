## Quiz: Active Record Associations

???

# Active Record Associations

?:

![Pokémon Trainer with 6 Pokémon](https://curriculum-content.s3.amazonaws.com/active-record-associations/quiz/ar-associations-Pokémon.jpg)

Imagine that you are a Pokémon trainer. A Pokémon trainer can carry up to 6 Pokémon at a time. If you were to have a model for `Trainer` and a model for `Pokemon`, what type of relationship would be best to use?

( ) One-to-one (X) One-to-many ( ) Many-to-many ( ) None of the Above

?:

![Pokémon Trainer's Pokedex. Design Credits: www.vecteezy.com](https://curriculum-content.s3.amazonaws.com/active-record-associations/quiz/ar-associations-pokedex.jpg)


A Pokémon trainer uses a Pokedex to help them identify Pokémon. If you have your `Trainer` model, and a model for a `Pokedex`, what type of relationship would be best to use?

(X) One-to-one ( ) One-to-many ( ) Many-to-many ( ) None of the Above

?: A Pokémon trainer can hone their Pokémons' skills at a gym. Each Pokémon trainer can train at multiple gyms. What type of relationship would be best to use?

( ) One-to-one (X) One-to-many ( ) Many-to-many ( ) None of the Above

?: If each city has only 1 gym and each gym has only 1 gym leader, how could you write this association?

( )
```ruby
class Gym < ActiveRecord::Base
  belongs_to :city
  has_many :leaders
end
```
( )
```ruby
class Gym < ActiveRecord::Base
  has_many :cities
  belongs_to :leader
end
```
( )
```ruby
class Gym < ActiveRecord::Base
  has_many :cities
  has_many :leaders
end
```
(X)
```ruby
class Gym < ActiveRecord::Base
  belongs_to :city
  belongs_to :leader
end
```

?:

```ruby
class Pokemon < ActiveRecord::Base
  belongs_to :trainer
  belongs_to :type
end

class Trainer < ActiveRecord::Base
  has_many :Pokémon
end

class Type < ActiveRecord::Base
  has_many :Pokémon
end
```

A Pokémon has a "type" associated with it. For this example, let's imagine that Pokémon only have a single type (ice, fire, water, grass, earth, etc). The type of Pokémon determines what skills can be learned, and what strengths and weaknesses it can have, and therefor are associated with the trainer. What type of relationship can be created between `Trainer` and `Type`?

( )
```ruby
class Trainer < ActiveRecord::Base
  belongs_to :type
end
```
( )
```ruby
class Trainer < ActiveRecord::Base
  has_many :types
end
```
( )
```ruby
class Type < ActiveRecord::Base
  has_many :trainers
end
```
(X)
```ruby
class Trainer < ActiveRecord::Base
  has_many :types, through: Pokémon
end
```

?: A Pokedex is a mini-encyclopedia of Pokémon species, types, evolutions, and moves. A `Pokedex` model would have `has_many` relationship for `Pokemon`?

(X) True ( ) False

?:

```ruby
class Pokemon < ActiveRecord::Base
  belongs_to :trainer
  belongs_to :type
end

class Skill < ActiveRecord::Base
  belongs_to :type
end
```

Gym leader Misty specializes in training Pokémon with the _water_ type. Based on the associations above, if she wanted to teach a new skill to one of her Pokémon, which could she choose?

(X) Waterfall ( ) Razor Leaf ( ) Fire Spin ( ) Spark

?:

```ruby
class Pokemon < ActiveRecord::Base
  belongs_to :trainer
  belongs_to :type
end
```

What association should be added to the `Pokemon` model so that `Skill`s can be attributed to it?

(X) `belongs_to :skill` ( ) `has_many :skills, through :type` (X) `has_many: skills` ( ) None of the Above

?: A Pokémon trainer acquires a new badge each time they defeat a gym leader in battle. How should the `Badge` model be written so that it's associated to the `Gym` model?

(X)
```ruby
class Badge < ActiveRecord::Base
  belongs_to :gym
end
```
( )
```ruby
class Badge < ActiveRecord::Base
  has_many :gyms
end
```
( )
```ruby
class Badge < ActiveRecord::Base
  has_many :gyms, through :trainer
end
```
( )
```ruby
class Badge < ActiveRecord::Base
  belongs_to :leader
end
```
?: A Pokémon trainer can have many `Skill`s through `Pokemon`?

(X) True ( ) False

???
