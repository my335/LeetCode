# 题目：

*C**L**Z* 银行只有两个接待窗口，VIP*V**I**P* 窗口和普通窗口，VIP*V**I**P* 用户进入 VIP*V**I**P* 窗口排队，剩下的进入普通窗口排队。现有 M*M* 次操作，操作有四种类型，如下：

- `IN name V`：表示一名叫 `name` 的用户到 VIP*V**I**P* 窗口排队
- `OUT V`：表示 VIP*V**I**P* 窗口队头的用户离开排队
- `IN name N`：表示一名叫 `name` 的用户到普通窗口排队
- `OUT N`：表示普通窗口队头的用户离开排队

求 M*M* 次操作结束后 VIP*V**I**P* 窗口队列和普通窗口队列中的姓名。

### 输入描述

第一行是一个整数 M（1\leq M \leq 1000）*M*（1≤*M*≤1000），表示一共有 M*M* 次操作。

第二行到第 M+1*M*+1 行输入操作，格式如下：

- `IN name V`
- `OUT V`
- `IN name N`
- `OUT N`

### 输出描述

输出 M*M* 次操作后 VIP*V**I**P* 窗口队列和普通窗口队列中的姓名（从头到尾），先输出 VIP*V**I**P* 窗口队列后输出普通窗口队列。

### 输入输出样例

#### 示例 1

> 输入

```txt
5
IN xiaoming N
IN Adel V
IN laozhao N
OUT N
IN CLZ V
```

> 输出

```txt
Adel
CLZ
laozhao
```

### 运行限制

- 最大运行时间：1s
- 最大运行内存: 128M

## 答案：

```java
import java.util.LinkedList;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        // TODO 自动生成的方法存根
        LinkedList<String> b=new LinkedList<String>();
        LinkedList<String> b1=new LinkedList<String>();
      Scanner sc=new Scanner(System.in);
      int n=sc.nextInt();
      String c=sc.nextLine();
      String[] s=new String[n];
      for(int i=0;i<n;i++) {
          s[i]=sc.nextLine();
      }
      for(int i=0;i<n;i++) {
          String[] s1=s[i].split(" ");
          if(s1[0].equals("IN")&&s1[2].equals("N")) {
              b.add(s1[1]);
          }
          else if(s1[0].equals("IN")&&s1[2].equals("V")) {
              b1.add(s1[1]);
          }
          else if(s1[0].equals("OUT")&&s1[1].equals("N"))
              b.remove(0);
          else if(s1[0].equals("OUT")&&s1[1].equals("V"))
              b1.remove(0);
      }
      for(String s2:b1)
          System.out.println(s2);
      for(String s3:b)
          System.out.println(s3);
    }
}
```

## 题目2



小发明家弗里想创造一种新的语言，众所周知，发明一门语言是非常困难的，首先你就要克服一个困难就是，有大量的单词需要处理，现在弗里求助你帮他写一款程序，判断是否出现重复的两个单词。

### 输入描述

第 11 行，输入 N*N*，代表共计创造了多少个单词。

第 22 行至第 N+1*N*+1 行，输入 N*N* 个单词。

1\leq N \leq 10^41≤*N*≤104，保证字符串的总输入量不超过 10^6106。

### 输出描述

输出仅一行。若有重复的单词，就输出重复单词，没有重复单词，就输出 `NO`，多个重复单词输出最先出现的。

### 输入输出样例

#### 示例1

> 输入

```txt
6
1fagas 
dsafa32j
lkiuopybncv
hfgdjytr
cncxfg
sdhrest
```

> 输出

```txt
NO
```

#### 示例2

> 输入

```txt
5
sdfggfds
fgsdhsdf
dsfhsdhr
sdfhdfh
sdfggfds
```

> 输出

```text
sdfggfds
```

### 运行限制

- 最大运行时间：3s
- 最大运行内存: 512M

```java
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class Main {

    public static void main(String[] args) {
        // TODO 自动生成的方法存根
      Set <String> s = new HashSet <String>();
      Scanner sc = new Scanner(System.in);
      int n = sc.nextInt();
      String s1 = sc.nextLine();
      String[] b = new String[n];
      for(int i = 0;i < n;i++) {
        b[i] = sc.next();
        s.add(b[i]);
      }
     
      if(s.size() == n)
          System.out.println("NO");
      else {
         for(int i = 0;i < n;i++) {
             for(int j = i+1;j < n;j++) {
                 if(b[i].equals(b[j])){
                     System.out.println(b[j]);
             return;
           }
        }
          }
      }
    }

}
```

# 总结：

1、当要输入一个整数接下来要输入一个字符串时，要在输入整数后面加上一个sc.nextLine();来吸收回车符。

2、做题时要尽量的认真，读清题意后再开始做题，避免不需要的时间。

3、实在想不起来就歇歇，这样会有一个全新的思路。会事半功倍。

