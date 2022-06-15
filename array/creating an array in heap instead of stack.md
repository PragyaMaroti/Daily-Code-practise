
When we declare an array, the usual way, Int Arr[size]; this memory allocation happens in stack. Stack has a limited memory which may not support much higher sizes. 
  
  Therefore, we use Pointer to allocate memory in heap. Its syntax is as follows:  

         int * pointer = new int[SIZE];
      
 NOTE: Memory allocated in stack gets automatically unallocated when the program ends, but when memory is allocated in heap, it must be unallocated using the delete function as follows:  

        delete [] pointer;
        
        
--------

Use of MALLOC function is also for allocating memory from heap.


### Differences between malloc and new:  

| new                                     | malloc()                          | 
| ----------------------------------------|---------------------------------  | 
| calls constructor                       |	does not calls constructors       |       
| It is an operator                       |	It is a function                  |
| Returns exact data type	                | Returns void *                    |
| on failure, Throws bad_alloc exception  |  	On failure, returns NULL        |
| size is calculated by compiler	        | size is calculated manually       |
| memory is allocated from free store     |memory allocation is done from heap|
|   Doesn't allow changing of buffer size |change size of buffer with realloc() |



