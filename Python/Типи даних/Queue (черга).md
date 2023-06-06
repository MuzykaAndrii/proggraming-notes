`collections.deque` - черга з двостороннім доступом, яка підтримує додавання та видалення елементів з будь-якого кінця за O(1). 

`queue.Queue` - синхронізована черга яка забезпечує семантику блокування з метою підтримки численних паралельних виробників та споживачів.

`multiprocessing.Queue` - черга, яка дозволяє виконувати паралельну обробку елементів, що знаходяться в черзі, численними паралельними робочими процесами.

## Черга з пріоритетом
`heapq` - двійкові купи на основі **списку**, підтримує вставку та вилучення найменшого елемента за **O(log n)** часу:
```python
import heapq

queue = []
heapq.heappush(queue, (2, 'develop'))
heapq.heappush(queue, (1, 'eat' ))
heapq.heappush(queue, (3, 'sleep'))

while queue:
	next_item = heapq.heappop(queue)
	print(next_item)

# >> (1, eat)
# >> (2, develop)
# >> (3, sleep)
```

`queue.PriorityQueue` - обгортка на основі `heapq`, синхронізована та забезпечує семантику блокування з метою підтримки численних паралельних виробників та споживачів.
```python
from queue import PriorityQueue

my_queue = PriorityQueue()

my_queue.put((2, 'develop'))
my_queue.put ((1, 'eat'))
my_queue.put((3, 'sleep'))

while not my_queue.empty:
	next_item = my_queue.get()
	print(next_item)

# >> (1, 'eat')
# >> (2, 'develop')
# >> (3, 'sleep')
```

[[Sequence (послідовність)]]