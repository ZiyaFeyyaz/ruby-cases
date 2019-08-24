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
    puts 'test'
  end
end

class A
  include M
end

A.new.test # => NoMethodError
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
