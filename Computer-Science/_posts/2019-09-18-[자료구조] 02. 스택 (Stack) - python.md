
# [자료구조] 02. 스택 (Stack) - python

## 1. 정의

가장 나중에 쌓은 데이터를 가장 먼저 꺼낼 수 있는 구조를 가지고 있다.<br>
즉 **LIFO(Last in First out), FILO(First in Last out)**구조를 가지고있다.<br>
* push : 데이터를 스택에 넣는다.<br>
* pop : 데이터를 스택에서 꺼낸다.

## 2. 특징

* 컴퓨터 내부의 프로세스 구조의 함수 동작 방식에 쓰임.<br>
* 데이터를 제한적으로 접근할 수 있는 구조이다.(한쪽 끝에서만 자료를 넣거나 뺄 수 있다.)
* 단순하고 빠른 성능을 위해 사용됨.

**장점**
  - 구조가 단순해서, 구현이 쉽다.
  - 데이터 저장/읽기 속도가 빠르다.<br>
  
**단점** 
  - 데이터 최대 갯수를 미리 정해야 한다.
  - 저장 공간의 낭비가 발생할 수 있다.

## 3. 코드 구현

### list 사용하여 구현하기

* stack_htm class 구현


```python
class stack_htm:
    def __init__(self):
        self.stack = list()
    
    def push(self, data):
        self.stack.append(data)
        return self.stack
    
    def pop(self):
        try:
            temp = self.stack[-1]
            del self.stack[-1]
            return temp
        except:
            return self.stack
    
    def ssize(self):
        return len(self.stack)
```

* test


```python
HTM = stack_htm()
# push
HTM.push(1)
HTM.push(2)
HTM.push(3)
HTM.push(4)
HTM.push(5)
```




    [1, 2, 3, 4, 5]




```python
# ssize
print('==>> qsize : ',HTM.ssize())
# pop
for _ in range(HTM.ssize()):
    print('==>> Dequeue : ',HTM.pop())
    print('==>> qsize : ',HTM.ssize())
```

    ==>> qsize :  5
    ==>> Dequeue :  5
    ==>> qsize :  4
    ==>> Dequeue :  4
    ==>> qsize :  3
    ==>> Dequeue :  3
    ==>> qsize :  2
    ==>> Dequeue :  2
    ==>> qsize :  1
    ==>> Dequeue :  1
    ==>> qsize :  0
    
