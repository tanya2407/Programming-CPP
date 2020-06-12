<h4>Some notes on programming questions solved using c++</h4>

<h5> String: </h5> 
Intialize: string s = "" </br>
length: s.length() </br>

## Hashmap in C++
#### unordered_map:
1. Stores elements as a combination of key value pair. 
2. Library: ``` #include<unordered_map>``` OR ```#include<bits/stdc++.h>``` 
3. Initialization example: ```unordered_map<string,int> map```
4. Internally implemented using Hash table. Therefore avgcost of search,insert,delete is O(1).
5. Inserting Values: ```map["Tanya"] = 1;``` 
6. Traversing: ```
                  for(auto i: map)
                  {
                      cout<<i.first()<<i.second(); 
                  } 
                  ```
                
<h5>unordered_set:</h5> Stores only keys </br>
                  Mainly used is keep track of absence/presence elements.</br>
                  
<h5>set:</h5> ordered sequence of unique keys
<h5>map:</h5> ordered sequence of unique keys and corresponding values</br>
              It is implemented as balanced tree structure that is why it is possible to maintain an order between the elements (by specific tree traversal).</br>
              Time complexity of map operations is O(Log n) while for unordered_map, it is O(1) on average.
                  

