
# [자료구조] 01. 큐 (Queue) - python

## 1. 정의

줄을 서는 거와 같이 가장 먼저 넣은 데이터를 가장 먼저 꺼낼 수 있는 구조이다.<br>
즉 **FIFO(First in First out), LILO(Last in Last out)**구조를 가지고있다.<br>
* Enqueue : 큐에 데이터를 넣는 기능 후단(rear)에서 이루어짐<br>
* Dequeue : 큐에서 데이터를 꺼내는 기능 전단(front)에서 이루어짐

## 2. 특징

* 멀티 태스킹을 위한 프로세스 스케쥴링 방식을 구현하기 위해 많이 사용됨<br>
* 데이터가 입력된 시간 순서대로 처리할때 유리하다

## 3. 종류

1.Queue(FIFO)<br>
* FIFO(First in First out), LILO(Last in Last out)구조의 일반적인 큐<br>

2.Priority Queue<br>
* index값을 데이터마다 지정하여 순서를 정하는 형태<br>

3.Circular Queue<br>
* 직선 큐에서 데이터를 제거 할때 추가적인 연산이 생기는 단점을 극복하기 위한 원 형태의 큐<br>

4.Linked Queue<br>
* 링크드 리스트와 비슷 한 형태로 노드에 후단(rear)방향의 주소값이 있고 전단(front)에서 Dequeue, 후단(rear)에서 Enqueue가 일어난다.<br>

## 4. 코드 구현

### 간단하게 라이브러리로 구현하기

* Queue


```python
import queue

queue_code = queue.Queue()
# Enqueue
queue_code.put("data_1")
queue_code.put("data_2")
queue_code.put("data_3")
queue_code.put("data_4")
queue_code.put("data_5")
queue_code.qsize()
```




    5




```python
# Dequeue
for _ in range(queue_code.qsize()):
    print(queue_code.get())
```

    data_1
    data_2
    data_3
    data_4
    data_5
    

* PriorityQueue


```python
# PriorityQueue
priority_queue = queue.PriorityQueue()
# Enqueue
priority_queue.put((5, "data_1"))
priority_queue.put((3, "data_2"))
priority_queue.put((11, "data_3"))
priority_queue.put((8, "data_4"))
priority_queue.put((1, "data_5"))
priority_queue.qsize()
```




    5




```python
# Dequeue
for _ in range(priority_queue.qsize()):
    print(priority_queue.get())
```

    (1, 'data_5')
    (3, 'data_2')
    (5, 'data_1')
    (8, 'data_4')
    (11, 'data_3')
    

### 라이브러리 안쓰고 구현하기(list 사용하여)

* queue_htm class 구현


```python
class queue_htm:
    def __init__(self):
        self.queue = list()
    
    def Enqueue(self, data):
        self.queue.append(data)
        return self.queue
    
    def Dequeue(self):
        try:
            temp = self.queue[0]
            del self.queue[0]
            return temp
        except:
            return self.queue
    
    def qsize(self):
        return len(self.queue)
```

* test


```python
HTM = queue_htm()
# Enqueue
HTM.Enqueue(1)
HTM.Enqueue(2)
HTM.Enqueue(3)
HTM.Enqueue(4)
HTM.Enqueue(5)
```




    [1, 2, 3, 4, 5]




```python
# qsize
print('==>> qsize : ',HTM.qsize())
# Dequeue
for _ in range(HTM.qsize()):
    print('==>> Dequeue : ',HTM.Dequeue())
    print('==>> qsize : ',HTM.qsize())
```

    ==>> qsize :  5
    ==>> Dequeue :  1
    ==>> qsize :  4
    ==>> Dequeue :  2
    ==>> qsize :  3
    ==>> Dequeue :  3
    ==>> qsize :  2
    ==>> Dequeue :  4
    ==>> qsize :  1
    ==>> Dequeue :  5
    ==>> qsize :  0
    
