---
title: programming
date: 2020-09-16 17:01:35
tags:
 - 程式語言
---
[Swap](#Swap)
[Fibonacci](#Fibonacci)

<!-- more -->

#### Swap

```C=
# Swap FUNCTION
void swap (int &c , int &d){
   int temp=c;
   c=d;
   d=temp;
}
```
#### Fibonacci
Fibonacci number 費氏數列
假設題目要求：給一數字N，求費氏數列中第N數的值
構想：N = 1 or 2時，直接輸入Ans = 1; 若N >=3，則進入迴圈判斷計算(N=3 to N)，利用兩個變數儲存 N-1 與 N-2 的值，程式碼如下：
```Java=
public class Fibonacci {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int number = 0;
		Scanner scanner = new Scanner(System.in);

		System.out.println("Enter a number: ");
		number = scanner.nextInt();

		if(number == 1) {
			System.out.println("last Fibonacci num = 1");
		} else if(number == 2) {
			System.out.println("last Fibonacci num = 1");
		} else {
			int res = calculate(number);
			System.out.println("last Fibonacci num = "+res);
		}
	}

	private static int calculate(int num) {
		// TODO Auto-generated method stub
		int p1 = 1; //the first number in fibonacci
		int p2 = 1; //the second number in fibonacci
		int res = 0;
		for(int i = 3; i <= num; i++) {
			res = p1 + p2;
			p1 = p2;
			p2 = res;
		}
		return res;
	}
}
```
#### Two SUM
```cpp=
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> a;//建立hash表存放数组元素
        vector<int> b(2);//存放结果
        for(int i=0;i<nums.size();i++)
            a.insert(pair<int,int>(nums[i],i));
        for(int i=0;i<nums.size();i++)
        {
            if(a.count(target-nums[i])>0&&(a[target-nums[i]]!=i))
            //判断是否找到目标元素且目标元素不能是本身
            {
                b[0]=i;
                b[1]=a[target-nums[i]];
                return b;
            }
        }
        return {};
    }
};
```
```java=
private int[] bubbleSort(int[] array) {
    int temp;
    for (int i = 0; i < array.length - 1; i++) {
        boolean Flag = false; // 是否发生交换。没有交换，提前跳出外层循环
        for (int j = 0; j < array.length - 1 - i; j++) {
            if (array[j] > array[j + 1]) {
                temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
                Flag = true;
            }
        }
        if (!Flag)
        {
            break;
        }
    }
    return array;
}
```
#### 找到兩陣列中 A有B沒有
```python=
#我目前有兩個List，如下所示：
Lst1 = [1, 2, 3]
Lst2 = [2, 3, 4]
#如果我想要知道以 Lst1 為主，和 Lst2 有哪裡不一樣
#也就是說 刪除 Lst1 和 Lst2 重複一樣的東西之後將 Lst1 剩下來的傳回去
s1 = set(Lst1)
s2 = set(Lst2)
print s1.difference(s2) #結果會是 set([1])
#得到得結果會是一個 "set" 使用 list() 函數將他化回原形(list)
result = list(s1.difference(s2))
#這時候result 就是大家熟悉的 list 啦
```
long->字串
`String.valueOf(long l)`
字串->long
`Long.parseLong(String s)`

找M~N質數
```java=
public class PrimerNum {
    public void getPrimer(int n,int m){
        int j,sum=0;
        int count=0;
        if(n<m){
            for(int i=n;i<=m;i++){
                for(j=2;j<=i;j++){
                    if((i%j)==0){
                        break;
                    }
                }
                if(j==i){
                    sum+=i;
                    count++;
                    System.out.print(i+"\t");
                }
        }
            System.out.println("\n");
            System.out.println("輸出的質數總和為："+sum);
            System.out.println("質數總數為："+count);
        }else{
            System.out.println("輸入的第一個數必須要比第二個數小");
        }
    }

public static void main(String[] args) {
// TODO Auto-generated method stub
    PrimerNum pn=new PrimerNum();
    pn.getPrimer(1, 10);
}
```
bubble sort
```java=
private int[] bubbleSort(int[] array) {
    int temp;
    for (int i = 0; i < array.length - 1; i++) {
        boolean Flag = false; // 是否发生交换。没有交换，提前跳出外层循环
        for (int j = 0; j < array.length - 1 - i; j++) {
            if (array[j] > array[j + 1]) {
                temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
                Flag = true;
            }
        }
        if (!Flag)
        {
            break;
        }
    }
    return array;
}
```


![C 語言程式記憶體配置](https://i.imgur.com/CnL8Ctp.png)
