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
