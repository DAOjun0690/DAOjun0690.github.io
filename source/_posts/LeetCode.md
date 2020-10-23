---
title: LeetCode實戰討論
date: 2020-10-19 17:14:53
tags:
 - 程式語言
 - interview
---

## Leetcode實戰討論
https://leetcode.com/
<!-- more -->
線上知名的 Leetcode網站裡面有許多演算法考題, 內容以英文方式陳述不論是外商或是台商企業都適用, 軟體也有各式程式語言, C/C++/JAVA/Python/Javascript/Ruby/Swift/Go/Scala/kotlin/Rust/PHP, 涵蓋領域很廣, 演算法可以比喻為軟體開發的內功, 而這些程式語言為外在的武功招式, 臨場要表現好要視該職缺的程式語言武功招式, 搭配強大的邏輯演算法內功才能發揮最大表現, 多練習提高自我能力為不二法門! 目前內容為976題, 分為 Easy/ Midium/ Hard, 我們再逐步加入熱門題型的演練:

## Easy:
難度為容易的等級, 可以先挑easy的題目建立手感以及熟悉度!

### * Same Tree:
給定兩個二叉樹，編寫一個函數來檢查它們是否相同。
如果兩個二叉樹在結構上相同並且節點具有相同的值，則認為它們是相同的。
![](https://4.bp.blogspot.com/-u_JiHY0w6XM/XEgyyfqUrlI/AAAAAAABpZ0/DzApCsQ611ASdjoo2krwaDZBNfQMa7igACLcBGAs/s1600/satr.png)

解法:
<details>
<summary>click to 展開</summary>
<pre><code>
/** 樹節點的內容定義如下:
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;      //數值
 *     struct TreeNode *left;  //左子節點
 *     struct TreeNode *right; //右子節點
 * };
 */
bool isSameTree(struct TreeNode`*` p, struct TreeNode`*` q) { //參數傳進來兩個欲比較之樹節點的指標
        if(p == NULL && q == NULL) //檢查空值, 若皆為空則True
            return true;
        else if(p != NULL && q != NULL) //否則, 兩者都非空的話,就必須要進行內容比較
        {
            if(p->val == q->val  //內容相同
               && isSameTree(p->left, q->left) //而且遞迴呼叫function, 判斷左子樹是否相同
               && isSameTree(p->right, q->right))//而且遞迴呼叫function, 判斷右子樹是否相同
            {
                return true; //以上三項都相同才能回傳true
            }
        }

        return false; //其他狀況,則為false
}
</code></pre>
</details>

### * Roman to Integer:
<p>羅馬數字由七個不同的符號表示：I，V，X，L，C，D和M.<br>
<strong>Symbol    –   Value</strong><br>
I         –    1<br>
V         –    5<br>
X         –    10<br>
L         –    50<br>
C         –    100<br>
D         –    500<br>
M         –    1000<br>
&nbsp;<br>
例如，兩個用羅馬數字寫成II，只有兩個加在一起。 十二寫為XII，簡稱為X + II。 第二十七號寫成XXVII，即XX + V + II。　羅馬數字通常從左到右從最大到最小。 但是，4這個數字不是IIII，而是為IV。 因為一個在五個之前，我們減去四個。 同樣的原則適用於九號，即九號。 有六個使用減法的實例：</p>
<p>I可以放在　V（5）和　X（10）之前表達 4 和 9。<br>
X可以放在　L（50）和　C（100）之前，以產生40和90。<br>
C可以放在　D（500）和　M（1000）之前，以產生400和900。<br>
給定羅馬數字，將其轉換為整數。 輸入保證在1到3999的範圍內。<br>
Example 1:<br>
Input: “III”<br>
Output: 3</p>
<p>Example 2:<br>
Input: “IV”<br>
Output: 4</p>
<p>Example 3:<br>
Input: “IX”<br>
Output: 9</p>
<p>Example 4:<br>
Input: “LVIII”<br>
Output: 58<br>
Explanation: L = 50, V= 5, III = 3.</p>

<p>Example 5:<br>
Input: “MCMXCIV”<br>
Output: 1994<br>
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.</p>
解法:
<details>
<summary>click to 展開</summary>
<pre><code>
/* 羅馬符號與數值的對應定義表
Symbol       Value
  I             1
  V             5
  X             10
  L             50
  C             100
  D             500
  M             1000
*/

int romanToInt(char* s) { //參數傳進來字串指標
    int i, sum=0;

    for(i=0; s[i]!='\0'; i++){ //字串指標可以透過array方式個別取值, 搭配for迴圈逐一檢查
        switch (s[i]) {  //建立switch-case語法以個別處理
            case 'M':
                sum += 1000; //先加1000
                if(s[i-1] == 'C') sum -= 100*2; //檢查它的前一位元, 若為C必須扣除2次100, 因為之前C有重復加100, 以下以此類推
                break;
            case 'D':
                sum += 500;
                if(s[i-1] == 'C') sum -= 100*2;                
                break;
            case 'C':
                sum += 100;
                if(s[i-1] == 'X') sum -= 10*2;                
                break;
            case 'L':
                sum += 50;
                if(s[i-1] == 'X') sum -= 10*2;               
                break;
            case 'X':
                sum += 10;
                if(s[i-1] == 'I') sum -= 1*2;  
                break;
            case 'V':    
                sum += 5;
                if(s[i-1] == 'I') sum -= 1*2;  
                break;
            case 'I':
                sum += 1; //I的話, 不用扣值
                break;                 
            default:
                printf("Wrong Character!\n"); //其他字元不支援
        }
    }

    return sum; //加總結果回傳
}
</code></pre>
</details>

### * Two Sum:
解法:
<details>
<summary>click to 展開</summary>
<pre><code>
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target) {
    int i, j, tmpsum;
    int *ret = malloc( 2 * sizeof(int) );


    for(i=0; i < numsSize; i++){
        for(j=i+1; j< numsSize; j++){
            tmpsum = nums[i] + nums[j];
            if( target == tmpsum){
                ret[0] = i;
                ret[1] = j;
                return ret;
            }
        }
    }

    free(ret);

    return NULL;
}
</code></pre>
</details>

### * Reverse Integer:
解法:
<details>
<summary>click to 展開</summary>
<pre><code>
int reverse(int x){

    int i = 0;
    int revNum =0;     //用來代表最後reverse Integer
    int zeroCounter =0;   //紀錄原本x數字, 尾巴帶有多少個0
    int onesDigit =0;     //個位數的值

    bool isPositiveNum = true;    //是負數嗎
    bool isFirstgetZero = true;   //是第一次遇到尾數有0嗎

    if(x < 0 )  //如果原本 x 小於0
    {    
        isPositiveNum = false;  //設為false
        if(x <= pow(-2,31))     //處理overflows算術溢位
            return 0;
        else                    //如果沒overflows算術溢位, 就取x為正數
            x = -x;
    }

    while( x > 0 ){             //只要x為正數, 就要處理
        onesDigit = x % 10;     //取餘數
        if(onesDigit == 0 )     //若餘數是0, 就開始計數
            zeroCounter ++;
        else                    //若餘數非0, 就重置clear計數
            zeroCounter = 0;

        if(revNum > (pow(2,31)-1)/10)   //處理overflows算術溢位,
            return 0;
        else
            revNum = revNum*10 + onesDigit; //如果revNum太大就不適合再加乘10, 會在assign時候出錯!

        x = x / 10;  //為下一次loop作準備
    }

    revNum /= pow(10, zeroCounter); //跳出迴圈後, 必須處理掉尾數的0


    if(!isPositiveNum)    //如果原本x是負數, 則在這裡轉回負數
        revNum =- revNum;

    return revNum;
}
</code></pre>
</details>

### * Search Insert Position:
解法:
<details>
<summary>click to 展開</summary>
<pre><code>
/* 方法1: 透過 Array 與 index 循序尋找 */
int searchInsert(int* nums, int numsSize, int target){
    int i = 0;  //索引數字
    for(i = 0; i < numsSize; i++){ //初始index為0, 循序i++可以透過nums[i]取出int數字
        if(nums[i] >= target)
            return i;  //回傳index
    }
    return numsSize;
}

/* 方法2: 透過 pointer指標 循序尋找, 更省空間 */    
int searchInsert(int* nums, int numsSize, int target){
    int *ptr = NULL;  //索引指標, 注意關鍵在於它被定義為 int*, 所以會以 int的大小找出下一個索引
    for(ptr = nums; ptr != nums+numsSize ;ptr++){ //把初始位置nums給ptr, 之後ptr++就可以找出下一個int數字
        if( *ptr >= target)        
            return (ptr - nums); //透過剪法, 就可以知道是第幾個index
    }
    return numsSize;
}
</code></pre>
</details>

## Medium:
?
### * Add Two Numbers:
解法:
<details>
<summary>click to 展開</summary>
<pre><code>

</code></pre>
</details>


LeetCode746題：使用最小花費爬樓梯
https://www.twblogs.net/a/5c220cb1bd9eee16b4a76a09
