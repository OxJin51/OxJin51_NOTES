---

title: stl小合集
date: 2024-10-17 22:00:00 +0800
categories: [Algorithm, Stl]
tags: [algorithm,stl]
---

# 一、遍历 

**begin()就是指向容器第一个元素的迭代器**

**end()是指向容器最后一个元素的下一个位置的迭代器**

## 1. iterator 遍历stl

- **string 中 string::iterator it ;**
- **vector 中 (vector<int>::iterator it**

```
for (vector<int>::iterator it = vtr.begin(); it != vtr.end(); it++) // 容器名称为vtr
	{
		cout << *it << " ";
	}
```

## 2. for(x:y) 遍历

```
for(auto x : arr) //输出arr中所有元素
{
   cout << x << ' ';
}
```



# 二、库函数

## reverse函数（左闭右开）

### **1. 反转vector **

- **reverse(vec.begin(), vec.end());**

### **2. 反转string**

- **reverse(str.begin(), str.end()); **

### 3. reverse_copy 函数

 **reverse_copy(first.begin(), first.end(), second.begin());** 把first倒置后复制到second

```
    string first, second;
    first = "xxxxx";
    second.resize(first.size());
    reverse_copy(first.begin(), first.end(), second.begin());`

```

## sort函数

### 头文件：algorithm

### 使用方法：sort(容器.begin, 容器.end, cmp)

### 自定义排序准则：bool cmp() {...}

默认为升序排序

```
bool  cmp(string a,string b)
{
        return a+b>b+a;
}
```

重载运算符（待补充）

# 三、修改值

### 删除指定位置的值

- **stl.erase(position)**
- 例：isbn.erase(isbn.end() - 1); 删除ISBN最后一个元素 

# 四、优先队列

\#include<queue>

声明格式：**priority_queue<结构类型> 队列名;**

![image-20241028234052964](./../assets/images/2024-10-17-Stl/image-20241028234052964.png)

![image-20241028234148761](./../assets/images/2024-10-17-Stl/image-20241028234148761.png)

- q.size();//返回q里元素个数
- q.empty();//返回q是否为空，空则返回1，否则返回0
- q.push(k);//在q的末尾插入k
- q.pop();//删掉q的第一个元素**（要保证q不为空 if（p.size()））**
- q.top();//返回q的第一个元素



**默认为大根堆（堆顶最大，左大右小）**



# 五、Map

内部红黑树R&B

存储键值对 **<key,value>**

- key 关键字**(有序)**

- value 关键值字的值

  *pair<const T1,T2>*

  ## 1. 修改 O(log n)

  insert

  [ ] 运算符

  ![image-20241029000755274](./../assets/images/2024-10-17-Stl/image-20241029000755274.png)

  count(key); 返回个数（0/1）

  find(key); 返回key所对应的迭代器(空返回.end()  )

  # 六、Set
  
  基于红黑树





Vector复制

法1：直接赋值

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v1 = {2, 4, 1, 5, 3};

    // Assigning the vector v1 to vector v2
    vector<int> v2 = v1;

    for (auto i : v2)
        cout << i << " ";
    return 0;
}


```

法2：assign()函数

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v1 = {2, 4, 1, 5, 3};
    vector<int> v2;

    // Copying the vector v1 into vector v
    v2.assign(v1.begin(), v1.end());
    
    for (auto i : v2)
        cout << i << " ";
    return 0;

}
```



## Using Vector insert()

The [***\*vector insert()\**** ](https://www.geeksforgeeks.org/cpp/vector-insert-function-in-cpp-stl/)method provides a version that can copy all the elements from the given range. This can be used to copy the entire vector to another in a similar way as assign() method.

```cpp

#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v1 = {2, 4, 1, 5, 3};
    vector<int> v2;

    // Copying vector v1 into vector v2
    v2.insert(v2.begin(), v1.begin(), v1.end());

    for (auto i : v2)
        cout << i << " ";
    return 0;
}
```

**Output**

```
2 4 1 5 3 
```

获取vector中的最大/最小值

## Using std::minmax_element()

The [std::minmax_element()](https://www.geeksforgeeks.org/cpp/stdminmax-stdminmax_element-c-stl/) function can be used to find the maximum and the minimum element in the array at once. It takes the iterator to the beginning and the end of the vector and returns a pair in which first member is minimum, and second member is maximum.

### Syntax

> ***\*std::minmax_element\****(v.begin(), v.end());

where, ****\*v\***** is the vector.

### Example





```cpp

// C++ Program to find the minimum element in a vector
// using std::minmax_element()
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {2, 4, 1, 5, 3};

    // Finding both minimum and maximum elements
    auto p = minmax_element(v.begin(), v.end());

    cout << *p.first;
    return 0;
}
```

**Output**

```
1
```

***\*Time Complexity:\**** O(n), where ***\*n\**** is the number of elements in the vector.
***\*Auxiliary Space:\**** O(1)

## Using std::accumulate()

Generally, the [***\*std::accumulate()\****](https://www.geeksforgeeks.org/cpp/accumulate-and-partial_sum-in-c-stl-numeric-header/) method is used to find the sum of all elements in the given range. But we can also find the minimum element in the vector by custom comparison function.

### Syntax

> ***\*std::accumulate\****(v.begin(), v.end(), i, comp);

where, ****\*v\***** is the vector, ****\*i\***** is the initial value, and ****\*comp\***** is the comparator.

### Example





```cpp

// C++ program to find the minimum element
// in std::vector using std::accumulate()
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {2, 4, 1, 5, 3};

    // Finding the minimum element in vector
    // using std::accumulate() along with
    // custom comparison
    int min = accumulate(v.begin(), v.end(),
                         v[0], [](int a, int b) { 
                           return std::min(a, b);
                         });

    cout << min << endl;
    return 0;
}
```

**Output**

```
1
```

***\*Time Complexity:\**** O(n), where ***\*n\**** is the number of elements in the vector.
***\*Auxiliary Space:\**** O(1)



Given a vector, find the maximum element of the vector using STL in C++.

***\*Example\****

> ***\*Input:\**** v = {2, 4, 1, 5, 3}
> ***\*Output:\**** 5
> ***\*Explanation:\**** 5 is the largest element of vector.
>
> ***\*Input:\**** v = {11, 23, 3, 5, 24}
> ***\*Output:\**** 24
> ***\*Explanation:\**** 24 is the largest element of the given range.

STL provides the following different methods to find the maximum element in the vector in C++.

Table of Content

- [Using std::max_element()](https://www.geeksforgeeks.org/cpp/how-to-find-the-maximum-element-of-a-vector-using-stl-in-c/#using-max_element)
- [Using std::minmax_element()](https://www.geeksforgeeks.org/cpp/how-to-find-the-maximum-element-of-a-vector-using-stl-in-c/#using-stdminmax_element)
- [Using Priority Queue](https://www.geeksforgeeks.org/cpp/how-to-find-the-maximum-element-of-a-vector-using-stl-in-c/#using-stdaccumulate)
- [Using std::sort()](https://www.geeksforgeeks.org/cpp/how-to-find-the-maximum-element-of-a-vector-using-stl-in-c/#by-sorting-in-ascending-order)

## Using std::max_element()

The simplest way to find the maximum element in the vector is by using the [***\*std::max_element()\****](https://www.geeksforgeeks.org/cpp/max_element-in-cpp/). This function returns the iterator to the maximum element in the given range of elements.

### Syntax

> ***\*std::max_element\****(v.begin(), v.end());

where, ****\*v\***** is the vector.

### Example





```cpp

// C++ program to find maximum element
// in vector using std::max_element()
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {2, 4, 1, 5, 3};

    // Finding the maximum element in vector
    // using std::max_element()
    cout << *max_element(v.begin(), v.end());
    return 0;
}
```

**Output**

```
5
```

***\*Time Complexity:\**** O(n), where ***\*n\**** is the number of elements in the vector.
***\*Auxiliary Space:\**** O(1)

## Using std::minmax_element()

The [***\*std::minmax_element()\****](https://www.geeksforgeeks.org/cpp/stdminmax-stdminmax_element-c-stl/) function can be used to find the maximum and the minimum element in the STL container at once. It returns a pair in which pair::first is minimum, and pair::second is maximum.

### Syntax

> ***\*std::minmax_element\****(v.begin(), v.end());

where, ****\*v\***** is the vector.

### Example

```cpp

// C++ Program to find maximum element in vector
// using std::minmax_element()
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {2, 4, 1, 5, 3};

    // Finding both minimum and maximum elements
    auto p = minmax_element(v.begin(), v.end());

    // Printing the maximum element
    cout << *p.second;
    return 0;
}
```

**Output**

```
5
```

***\*Time Complexity:\**** O(n), where ***\*n\**** is the number of elements in the vector.
***\*Auxiliary Space:\**** O(1)
