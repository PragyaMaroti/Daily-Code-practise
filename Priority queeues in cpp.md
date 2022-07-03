[Reference](https://www.geeksforgeeks.org/implement-min-heap-using-stl/)   


- Priority queues are a type of container adapters.  
- Priority queues are built on the top to the max heap and uses **array or vector as an internal structure**.   
- By default, C++ creates a max-heap for priority queue.   
- We can pass another parameter while creating the priority queue to make it a min heap. C++ provides the below syntax for the same:   

```
priority_queue <int, vector<int>, greater<int>> g = gq;  
```

❗The above syntax may be difficult to remember, so in case of numeric values, we can multiply the values with -1 and use max heap to get the effect of min heap. 🤭   


|Method| Definition|
|-------|-----------------|
|priority_queue::empty()|	Returns whether the queue is empty.|
|-------|-----------------|
|priority_queue::size() |	Returns the size of the queue. |
|-------|-----------------|
|priority_queue::top()	| Returns a reference to the topmost element of the queue.|
|-------|-----------------|
|priority_queue::push() |	Adds the element ‘g’ at the end of the queue.|
|-------|-----------------|
|priority_queue::pop()	|Deletes the first element of the queue.|
|-------|-----------------|
|priority_queue::swap()	|Used to swap the contents of two queues provided the queues must be of the same type, although sizes may differ.|
|-------|-----------------|
|priority_queue::emplace()|	Used to insert a new element into the priority queue container.|
|-------|-----------------|
|priority_queue value_type |	Represents the type of object stored as an element in a priority_queue. It acts as a synonym for the template parameter.|   
|-------|-----------------|
