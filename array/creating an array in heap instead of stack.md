When we declare an array, the usual way, Int Arr[size]; this memory allocation happens in stack. Stack has a limited memory which may not support much higher sizes. 
  
  Therefore, we use Pointer to allocate memory in heap. Its syntax is as follows:  

         int * pointer = new int[SIZE];
      
 NOTE: Memory allocated in stack gets automatically unallocated when the program ends, but when memory is allocated in heap, it must be unallocated using the delete function as follows:  

        delete [] pointer;



