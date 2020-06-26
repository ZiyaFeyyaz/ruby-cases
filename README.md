#### 1
```ruby
class A
  def test(arg = 'test')
    arg
  end
end

class B < A
  def test(arg = 'test')
    super
  end
end

class C < A
  def test(arg = 'test')
    super()
  end
end

puts A.new.test('aaa') # => aaa
puts B.new.test('bbb') # => bbb
puts C.new.test('ccc') # => test
```

#### 2
```ruby
module M
  private

  def test
    'test'
  end
end

class A
  include M
end

puts A.new.test # => NoMethodError
```

#### 3
```ruby
"\n" == '\n' # => false
```

#### 4
```ruby
String === 'zzz' # => true 
'zzz' === String # => false
```

#### 5
```ruby
class A
  def test1
    'test1'
  end

  def test2
    'test2'
  end
end

class A
  def test1
    'new test1'
  end

  def test3
    'test3'
  end
end

a = A.new
puts a.test1 # => new test1
puts a.test2 # => test2
puts a.test3 # => test3
```

#### 6
```ruby
class A
  def test(&block)
    block[:name]
  end
end

options = { name: 'test' }
puts A.new.test(&options) # = > test
```

#### 7
```ruby
0.1 + 0.2 # => 0.30000000000000004
```

#### 8
```ruby
nil.to_a # => []
```

#### 9
```ruby
true + false # => NoMethodError: undefined method '+'
```

#### 10
```ruby
class A
  def self.new
    'test'
  end
end

puts A.new # => test
```

#### 11
```ruby
def test
  'test'
end

puts test # => test
puts self.test # => NoMethodError: private method 'test' called for main:Object
```

#### 12
```ruby
str = 'TEST'

def str.-@
  downcase
end

puts str # => TEST
puts -str # => test
```

#### 13
```ruby
'zzz' == :zzz # => false
```

#### 14
```ruby
val1 = true and false 
val2 = true && false

puts val1 # => true
puts val2 # => false
```

#### 15
```ruby
VALUE = 'Global'

module M
  VALUE = 'Local'

  class A
    def test1
      VALUE
    end
  end
end

class M::A
  def test2
    VALUE
  end
end

puts M::A.new.test1 # => Local
puts M::A.new.test2 # => Global
```

#### 16
```ruby
def test1(*attrs)
  attrs
end

def test2(**attrs)
  attrs
end

test1 # => []
test2 # => {}
```

#### 17
```ruby
a = 1
puts a # => 1
a += 1
puts a # => 2
a =+ 1
puts a # => 1
a =+++ 1
puts a # => 1
a =+ 2
puts a # => 2
```

#### 18
```ruby
def public
  'test'
end

puts public # => Object
```

#### 19
```ruby
puts '10' > '9' # => false
```

#### 20
```ruby
class A
  def test
    super
  end
end

A.new.test # => ArgumentError
```

#### 21
```ruby
puts DATA.to_a # => ['aaa'", 'bbb', 'ccc']
__END__
'aaa'
'bbb'
'ccc'
```

#### 22
```ruby

class A
  @value = 'Instance variable'
  @@value = 'Class variable'

  def initialize
    @value = 'test'
  end

  def test1
    @value
  end

  def test2
    @@value
  end
end

puts A.new.test1 # => test
puts A.new.test2 # => Class variable
```

#### 23
```ruby
def test1
  self
end

class A
  def test2
    test1
  end
end

puts test1 # => main
puts A.new.test2 # => instance of the A class
```

#### 24
```ruby
def test1
  [1, 2]
end

def test2
  puts "before: #{test1} | class: #{test1.class}" # => before: [1, 2] | class: Array
  test1 = test1
  puts "after: #{test1} | class: #{test1.class}" # => after:  | class: NilClass
end

test2
puts test1 # => [1, 2]
```

#### 25
```ruby
def test(a, l)
  puts "a = #{a}"
  l.call if l
  yield if block_given?
end

test(123, ->() { puts 'Lambda' } ) { puts 'Block' }

# => a = 123
# => Lambda
# => Block
```

#### 26
```ruby
def test
  puts 'do something'
  'do something'
rescue
  puts 'rescue'
  'rescue'
else
  puts 'else'
  'else'
ensure
  puts 'ensure'
  'ensure'
end

puts "test = #{test}"

# => do something
# => else
# => ensure
# => test = else
```

#### 27
```ruby
def test
  2 / 0
  puts 'do something'
  'do something'
rescue
  puts 'rescue'
  'rescue'
else
  puts 'else'
  'else'
ensure
  puts 'ensure'
  'ensure'
end

puts "test = #{test}"

# => rescue
# => ensure
# => test = rescue
```
