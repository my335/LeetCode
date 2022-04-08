# 题目：

设有 n个人围坐在圆桌周围，现从某个位置 k上的人开始报数，报数到 m的人就站出来。下一个人，即原来的第 *m*+1 个位置上的人，又从 1开始报数，再报数到 m 的人站出来。依次重复下去，直到全部的人都站出来为止。试设计一个程序求出这 n个人的出列顺序。

![ss](https://doc.shiyanlou.com/courses/3993/1677054/940d7829aca843dd038abc9713837700-0)

要求一：采用循环链表解决。

要求二：可以使用模拟法，模拟循环链表。

要求三：可以不使用循环链表类的定义使用方式。

### 输入描述

输入只有一行且为用空格隔开的三个正整数 n,k,m其含义如上所述。

### 输出描述

共 n行，表示这 n 个人的出列顺序。

### 输入输出样例

#### 示例 1

> 输入

```txt
3 5 8
```

> 输出

```txt
3
2
1
```

### 运行限制

- 最大运行时间：1s
- 最大运行内存: 128M

# 我的答案：

```java
import java.util.LinkedList;
import java.util.Scanner;

public class 约瑟夫环 {

	public static void main(String[] args) {
		// TODO 自动生成的方法存根
         Scanner sc=new Scanner(System.in);
         LinkedList<Integer> s=new LinkedList<Integer>();
         int n=sc.nextInt();
         int k=sc.nextInt();
         int m=sc.nextInt();
         for(int i=k%n;i<=n;i++) {
        	 s.add(i);
         }
         for(int i=1;i<k%n;i++) {
        	 s.add(i);
         }
         int i=1;
         for(int j=0;true;j++) {
        	 int c=0;
        for(Object s1:s) {
        	if((int)s1!=0) {
        	if(i==m) {
        		System.out.println(s1);
                s.set(c, 0);
        		i=1;
        	}else {
        		i++;
        	}
        	if(s.size()==0)
        		return;
        }
        	c++;
        }
	}
	}

}
```

# 用循环链表答案：

```java
import java.util.Scanner;

public class 约瑟夫环
{
    static class Node
    {
        int val;
        Node next;
        Node(int v)
        {
            val = v;
        }
    } //成员类，代表节点，类似于C++语言中的结构体

    public static void main(String[] args)
    {

        int N, M, K; //n个人从k位置开始报数，数到m出列

        Scanner input = new Scanner(System.in);

        N = input.nextInt();

        K = input.nextInt();
        M = input.nextInt();
        
     
        Node t = new Node(1); //头节点单列出来，方便形成循环链表
        Node x = t;

        for (int i = 2; i <= N; i++)
            x = (x.next = new Node(i)); //建立单向链表
        x.next = t;                     //最后一个节点的next指向第一个节点，形成循环链表

        for (int i = 1; i <= K - 1; i++) //寻找报数的起点
            x = x.next;

        while (x != x.next)
        { //只剩下一个结点的时候停止
            for (int i = 1; i < M; i++) {
                x = x.next;
                // System.out.print(x.val+" ");
            }
            //此时x是将出列的节点的前一个节点
            System.out.println(x.next.val + " ");
            x.next = x.next.next;
        }
        System.out.println(x.val);
       
    }
}

```

# 总结：

- 在集合中用remove要注意，当集合中的元素减少时，减少元素的下面不会被读到（用foreach时）而且还会报错。如果用for，减少元素的下一个元素将不会被输出。尽量不要再循环中使用

- 循环链表的表示方式

  

```java
1、static class Node
    {
        int val;
        Node next;
        Node(int v)
        {
            val = v;
        }
    } //成员类，代表节点，类似于C++语言中的结构体
2、 Node t = new Node(1); //头节点单列出来，方便形成循环链表
        Node x = t;
3、 x = (x.next = new Node(i)); //建立单向链表

```

