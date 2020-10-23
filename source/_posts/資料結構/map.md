---
title: Map
date: 2020-09-27 14:44:01
tags:
 - 程式語言
 - C Language
 - 排序
---
## 一、Map 簡介
Map 是 C++ 標準程式庫中的一個 class，為眾多容器（container）之一。它提供搜尋和插入友善的資料結構，並具有一對一 mapping 功能：

<!-- more -->

- 第一個稱為關鍵字 (key)，每個關鍵字只能在 map 中出現一次。
- 第二個稱為該關鍵字的值 (value)。

Map 的 key-value 對應主要用於資料一對一映射 (one-to-one) 的情況，比如一個班級中，每個學生的學號跟他的姓名就存在著一對一映射的關係。

### Map 的特色
* map 內部資料結構為一顆紅黑樹 (red-black tree)，因此：
    * 內部是有排序的資料。
    * 對於搜尋和插入操作友善( O(logn) )。
* 可以修改 value 值、不能修改 key 值。
* 以模板（泛型）方式實現，可以儲存任意類型的變數，包括使用者自定義的資料型態。

> [用心去感覺] 類似 map 的 STL 結構
>- map : 紅黑樹 (查询、插入、删除都是O(logn) )
>- unordered_map : hash 結構，C++11 標準函式庫。
>- unordered_set : hash 結構，但 value 本身即是 key。
>- hash_map : hash 結構，非標準函式庫。


## 二、成員函式簡介與常用程式寫法
### 1. 宣告
```cpp
map<string, string> mapStudent;
```

### 2. 插入 insert()
```cpp
// 用 insert 函數插入 pair
    mapStudent.insert(pair<string, string>("r000", "student_zero"));

//用 "array" 方式插入
    mapStudent["r123"] = "student_first";
    mapStudent["r456"] = "student_second";
```
### 3. 尋找 find()
出現時，它返回資料所在位置，如果沒有，返回 iter 與 end() 函數的返回值相同。
```cpp
iter = mapStudent.find("r123");

if(iter != mapStudent.end())
    cout<<"Find, the value is"<<iter->second<<endl;
else
    cout<<"Do not Find"<<endl;
```
![](https://3.bp.blogspot.com/-p2D7ql_iuFE/VmU7pe7zQrI/AAAAAAAA_Ks/WC3G3ADrKBE/s1600/27.7.png)

### 4. 刪除與清空
清空 map 中的資料可以用 clear() 函數，判定 map 中是否有資料用 empty() 函數，如果回傳 true 則 map 為空，而資料的刪除用 erase() 函數，它有三種 overload 的用法：
```cpp
//迭代器刪除
iter = mapStudent.find("r123");
mapStudent.erase(iter);

//用關鍵字刪除
int n = mapStudent.erase("r123");//如果刪除了會返回1，否則返回0

//用迭代器範圍刪除 : 把整個map清空
mapStudent.erase(mapStudent.begin(), mapStudent.end());
//等同於mapStudent.clear()
```
### 5. 用法彙整
```cpp
#include <iostream>
#include <string>
#include <map>

using namespace std;

int main(){

    //declaration container and iterator
    map<string, string> mapStudent;
    map<string, string>::iterator iter;
    map<string, string>::reverse_iterator iter_r;

    //insert element
    mapStudent.insert(pair<string, string>("r000", "student_zero"));

    mapStudent["r123"] = "student_first";
    mapStudent["r456"] = "student_second";

    //traversal
    for(iter = mapStudent.begin(); iter != mapStudent.end(); iter++)
                cout<<iter->first<<" "<<iter->second<<endl;
    for(iter_r = mapStudent.rbegin(); iter_r != mapStudent.rend(); iter_r++)
                cout<<iter_r->first<<" "<<iter_r->second<<endl;

    //find and erase the element
    iter = mapStudent.find("r123");
    mapStudent.erase(iter);

    iter = mapStudent.find("r123");

    if(iter != mapStudent.end())
       cout<<"Find, the value is "<<iter->second<<endl;
    else
       cout<<"Do not Find"<<endl;

    return 0;
}
```


以上內容打多轉載至 Mr.Opengate ，個人心得尚在添加中
https://mropengate.blogspot.com/2015/12/cc-map-stl.html
