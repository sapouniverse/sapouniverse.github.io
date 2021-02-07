# type 


```python
a_string="like this"
a_number=3
a_float=3.12
a_boolean=False
a_none=None

print(type(a_string))
print(type(a_number))
print(type(a_float))
print(type(a_boolean))
print(type(a_none))
```

    <class 'str'>
    <class 'int'>
    <class 'float'>
    <class 'bool'>
    <class 'NoneType'>
    

# list = mutable sequence [ ~ ]


```python
days=["Mon", "Tue", 'Wed', 'Thur', 'Fri']

print(type(days))
print("Mon" in days)
print("Man" in days)
```

    <class 'list'>
    True
    False
    


```python
print(len(days))
```

    5
    


```python
days.append("Sat")
print(days)
```

    ['Mon', 'Tue', 'Wed', 'Thur', 'Fri', 'Sat']
    


```python
days.reverse()
print(days)
```

    ['Sat', 'Fri', 'Thur', 'Wed', 'Tue', 'Mon']
    

# tuple = immutable sequence ( ~ )


```python
days2=("Mon", "Tue", 'Wed', 'Thur', 'Fri')
print(type(days2))
```

    <class 'tuple'>
    

# dictionary = list, tuple 까지 묶어서 저장 가능


```python
who = {
    "name": "Suepr",
    "age": 29,
    "korean": True,
    "fav_food": ["Kimchi", "rice"]

}

print(who)
```

    {'name': 'Suepr', 'age': 29, 'korean': True, 'fav_food': ['Kimchi', 'rice']}
    


```python
print(who["name"])
print(who["age"])
print(who["korean"])
print(who["fav_food"])
```

    Suepr
    29
    True
    ['Kimchi', 'rice']
    


```python
who["handsome"]=True
print(who)
```

    {'name': 'Suepr', 'age': 29, 'korean': True, 'fav_food': ['Kimchi', 'rice'], 'handsome': True}
    

# change type


```python
age = "29"
print(age)

i_age=int(age)
print(i_age)
```

    29
    29
    


```python
age = "29"
print(type(age))

i_age=int(age)
print(type(i_age))
```

    <class 'str'>
    <class 'int'>
    

# creating function


```python
def say_hello(who="you"):
    print("hello", who)
    
say_hello("Nicolas")
say_hello()
```

    hello Nicolas
    hello you
    


```python
def plus(a,b):
    print(a+b)
    
plus(25474221,2213243543)
```

    2238717764
    

# return vs print


```python
def say_nick(nick):
    if nick=="바보":
        return
    print("나의 별명은 %s입니다" % nick)
    
    
say_nick("당나귀")
say_nick("바보")
say_nick("기린")
say_nick("바보")
say_nick("말")
```

    나의 별명은 당나귀입니다
    나의 별명은 기린입니다
    나의 별명은 말입니다
    

# arguments


```python
def say_introduce(name, age, are_from, fav_food):
  return f"Hello {name}! you are {age}, you are form {are_from}, you like {fav_food}"
  
hello=say_introduce("nicolas", "29", "kimchi", "colombia")

print(hello)
```

    Hello nicolas! you are 29, you are form kimchi, you like colombia
    


```python
def say_introduce(name, age, are_from, fav_food):
  return f"Hello {name}! you are {age}, you are form {are_from}, you like {fav_food}"
  
hello=say_introduce(name="nicolas", age="29", fav_food="kimchi", are_from="colombia")

print(hello)
```

    Hello nicolas! you are 29, you are form colombia, you like kimchi
    

# if else calculator


```python
def e_plus(a,b):
    if type(a) is str:
        return None
    elif type(b) is str:
        return None
    else:
        return a + b
    
x=e_plus(10,213)
y=e_plus("11230",212313)
z=e_plus(1123410,"123213")
u=e_plus("112351250","2123412313")
v=e_plus(100,300)

print(x,y,z,u,v)
```

    223 None None None 400
    


```python
def g_plus(a,b):
    if type(a) is float or type(b) is float:
        return a + b
    else:
        return None
    
ga=g_plus(10,2.3)
na=g_plus("11230",212313)
da=g_plus(1,"10.1")
ra=g_plus(1,10.1)
ma=g_plus("112351250","2123412313")
ba=g_plus(100,300)

print(ga,na,da,ra,ma,ba)
```

    12.3 None None 11.1 None None
    

# if else age_check


```python
def age_check(age):
    print(f"you are {age}")
    
    if age<18:
        print("you cannot drink")
    elif age==18 or age==19:
        print("you are new to this")
        
    elif age>=20 and age<25:
        print("Just Do It")
    else:
        print("enjoy your drink")

age_check(15)
age_check(18)
age_check(20)
age_check(26)
```

    you are 15
    you cannot drink
    you are 18
    you are new to this
    you are 20
    Just Do It
    you are 26
    enjoy your drink
    

# import


```python
import math

print(math.ceil(1.2)) #올림
print(math.fabs(-1.2)) #절대값
```

    2
    1.2
    
