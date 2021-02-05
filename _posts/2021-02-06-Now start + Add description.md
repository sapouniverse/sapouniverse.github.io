# for는 반복


```python
for i in range(5):
  print("HaHa")
```

    HaHa
    HaHa
    HaHa
    HaHa
    HaHa
    

# if는 내맘대로


```python
for i in range(10):
  if(i%2==0):
    print("넌 짝수")
  elif(i==3):
    print("당첨")
  else:
    print("다음 기회에")
```

    넌 짝수
    다음 기회에
    넌 짝수
    당첨
    넌 짝수
    다음 기회에
    넌 짝수
    다음 기회에
    넌 짝수
    다음 기회에
    

# def 하고 불러오기


```python
def multiple_7(x):
  return x*7

for i in range(10):
  print(multiple_7(i))
```

    0
    7
    14
    21
    28
    35
    42
    49
    56
    63
    

# 문자 더하기, 숫자 더하기


```python
a=7 # 숫자 타입
b="7" # 문자 타입

print(str(a)+b)
print(a+int(b))
```

    77
    14
    
