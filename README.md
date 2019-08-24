# ruby-cases
Ruby cases

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

puts A.new.test('aaa')
puts B.new.test('bbb')
puts C.new.test('ccc')
```

***

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

A.new.test
```
