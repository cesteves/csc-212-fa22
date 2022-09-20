# Code Samples Used in Class

## Static Arrays

---

### Memory Allocation: Stack <br> Declaring an array and insert values by index

```cpp
#include<iostream>
using namespace std;

// Memory Allocation: Stack
// Declaring an array and insert values by index

int main () {

  // declare array
  int values [4];

  // append values to array
  values[0] = 2;
  values[1] = 4;
  values[2] = 6;
  values[3] = 8;

  // output array values by index
  cout << "\n" << endl;

  cout << values[0] << endl;
  cout << values[1] << endl;
  cout << values[2] << endl;
  cout << values[3] << endl;

  cout << "\n" << endl;
  
  return 0;

}
```

### Memory Allocation: Stack <br> Initializing an array

```cpp
#include<iostream>
using namespace std;

// Memory Allocation: Stack
// Initializing an array

// 1) run code once as is
// 2) insert any number into the static_arr array
// 3) run code again...
//    what was the result? and why did it happen?

int main () {

  // declare and initialize static array
  int static_arr [4] = { 2, 4, 6, 8, 10 };

  // output array values by index
  cout << "\n" << endl;

  cout << static_arr[0] << endl;
  cout << static_arr[1] << endl;
  cout << static_arr[2] << endl;
  cout << static_arr[3] << endl;

  cout << "\n" << endl;
  
  return 0;
}
```

### Memory Allocation: Stack <br> Resizing arrays

```cpp
#include<iostream>
using namespace std;

// Memory Allocation: Stack
// Resizing arrays

int main () {
  
  // original array
  int src [] = { 2, 4, 6, 8 };

  // move src to array with updated size
  int dest [10];

  // copy all values from 
  copy(src, src+10, dest);

  // size of source
  // - sizeof() assumes 4 bytes per element
  //   hence we need to divide by reference to get length      
  int s_size = sizeof(src) / sizeof(*src);
  int d_size = sizeof(dest) / sizeof(*dest);

  cout << "\n" << endl;
  // view array sizes
  cout << "size of arrays, respectively: \nsrc / dest\n" << s_size << " / " << d_size << endl;
  cout << "\n" << endl;

  // Add in value to index 4 of the dest array
  dest[4] = 10;

  // print all values dest array
  for(int i = 0; i < d_size; i++){
    cout << dest[i] << endl;
  }
  cout << "\n" << endl;
  return 0;
}


```

### Memory Allocation: Heap

```cpp
#include<iostream>
using namespace std;

// Memory Allocation: Heap

int main () {

  // declare array
  // - values as pointer
  int *static_arr_heap = new int[4];

  // append values
  static_arr_heap[0] = 2;
  static_arr_heap[1] = 4;
  static_arr_heap[2] = 6;
  static_arr_heap[3] = 8;

  cout << "\n" << endl;

  // using the new keyword requires deallocation of memory
  delete[] static_arr_heap;

  // print all static_arr_heap array values by index
  for(int i = 0; i < 4; i++){
    cout << static_arr_heap[i] << endl;
  }
  cout << "\n" << endl;
  
  return 0;
}


```

## Dynamic Arrays

### Creating a dynamic array <br> vectors

```cpp
#include<iostream>
#include<vector>
using namespace std;

// Creating a dynamic array
//  - vectors

int main () {
  
  // declare a vector
  vector<int> dynamic_arr;

  // add values to the vector
  dynamic_arr.push_back(2);
  dynamic_arr.push_back(4);
  dynamic_arr.push_back(6);
  dynamic_arr.push_back(8);
  
  // output the location | index: value
  cout << "\n" << endl;

  for(int i = 0; i < dynamic_arr.size(); i++) {
    cout << i << ": " << dynamic_arr[i] << endl;
  }

  cout << "\n" << endl;

  return 0;
}
```

### Working with vectors <br> vector methods

```cpp
#include<iostream>
#include<vector>
using namespace std;

// Working with vectors
//  - vector methods
//    - .push_back()    <=> append to end
//    - .clear()        <=> clear all values from vector
//    - .erase()        <=> remove an individual value
//    - .size()         <=> get length of vector
//    - .at()           <=> get value at specific element

int main () {
  
  // declare a vector
  vector<int> dynamic_arr;
  dynamic_arr.push_back(44);

  // output the location | index: value
  // - pre-validation
  cout << "\nPre" << endl;
  for(int i = 0; i < dynamic_arr.size(); i++) {
    cout << i << ": " << dynamic_arr.at(i) << endl;
  }

  // validate array contents | test for values
  // - if array has elements with values, clear all values
  if (dynamic_arr.empty() == false) {
    dynamic_arr.clear();
  }

  dynamic_arr.push_back(2);
  dynamic_arr.push_back(4);

  // output the location | index: value
  // - post-validation
  cout << "\nPost" << endl;
  for(int i = 0; i < dynamic_arr.size(); i++) {
    cout << i << ": " << dynamic_arr.at(i) << endl;
  }

  cout << "\n" << endl;
  return 0;
}
```

### Working with vectors <br> vector methods: `.insert()`

```cpp
#include<iostream>
#include<vector>
using namespace std;

// Working with vectors
//  - vector methods
//    - .insert()    <=> adds value to location and adjusts pointers accordingly to fit new data

int main () {
  
  // declare a vector
  vector<int> dynamic_arr;

  // add values to the array
  dynamic_arr.push_back(2);
  dynamic_arr.push_back(4);
  dynamic_arr.push_back(6);
  
  cout << "\n" << endl;
  
  // output iterating through array
  for(vector<int>::iterator iter = dynamic_arr.begin(); iter != dynamic_arr.end(); iter++ ) {
    if (*iter == 4) {
      // use the `+ 1` to insert after the current element
      // or, remove `+ 1` to insert before the current element 
      dynamic_arr.insert(iter, 7);
      break;
    }
  }

  for (int i = 0; i < dynamic_arr.size(); i++) {
    cout << dynamic_arr[i] << endl;
  }

  cout << "\n" << endl;
  return 0;
}
```

### Remove last element from vector <br> vector method: `.pop-back()`

```cpp
#include<iostream>
#include<vector>
using namespace std;

// Remove last element from vector
// - vector methods:
//    - .pop_back()       <=> removes the last element 

int main () {
  
  // declare a vector
  vector<int> dynamic_arr;

  // add values to the array
  dynamic_arr.push_back(2);
  dynamic_arr.push_back(4);
  dynamic_arr.push_back(6);

  // remove last value from vector
  dynamic_arr.pop_back();
  
  cout << "\n" << endl;

  for (int i = 0; i < dynamic_arr.size(); i++) {
    cout << dynamic_arr[i] << endl;
  }
  cout << dynamic_arr.size() << endl;

  cout << "\n" << endl;
  return 0;
}
```

### Manually resize a vector <br> vector method: `.resize()`

```cpp
#include<iostream>
#include<vector>
using namespace std;

// Manually resize a vector
// - vector methods
//  - resize()          <=> adjusts size manually based on user input / hard-coding

int main () {
  
  // declare a vector
  vector<int> dynamic_arr;

  // add values to the array
  dynamic_arr.push_back(2);
  dynamic_arr.push_back(4);
  dynamic_arr.push_back(6);

  // Resize vector
  // dynamic_arr.resize(10);

  // remove last value from vector
  dynamic_arr[5] = 10;
  
  cout << "\n" << endl;

  for (int i = 0; i < dynamic_arr.size(); i++) {
    cout << dynamic_arr[i] << endl;
  }

  cout << "\n" << endl;
  return 0;
}
```
