---
title: 物件導向 Object Oriented Programming
date: 2020-09-16 17:41:14
tags:
 - 程式語言
---
什麼叫模組化？簡單來說，就是把特定功能分出來當成一個模組，需要的時候只要呼叫這個模組就好；而需要修正的時候也只要修正模組即可。
<!-- more -->
### 類別
類別比較算是一個範本，裡面定義好該有的屬性和方法，其中方法又大概可以分為一般的方法、類別方法和建構子。例如我們可以定義一個學生類別，裏面包含了name、score 屬性，以及 getName() 方法、setScore() 方法。

### 物件
物件則是實體的東西，由定義好的類別來建立一個物件。

物件導向的三大特型：封裝、繼承、多型。

### 物件導向的封裝性
封裝(**Encapsulation**)，簡單來說就是抽象(Abstract)的概念。對一件事情只需要理解他的外在就好，不需要了解裡面內部的構造。 就像我們只要知道看電視的時候該怎麼轉台、調音量，並不需要知道裡面有多少電線和構造。

而我們在寫類別的時候，把類別定義完，之後要寫物件就只要指定屬性和方法就好，並不需要知道方法是怎麼實作的。這也是一種封裝性。

### 物件導向的繼承性
繼承(**Inheritance**)，要設計一張和原有設計很像的設計圖，可以拿原本的設計圖當底開始畫。 這樣就不需要把相同的東西再宣告一次。

比方說一個經典的例子，如果有一個 Car 類別：
```cpp=
class Car {
    public String plate;
    public String brand;
    public String color;
}
```
記載了車牌、廠牌、顏色三個屬性。如果要多新增一個 Taxi 類別，可以直接繼承 Car 屬性來用：
```cpp=
class Taxi extends Car {
    public String plate;
    public String brand;
    public String color;
    public String driver;
}
```
這就是經典的計程車繼承車 XD。
### 物件導向的多型性
多型(**Polymorphism**)，簡單來說就是同名的方法。多個相同名稱的方法，傳入不同的參數，會執行不同的敘述。 比方說，一個計算面積的方法，如果傳入一個參數，就當正方形來算面積；傳入兩個參數，就當成長方形來算面積。
```java=
public int computeArea(int length) {
    return length * length;
}
public int computeArea(int length, int width) {
    return length * width;
}
```
`其實多型包含多載(Overloading)和複寫(Overriding)，不過暫時知道多載就好了。`

以上就是物件導向的三個特性，不過，物件導向協助我們解決了什麼樣的問題？ 以下引用 Ruby 使用手冊：

物件導向程式設計能夠將單調而重複的邏輯工作委派予資料，把我們對資料的概念從被動轉為主動。換而言之，

- 資料不再是一個開蓋盒子，只能讓我們自己去找東西或放東西進去。
- 資料變成是能夠運作的機器，具有標示明確的開關與功能。
