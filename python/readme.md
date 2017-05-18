# Python cheatsheet

## Basic syntax
```python
a = 1 # this is integer declaration
b = float(10) # this is float declaration
b = 10.0 # this is float declaration

# list
a = [1,2,3] # list declaration
b = [4,5,6]
a+b # list concatentation

a = (1,2,3) # tuple declaration, tuple is immutable
for i in a:
  print(i)


# dict
dict1 = {}
dict1['key1'] = 'value1'
dict1['key2'] = 'value2'
dict2 = {
  'key1': 'value1',
  'key2': 'value2'
}
print(dict1 == dict2) # True will be printed
for key,value in dict1.items():
  print('%s: %s' % (key,value))
print('key1' in dict1) # True
print('key1' not in dict1) # False


# set
set([1,2,3,1,2,3]) # set is unique list
a = set([1,2,3])
b = set([3,4])
a.difference(b) # a XOR b, and get elements in a => {1,2}, so it actually is (a XOR b) AND a
a.symmetric_difference(b) # Simply a XOR b => {1,2,4}
a.union(b) # Simply a OR b => {1,2,3,4}
a.intersection(b) # a AND b => {3}



# str
h = "hello" # string
w = 'world' # string
h+w # string concatentation


if (h == 'hello'):
  print('if')
elif (h == 'world'):
  print('elif')
else:
  print('else')


```

## Functions
```python

def fib(cnt):
  a,b = 0,1
  for i in range(cnt):
    a,b = b, (a+b)
    yield a

cnt = 10
for i in fib(cnt):
  print(i)

def sumAll(*nums): #nums is a tuple (readonly list)
  result=0
  for i in nums:
    result += i
  return result

def dictArgs(**dict): # dict is a dictionary
  for k,v in dict.items():
    yield (k,v)

for t in dictArgs(k1=1,k2=2,k3=3):
  print('%s=%s' % t) # print k1=1 k2=2 k3=3


```

## Calling Functions
Type to do the same thing as `apply` in JavaScript.
```python
def sum(*args):
    result = 0
    for arg in args:
        result += arg
    return result

print(sum(1,2,3)) # print 6
a=[]
a.append(1)
a.append(2)
a.append(3)
print(sum(*a)) # same as sum(1,2,3), so 6 is printed
```

## Classes and Objects
```python
class Vehicle:
  color = 'red'
  name = ''
  def show(self):
    print('Vehicle %s is %s color' % (self.name, self.color))

car1 = Vehicle()
car1.name = 'Bus'
car1.show()

```

## Modules


## Numpy Array


## Panda DataFrame

## List Comprehensive
```python
a = [1,2,3,4,5,6]
evensquare = [i**2 for i in a if i % 2 == 0]
print(evensquare) # print [4, 16 36]
```


## Partial Functions
```python
from functools import partial
def func(u,v,w,x):
    return u*4 + v*3 + w*2 + x

func2 = partial(func,5,6,10)
print(func2(2)) # effectively, same as func(5,6,10,2)
```

## Declorators
This is `AOP`  (Aspect-Oriented Programming)??
```python
# Here is the idea
@myDeclorator
def myFunc()
  pass

# same as
myFunc = myDeclorator(myFunc)
```

```python
def change(val):
    def multipler(old_func):
        def new_func(*args):
            new_args = [i*val for i in args]
            return old_func(*new_args)
        return new_func
    return multipler

@change(3)
def sum(*args):
    result = 0
    for arg in args:
        result += arg
    return result


print(sum(1,2,3)) # 18
```
