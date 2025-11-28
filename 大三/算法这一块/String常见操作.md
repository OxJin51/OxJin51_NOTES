---
title: 字符串处理
date: 2024-10-18 21:17:00 +0800
categories: [Algorithm,Sting]
tags: [algorithm,string]
---

# 一、字符串输入

- [x] 小时候看完这集吓哭了

cin会过滤**空格、回车、换行符**

解决方法：

## getline(cin, str);

str为输入的字符串名

# 二、常见操作

## 1. 转换 int

### **str[i]-'0' ;**（适用单个字符）

### stoi(串名,起始点,进制);

```
stoi (date1,0); //进制不写默认为10进制
```

### to_string(数字);

```
to_string(123); 
```



## 2. 大小写转换

### 法1：str[i]+32(大写转小写)

### 法2：transform

#### transform(str.begin(),str.end(),str.begin(),::tolower);

头文件algorithm

- transform( str.begin() , str.end() , str.begin() , ::toupper );//化为大写
- transform( str.begin() , str.end() , str.begin() , ::tolower );//化为小写

transform(处理对象容器**起始**地址，处理对象容器**结束**地址，**存放结果**的容器地址，**处理操作（可自定义）**）



## 3. 查找

### str1.find(str2);

头文件 string

string中find()返回值是字母在母串中的**下标位置**。
如果没有找到，那么会返回一个特别的标记npos，一般写作`string::npos` 或者-1（int）

`常用判断 ： (index != string::npos)`

### str1.find（str2，pos）;

find(str2,pos)是用来寻找从pos开始(包括pos处字符)匹配str的位置。

```cpp
if(to_string(i).find('2')!=string::npos) //用'2'而不是2
```

首先，`string` 的 `find` 函数需要找的是字符，而不是数字。

- ❌ `find(2)` 会去找 ASCII 码为 2 的不可见字符。
- ✅ `find('2')` 才是找字符 '2'。
