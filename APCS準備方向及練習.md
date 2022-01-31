---
title: APCS準備方向及練習
tags: APCS
language: zh-tw
---
# APCS準備方向及練習
主旨：希望能幫助到大家在APCS中取得好成績
編者：高雄中學程式設計社 J.T.
> 本講義參照：https://github.com/sparanoid/chinese-copywriting-guidelines

:::warning
<div class=display >
</div>
<div class=display>
    <font size=5px color=#E2C2DE>
        <strong>Cryptography(cipher)</strong>
    </font>
    </br>
    <img src= "https://i.imgur.com/MoNFm7S.png" weight=300 height=300>
    </br>
    <font size=5px color=#E2C2DE>
        <strong>Presented by J.Tsai</strong>
    </font>
</div>
<style>
.display {
  text-align:center;
}
</style>
:::

---

## APCS簡介
APCS為Advanced Placement Computer Science的英文縮寫，是指「大學程式設計先修檢測」。其檢測模式乃參考美國大學先修課程（Advanced Placement，AP），與各大學合作命題，並確定檢定用題目經過信效度考驗，以確保檢定結果之公信力。
APCS成績除了是申請入學APCS組必要成績外，也是多校特殊選才等多元入學管道重要參考資料。APCS檢測每年舉辦三次，檢測日程預訂在1月、6月及10月，實際日期以公告為準。
其中測驗分為觀念題及實作題，公布成績時會有原始分數跟級分數(一至五級分)。

1.程式設計觀念題：為選擇題測驗，總共包含50道試題，並且藉由試題區塊配置成兩份測驗題本，每份測驗題本共有25道試題。
2.程式設計實作題：為非選擇題測驗，總共包含4個題組試題，每個題組各有10-20組測試資料
https://apcs.csie.ntnu.edu.tw/index.php/apcs-introduction/

### 為什麼要考APCS?
1.保送TOI初選：APCS實作三級分以上，可跳過TOI海選，直接進入初選。
2.檢測自己學習狀況，APCS難度適中，是很好的檢測項目。
3.大學端採計
:::spoiler 採計校系總覽及篩選倍率
![](https://i.imgur.com/dEzR6HN.jpg)
資料來源：https://www.unews.com.tw/News/Info/3799
:::

---

## CH1 複習

### 1-1複習
**複習所學過的基礎知識,就這樣，沒了...**

---

### 一、選擇結構 selection control
**1.單向選擇結構 if statement**
若符合條件，則執行敘述。
```cpp=
if(條件){
    條件成立時(不為0)時，執行的敘述;
}
```

---

**2.雙向選擇結構 if...else statement**
若符合條件，則執行敘述1，若不符合，則執行敘述2。
```cpp=
if(條件){
    條件成立時(不為0)時，執行的敘述1;
}else{
    條件不成立時(為0)時，執行的敘述2;
}
```

---

**3.多向選擇結構 if...else if...else statement**
若符合條件1，則執行敘述1，若不符合條件1，則檢查條件2，若符合，則執行敘述2，以此類推。
```cpp=
if(條件1){
    條件1成立時(不為0)時，執行的敘述1;
}else if(條件2){
    條件2成立時(為0)時，執行的敘述2;
}else{
    以上條件都不成立，執行的敘述3;
}
```

---

**4.多向選擇結構 switch case**
"case:"後接敘述。
***如果用switch，不加break的話就無法跳脫程式，要多注意。**

```cpp=
switch(變數){
    case 1:
        敘述1;
        break;
    case 2:
        敘述2;
        break;
    default:
        敘述3;
        break;
}
```

:::spoiler 補充：條件運算子
條件運算子 ? : （也稱為三元運算子）
會評估布林運算式，並根據布林運算式是否評估為"或"
傳回兩個運算式其中之一的結果 true / false 
```cpp=
int var = 50;

cout << (var==50) ? "五十" : "不是五十";

相當於:

if(var == 50){
    cout << "五十";
}else{
    cout << "不是五十";
}
```
啊也可以推廣成多向選擇結構窩~
:::

---

### 二、迴圈 loop
**1.while迴圈 while loop**
若符合條件，執行括號中程式碼
最好設定終止條件(條件式中設定或是用break)

```cpp=
while(條件){
    敘述1;
    敘述2;
    ...
}
```

---

**2.for迴圈 for loop**
第一項是初始設定，第二項是條件，第三項是更新。
初始設定只進行一次(也可不設定)，接著丟入條件判斷，若符合，在執行完敘述後再進行更新，更新後再丟回條件判斷。
:::warning
**注意：要用分號區隔**
:::
```cpp=
for(初始設定;條件;更新){
    敘述1;
    敘述2;
    ...
}
```

:::spoiler 基於範圍的for迴圈
對於一個有範圍的集合而言，如果再去說明迴圈的範圍，就很多此一舉
所以，C++11中引入了基於範圍的for迴圈。

for迴圈後的括號由冒號“：”分為兩部分：
* 第一部分是範圍內用於迭代的變數
* 第二部分則表示被迭代的範圍。

編譯器選項要至少C11以上窩(默認是C98啦)
` -std=c++11 `
` -std=c++14 `
` -std=c++17 `

```cpp=
int a[5] = {1,2,3,4,5};

for(auto x : a){
    cout<<x<<endl;
}

相當於：

for (int x=0;x<sizeof(array)/sizeof(array[0]);x++){
    cout<<a[x]<<endl;
}
```

:::

---

### 三、陣列 array
**1.陣列 array**
陣列是從"0"開始存取，舉以下為例，格子為0~9，共10格。
```cpp=
int arr1[10]; //宣告共10格的整數陣列
for(int i=0;i<10;i++){
    cin>>arr1[i]; //輸入至陣列中
}
return 0;
```
除了平常的一維陣列，也可以開二維甚至三維的多維陣列
```cpp=
int arr2[10][10]; //宣告共10格x10格的整數陣列
int arr3[10][10][10]; //宣告共10格x10格x10格的整數陣列
```
以下為初始化的參考寫法：
```cpp=
int arr1[10]={}; //方法一
int arr2[10]={0}; //方法二
int arr3[10];
for(int i=0;i<sizeof(arr3);i++){
    arr3[i]=0;
} //方法三
int arr4[10][10];
memset(arr4,0,sizeof(arr4)); //毒瘤(x
```

---

### CH1題目

1.zerojudge a.005
https://zerojudge.tw/ShowProblem?problemid=a005
2.zerojudge a.024
https://zerojudge.tw/ShowProblem?problemid=a024
3.zerojudge a.053
https://zerojudge.tw/ShowProblem?problemid=a053


---

## CH2 基本資料型態
### 2-1指標
取址符號 `&`
指派運算子 `=`
提領運算子 `*`

#### 想想看
設計一個函式swap使 a, b 兩數互換
:::spoiler 這樣對嗎?
```cpp=
#include<bits/stdc++.h>
using namespace std;
void swap(int x,int y){
    int tmp;
    tmp=x;
    x=y;
    y=tmp;
}

int main(){
    int a=1,b=0;
    cout<<a<<" "<<b<<endl;
    swap(a,b);
    cout<<a<<" "<<b<<endl;
}
/*
output:
1 0
1 0
*/
:::
奇怪明明swap就進行交換了啊，怎麼輸出會不變？
這時就要談到我們的取址符號及提領運算子了！

---
### 一、取址符號及提領運算子
取址符號（`&`）：存取該變數的記憶體位址（address）。
提領運算子（`*`）：取該記憶體位址的值。

以分房間為例，假設101號房內有一名男性。
若不加符號直接複製主函式變數的值後傳遞，那副函式的變數值就是「男」。（傳值 pass by value）
若使用取址符號及提領運算子，則`&`儲存到的是"101"，`*`則是找到在房間裡的人。（傳址 pass by address）

拿以上的寫法做例子、副函式取 x, y 時是「傳值」，不會影響本來 a, b 的值。
此時，要利用取址符號及提領運算子做「傳址」，是直接修改記憶體空間。
那剛才的程式碼應該怎麼改呢？
:::spoiler 這樣才對！
```cpp=
#include<bits/stdc++.h>
using namespace std;
void swap(int *x,int *y){
    int tmp;
    tmp=*x;
    *x=*y;
    *y=tmp;
}

int main(){
    int a=1,b=0;
    cout<<a<<" "<<b<<endl;
    swap(&a,&b);
    cout<<a<<" "<<b<<endl;
}
/*
output:
1 0
0 1
*/
:::


:::spoiler 我不是毒瘤，我是C++11
```cpp=
#include<bits/stdc++.h>
using namespace std;

int main(){
    auto swap=[&](int &a, int &b){
        a ^= b ^= a ^= b;
    };

    int a=50,b=100;
    swap(a,b);
    cout<<a<<" "<<b<<endl;
    //output:100 50

    return 0；
}
:::

:::warning
若如上述以int *x來做宣告，則此時作為指標宣告(pointer)。
**上述兩者可用於int, float, double等資料型態。**
*提醒：
swap有在algorithm的內建函式庫裡，直接用就好，沒事不要自己寫。*
:::

---
### 二、指派運算子
就是你我熟知的`=`
指派運算子(`=`):要相同型態才能指派(int=int,float=float,...)

---

### 三、指標運算子(+,=,[])
運算子(`+`,`-`):
可以對地址增減一個整數
addr±i意思是增加/減少i個單位的資料型態。

運算子(`［］`):
arr[i]等同於*(arr+i)。
當我們把陣列當成數值，做賦值當我們把陣列當成數值，做賦值、運算、比較關係等運算時，其實隱含了陣列和指標的轉換。
```cpp=
//範例:sort
int arr[1000];
sort(arr,arr+1000,cmp);
//從arr的第一個位址排序到第1000個位址
```
```cpp=
//範例:指標不能相加，但可以相減
int i,j,k;
int *p=&i,*q=&j;
double x,y;
double *r=&x,*s=&y
cout<<p-q<<endl;
cout<<&i-&k<<endl;
cout<<r-s;
/*output:
1
2
1
*/
//補充:每次執行結果的記憶體位址可能不同
```


---

#### 指標的初始化
**設定空指標可以用:**
- 0是唯一可以放進指標的數字
- NULL是C語言常用的
- nullstr是C++ 11裡用來表示空指標的常數

---

#### 傳送位址到函式裡
``` cpp=
//範例:傳遞位址至函式中
#include<bits/stdc++.h>
using namespace std;
void func(int val,int *addr){
    cout<<"val = "<<val<<",addr = "<<addr<<endl;
}

int main(){
    int x=1234;
    func(x,&x);
    cout<<"x = "<<x<<",&x = "<<&x;
}
 /*output
val = 1234,addr = 0x69feec
x = 1234,&x = 0x69feec
*/

//注意:記憶體空間視電腦而定，每次執行結果可能不同
```

---

#### 傳遞陣列到函式裡
在C/C++裡我們會傳遞陣列的起始位置到函式裡
```cpp=
//範例:傳遞陣列至函式中
#include<bits/stdc++.h>
using namespace std;
void print(int *p){
    for(int i=0;i<=sizeof(p);i++){
        cout<<p[i]<<" ";
    }
    cout<<endl;
}

int main(){
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        cin>>a[i];
    }
    print(arr);
}
```
**備註：如果真的有需要，也可直接開全域陣列，就不用一直傳來傳去。**

---

### 補充:
其實常用的內建sort及reverse(標頭檔須包含algorithm)都有用到指標的概念歐。
:::spoiler sort函式格式：
sort(array_begin,array_end,tmp);
**範例:**
```cpp=
int arr[10]={1,7,5,3,4,6,9,0,13,2};
sort(arr,arr+10);
//此時arr[10]={0,1,2,3,4,5,6,7,9,13}
//若沒有加tmp函式判斷，則預設為升冪排列
:::
:::spoiler reverse格式：
reverse(array_begin,array_end);
**範例:**
```cpp=
//接續上面的sort
reverse(arr,arr+10);
//此時arr[10]={13,9,7,6,5,4,3,2,1,0}
//將陣列反轉，此時為降冪排列
:::
其中的(arr,arr+n);就是利用指標的概念讀取陣列的記憶體位址後作加減平移。


---

### 2-2多維陣列
```cpp=
int arr2[10][10]; //宣告共10格x10格的整數陣列
int arr3[10][10][10]; //宣告共10格x10格x10格的整數陣列
```
因為之前已提過多維陣列，此處就簡略帶過
其實多維陣列的概念很簡單，舉二維陣列而言，上述arr2[10][10]可視為是10個10格的陣列。
### 2-3字元陣列
### 一、字元 char
一個char變數就是儲存ASCII碼裡的一個整數編號(0~127)<其中分成可顯示以及不可顯示兩類
:::spoiler ASCII對照表
![](https://i.imgur.com/rFR4V9N.png)
:::
(1)半形字(可顯示)：
ASCII編碼中的32~126是可顯示的半形字，在C++中以char輸出就會輸出半形字。
(2)控制字元(不可顯示)：
編號0~31、127一個整數編號會對應到一個控制字元，例如:0對應到"\0"代表空字元"NULL"，10對應到"\n"代表換行字元(ENTER)。
:::warning
注意:當輸入文字含有空格時，會視為輸入結束，若要包含輸入包含空格的句子，可使用cin.getline(chartype,streamsize)，還要注意的一點是使用cin.getline時必須多開一格，最後一格是"\0"代表輸入結束。
```cpp=
char ch[500];
cin.getline(ch,500);
cout<<ch;
```
:::
### 二、字串 string
string是一種很方便的變數類型，可以用string建立一個字元陣列，不同於char的是string不用估算字元數量，但是跟char一樣的問題是遇到"\0"會視為輸入結束，所以當我們需要儲存含有空格的字串時可以使用getline(cin,stringtype)來儲存。
```cpp=
string str;
getline(cin,str);
cout<<str;
```
### 2-4結構
#### 結構struct
* 結合多個相關變數在同一個名稱中，即便是不同資料型態也可以。
* 各成員的儲存位置是連續的。
:::info
以下範例會以儲存考試成績來說明，以下為範例:
A班有三位學生，座號1~3分別是Amy,Ben,Carol，某次考試考了三科，分別是國文、數學及英文，讓我們試著用結構來記錄他們的考試成績吧！
:::
#### 宣告變數
:::warning
注意:使用struct宣告時一定要在大括號後加`;`才能宣告
:::
```cpp=
struct score{
    int num,chinese,math,english;
    string name;
};

score A[3];
```
#### 存取資料及輸出
以下為完整原始碼
```cpp=
#include<bits/stdc++.h>
using namespace std;
int main(){
    struct score{
        int num,chinese,math,english;
        string name;
    };
    score A[3];
    for(int i=0;i<3;i++){
        A[i].num=i+1;
        cin>>A[i].name>>A[i].chinese>>A[i].math>>A[i].english;
    }
    for(int i=0;i<3;i++){
        cout<<A[i].num<<"."<<A[i].name<<":"<<A[i].chinese<<","<<A[i].math<<","<<A[i].english<<endl;
    }
}
```
:::success
input:
Amy 50 60 70
Ben 90 95 100
Carol 40 35 30
output:
1.Amy:50,60,70
2.Ben:90,95,100
3.Carol:40,35,30
:::
### 補充：
如果想知道一個字的ASCII碼可以用(int)來轉換，反之，如果想知道一個數字對應的文字也可以用(char)轉換，範例如下：
:::spoiler 轉換方式
```cpp=
int n=65; //ASCII碼65對應到的字元
string s;
s[0]='A'; //A的ASCII碼
//如果想知道一個字元的ASCII碼，也可以直接把字元塞到變數裡面
int k='A'; //A的ASCII碼
cout<<(char)n<<" "<<(int)s[0]<<" "<<k<<endl; 
//output:A 65 65
```
:::
### CH2題目
1.zerojudge a.009
https://zerojudge.tw/ShowProblem?problemid=a009
2.zerojudge a.022
https://zerojudge.tw/ShowProblem?problemid=a022
3.自己寫一個ROT13解碼器
About ROT13:https://zh.wikipedia.org/wiki/ROT13
4.zerojudge d.091
https://zerojudge.tw/ShowProblem?problemid=d091


---

## CH3 複雜度
### 3-1漸進符號
**漸進符號 $O(n)$(big o):**
大O符號在分析演算法效率的時候非常有用，若假設現有一個規模為$n$的問題需要花費時間如以下函式：
$T(n)=5n^{3}+4n^{2}+7n+10$
則我們可以說
$T(n) \in\ O(n^{3})$ 或 $T(n)=O(n^{3})$
因為在n值夠大時，最高次項對數值的影響遠超過其他各項，故可忽略其他項。
而漸進符號可以幫助我們估算程式執行時的複雜度(空間及時間複雜度)。

---

### 3-2空間複雜度
**空間複雜度(Space Complexity):**
簡單的來說就是，電腦執行演算法所需要耗費的空間記憶體。
舉以下兩段程式碼為例：
```cpp=
#include<bits/stdc++.h>
using namespace std;
int main(){
    int n;
    cin>>n;
    for(int i=0;i<=10;i++){
        cout<<i<<" ";
    }
}
```
不管n值為多少都不會影響記憶體空間，此時空間複雜度為$O(1)$。
```cpp=
#include<bits/stdc++.h>
using namespace std;
int main(){
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        arr[i]=i;
    }
}
```
n值的大小會影響到記憶體空間，此時空間複雜度為$O(n)$。

---

### 3-3時間複雜度
**時間複雜度(Time complexity):**
時間複雜度描述該演算法的執行時間，以下範例：
```cpp=
#include<bits/stdc++.h>
using namespace std;
int main(){
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        arr[i]=i;
    }
}
```
該範例為一迴圈，時間複雜度為$O(n)$。
```cpp=
#include<bits/stdc++.h>
using namespace std;
int main(){
    int n;
    cin>>n;
    int arr[n][n];
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            arr[i][j]=i*j;
        }
    }
}
```
該範例為雙重迴圈，時間複雜度為$O(n^{2})$。
```cpp=
//設現在已給定一全域升冪排序陣列arr[n]
int binary_search(int key){ //key為要尋找的數
    int left=0,right=n,mid,rec=-1;
    //left代表陣列左端，right代表陣列右端，rec用於紀錄是否找到一數等於key
	while(left<=right){
            mid=left+(right-left)/2;
            if(arr[mid]>key){
                right=mid-1;
            }else if(arr[mid]<key){
                left=mid+1;
            }else{
                rec=mid
                break;
            }
        }
    return rec;
}
```
以上為一段二分搜尋的程式碼，在後面幾章會再做詳細介紹，此處因為二分搜尋的概念就是每次折半搜尋所以時間複雜度為$O(\log n)$。

---

經由上述3-2及3-3的內容，其實不難發現，有時候時間複雜度跟空間複雜可以互相轉換，但並非每次都可以，以上述二分搜尋為例，時間複雜度為$O(\log n)$，但是空間複雜度為$O(1)$。若以APCS及程式競賽為例，往往是比較在乎時間複雜度，因為如果時間複雜度太大可能造成TLE(執行時間過長)。基本上空間是不太會超過題目限制，除非是開了過大的陣列或是忘記歸還記憶體。
:::spoiler 複雜度變化圖形
![](https://i.imgur.com/Tor23DK.png)
資料來源:http://robot39.blogspot.com/2013/09/computing-power-and-time-complexity.html
:::

---

## CH4 函式
### 4-1內建函式
函式的用處就是在我們重複執行某項指令時非常好用的東西，或是將常用到的指令做成函式，下次就可以直接使用。
以下舉一些常見函式，例如:
sort(),reverse(),max(),min(),find()...(存放在algorithm函式庫中)
pow(),sqrt(),rand(),time()...(存放在cmath函式庫中)
在使用前須包含對應的標頭檔，但是要去記個別函式對應到的函式庫是一件很麻煩的事，所以也可以直接使用我們的「萬能標頭檔」。
```cpp=
#include<bits/stdc++.h>
```
:::spoiler 萬能標頭檔原始碼(參考用)
```cpp=
// C++ includes used for precompiling -*- C++ -*-

// Copyright (C) 2003-2014 Free Software Foundation, Inc.
//
// This file is part of the GNU ISO C++ Library.  This library is free
// software; you can redistribute it and/or modify it under the
// terms of the GNU General Public License as published by the
// Free Software Foundation; either version 3, or (at your option)
// any later version.

// This library is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
// GNU General Public License for more details.

// Under Section 7 of GPL version 3, you are granted additional
// permissions described in the GCC Runtime Library Exception, version
// 3.1, as published by the Free Software Foundation.

// You should have received a copy of the GNU General Public License and
// a copy of the GCC Runtime Library Exception along with this program;
// see the files COPYING3 and COPYING.RUNTIME respectively.  If not, see
// <http://www.gnu.org/licenses/>.

/** @file stdc++.h
 *  This is an implementation file for a precompiled header.
 */

// 17.4.1.2 Headers

// C
#ifndef _GLIBCXX_NO_ASSERT
#include <cassert>
#endif
#include <cctype>
#include <cerrno>
#include <cfloat>
#include <ciso646>
#include <climits>
#include <clocale>
#include <cmath>
#include <csetjmp>
#include <csignal>
#include <cstdarg>
#include <cstddef>
#include <cstdio>
#include <cstdlib>
#include <cstring>
#include <ctime>

#if __cplusplus >= 201103L
#include <ccomplex>
#include <cfenv>
#include <cinttypes>
#include <cstdalign>
#include <cstdbool>
#include <cstdint>
#include <ctgmath>
#include <cwchar>
#include <cwctype>
#endif

// C++
#include <algorithm>
#include <bitset>
#include <complex>
#include <deque>
#include <exception>
#include <fstream>
#include <functional>
#include <iomanip>
#include <ios>
#include <iosfwd>
#include <iostream>
#include <istream>
#include <iterator>
#include <limits>
#include <list>
#include <locale>
#include <map>
#include <memory>
#include <new>
#include <numeric>
#include <ostream>
#include <queue>
#include <set>
#include <sstream>
#include <stack>
#include <stdexcept>
#include <streambuf>
#include <string>
#include <typeinfo>
#include <utility>
#include <valarray>
#include <vector>

#if __cplusplus >= 201103L
#include <array>
#include <atomic>
#include <chrono>
#include <condition_variable>
#include <forward_list>
#include <future>
#include <initializer_list>
#include <mutex>
#include <random>
#include <ratio>
#include <regex>
#include <scoped_allocator>
#include <system_error>
#include <thread>
#include <tuple>
#include <typeindex>
#include <type_traits>
#include <unordered_map>
#include <unordered_set>
#endif
```
參考資料:https://www.itread01.com/content/1547093362.html
:::
通常主流的OJ都是支持的，例如：ZeroJudge,Codeforces...
但是還是有一些OJ，例如：Greenjudge是不支持的喔。
:::warning
其中還有要注意的一點是，因為萬能標頭檔包含很多函式庫，所以編譯時間會比較長！
:::
### 4-2自訂函式
當然，內建函式不一定能滿足所有狀況，有的時候可能要自己刻一個自訂函式，而自訂函式也分為回傳值跟不回傳值，而傳值的函式也分為各種變數型態，例如：bool,int,long long...
函式還有其他各種好處：
* 把程式拆成一個一個小區塊，方便與人分工合作。
* 把經常出現的程式碼寫成函式，可以增加可讀性和維護性。
以下範例：
```cpp=
void Print(int arr[]){
    for(int i=0;i<sizeof(arr);i++){
        cout<<arr[i]<<endl;
    }
} //此處為執行而不傳值
int max(int a,int b){
    if(a>=b){
        return a;
    }else{
        return b;
    }
} //回傳值的函式
```
::: warning
注意：函式一旦執行到return，就會立刻回傳，略過之後所有程式碼。
:::
其中傳值的函式有一項重要的應用就是遞迴，以下舉費氏數列作為例子：
```cpp=
#include<bits/stdc++.h>
#define ll long long
using namespace std;
int fib(ll x){ //透過遞迴計算
    if(x==1||x==0){ //設置起始項
        return x;
    }else{
        return fib(x-1)+fib(x-2); //遞迴計算
    }
} //一旦查詢項數不為1或0時進行遞迴
```

### CH4題目
1.zerojudge a.044
https://zerojudge.tw/ShowProblem?problemid=a044

---

## CH5 基礎資料結構（容器）
**先備知識：什麼是STL**
STL就是標準模板庫(Standard Template Library)，是一個C++軟體庫，裡面存放了很多常用的東西，其中包含4個組件，分別為演算法、容器、函式、疊代器。

詳見：[STL](https://zh.wikipedia.org/wiki/%E6%A0%87%E5%87%86%E6%A8%A1%E6%9D%BF%E5%BA%93)
### 5-1 Vector
### 一、向量(vector)介紹
vector可以視為一個動態陣列，有以下幾個常用基本功能：
|函式|功能|
|--|--|
|size|回傳向量(vector)內元素的數量|
|front|取得向量(vector)中的第一個元素|
|back|取得向量(vector)中的最後一個元素|
|push_back|從向量(vector)後端推入元素|
|pop_back|從向量(vector)後端移除元素|
|insert|從指定位子插入元素|
|erase|從指定位子移除元素|
|clear|清空向量(vector)|
以下範例：
```cpp=
#include<bits/stdc++.h>
using namespace std;
int main(){
    vector <int> v;
    for(int n,i=0;i<10;i++){
        cin>>n;
        v.push_back(n);
    }
    for(int i=0;i<10;i++){
        cout<<v.back()<<" ";
        v.pop_back();
    }
}
/*
input:
1 2 3 4 5 6 7 8 9 10
output:
10 9 8 7 6 5 4 3 2 1
*/
```
### 二、向量(vector)的優缺點
1.優點
- 宣告時不用確定大小

2.缺點
- 在內部進行刪除時效率很低

---

### 5-2 Stack
### 一、堆疊(stack)介紹
stack是一種**先進後出 FILO**(First In, Last Out)的資料結構，就像是堆東西一樣，由下往上堆，要拿取時只能從上往下拿。
堆疊(stack)有以下幾個常用基本功能：
|函式|功能|
|--|--|
|top|回傳堆疊(stack)頂端的元素|
|push|加入一個元素到堆疊(stack)裡|
|pop|從堆疊(stack)頂端移除元素|
以下範例：
```cpp=
#include<bits/stdc++.h>
using namespace std;
int main(){
    stack <int> s;
    for(int n,i=0;i<10;i++){
        cin>>n;
        s.push(n);
    }
    for(int i=0;i<10;i++){
        cout<<s.top()<<" ";
        s.pop();
    }
}
/*
input:
1 2 3 4 5 6 7 8 9 10
output:
10 9 8 7 6 5 4 3 2 1
*/
```
### 二、堆疊(stack)的優缺點
1.優點：
- 操作容易，方便實作

2.缺點：
- 只能操作頂端的值

---
### 5-3 Queue
### 一、佇列(queue)介紹
queue是一種**先進先出 FIFO**(First In, First Out)的資料結構，就像排隊一樣，先排隊的就先出去。
堆疊(stack)有以下幾個常用基本功能：
|函式|功能|
|--|--|
|front|取得佇列(queue)中的第一個元素|
|back|取得佇列(queue)中的最後一個元素|
|push|從佇列(queue)後端推入元素|
|pop|從佇列(queue)前端移除元素|
以下範例：
```cpp=
#include<bits/stdc++.h>
using namespace std;
int main(){
    queue <int> q;
    for(int n,i=0;i<10;i++){
        cin>>n;
        q.push(n);
    }
    for(int i=0;i<10;i++){
        cout<<q.front()<<" ";
        q.pop();
    }
}
/*
input:
1 2 3 4 5 6 7 8 9 10
output:
1 2 3 4 5 6 7 8 9 10
*/
```
### 二、佇列(queue)的優缺點
1.優點
- 可以快速的把頭的值拿掉

2.缺點
- 只能操作頭跟尾


---

## CH6 基礎資料結構（樹狀結構）
### 6-1 樹的介紹
![](https://i.imgur.com/2NFkLqE.png)
本章會簡單敘述關於樹狀結構的概念以及樹狀結構的應用。

一、關於樹的名詞介紹：
- 父節點（Parent）：節點的上一個節點。
- 子節點（Child）：節點的下一個節點。
- 根節點（Root）：沒有父節點的節點。
- 葉節點（Leaf）：沒有子節點的節點，又稱外部節點。
- 節點分支度（Degree）：節點的子節點數。
- 樹分支度（Degree of tree）：樹的各節點中最大的節點分支度。
- 階層（Level）：從節點到葉節點的最大高度。
- 樹高度（Height of tree）：從根節點到葉節點的最大高度，又稱深度(Depth of tree)。
- 森林（Forest）：兩棵以上不相交的樹。
- N元樹（N-ary tree）：所有節點的子節點都不超過N（樹分支度）。

二、以下為樹的定義：
- 樹是由一個以上的節點形成的有限集合
- 存在一個特殊的節點稱為根節點（root）
    - 根節點不存在父節點 
    - 其餘節點分為數個不相交的子集合稱為子樹（subtree）
        - 每個子節點有有限個子節點
- 樹中沒有環路（cycle）
### 6-2 樹的應用
### 一、二元樹
#### 完美二元樹
![](https://i.imgur.com/0XgsykH.png)
如同上面所述，二元樹的定義就是所有子樹的子節點都不超過2，完美二元樹的定義就是每個階層都被填滿，現在假設有一深度為$N$的完美二元樹，則會有以下性質：
1. 這棵樹共有$2^N-1$個節點
2. 第$K$層會有$2^{(K-1)}$個節點

#### 完滿二元樹
![](https://i.imgur.com/39HwDml.png)
每個節點有0或2個子節點。也稱作嚴格二元樹、正規二元樹。
#### 完全二元樹
![](https://i.imgur.com/kR9LhvK.png)
最後一階層之外的階層都必須填滿，而最後一階層的節點必須由左至右填入。
#### 歪斜二元樹
![](https://i.imgur.com/ALlpzVO.png)
都所有節點都只有同一邊的子節點的時候，就稱為歪斜二元樹。

---

### 二、二元搜尋樹
#### 二元搜尋樹的介紹
二元搜尋樹又稱有序二元樹或排序二元樹，在各種資料結構中的優勢就是它在尋找或是插入時的時間複雜度較低，為$O(\log n)$，那什麼是二元搜尋樹呢？
二元搜尋樹具有以下性質：
- 若任意節點的左子樹不空，則左子樹上所有節點的值均小於它的根節點的值
- 若任意節點的右子樹不空，則右子樹上所有節點的值均大於或等於它的根節點的值
- 任意節點的左、右子樹也分別為二元搜尋樹
- **任兩節點值不相等**
#### 二元搜尋樹的建立
將第一個值作為根節點，接下來輸入的值大於根節點則進入右子樹，反之則進入左子樹，重複進行這個步驟就可以得到二元搜尋樹。
``` cpp=
#include<bits/stdc++.h>
using namespace std;
int arr[1025]=0;
void bst(int x,int y){
    if(arr[x]){
        if(y>arr[x]){
            bst(2*x+1,y);
        }else{
            bst(2*x,y);
        }
    }else{
        arr[x]=y;
    }
}
int main(){
    int n;
    while(cin>>n){
        bst(1,n);
    }
}
```
#### 二元搜尋樹的搜尋
搜尋就是二元搜尋樹最擅長的事了，因為資料進入二元樹時就經歷過排序了，所以查找速度非常快，時間複雜度為$O(depth$ $of$ $tree)$，最差的狀況也只有$O(n)$
```cpp=
int find(int x,int y){ //
    if(arr[x]==y){
        
    }
}
```

---

