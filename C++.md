# C++

[TOC]





## 入门与基本概念

### (一)书写Hello World

```c++
#include<iostream>
using namespace std;

int main()
{
	cout << "hello world" << endl;
	system("pause");
	return 0;
}
```

### （二）注释

单行注释：//; 多行注释：/*

### （三）关键字

![image-20210611102939145](C:\Users\huawei\AppData\Roaming\Typora\typora-user-images\image-20210611102939145.png)

### （四）数据类型

#### 浮点型 float double

```c++
//默认情况下，输出一个小数会显示6位有效数字
float f1 = 3.14f;//(否则默认为双精度)
double d1 = 3.14;
//科学计数法
float f2 =3e2;//3*10^2
float f3 =3e-2;//3*0.1^2

```

#### 字符型：

char 单个字符 使用单引号‘ ’

ASCLL:    a-97 A-65

可以用ascll码给字符赋值

#### 转义字符

作用：用于显示一些不能显示出来的ASCLL字符

```c++
//换行符：\n
//反斜杠：\\
//水平制表符：\t 8个a 可以整齐输出数据

```

#### 字符串型

C风格字符串：

```c++
char str[] = "hello world";//双引号
cout << "hello world"<<endl;
```

C++风格字符串：

```c++
//包含一个头文件 #include<string>
string str2 = "hello world";
cout<< str2<<endl;
```

### （五）数据的输入

作用：用于从键盘中获取数据

关键字：cin

```c++
//整型
int a =0;
cout << "请给整型变量a赋值："<<endl
cin >> a;

```

### （六）运算符

#### 逻辑运算符

| 运算符 | 术语 | 示例   | 结果               |
| ------ | ---- | ------ | ------------------ |
| ！     | 非   | ！a    | 真即是假，假即为真 |
| &&     | 与   | a&&b   | 都为真才为真       |
| \|\|   | 或   | a\|\|b | 有一个为真就为真   |

### 6.程序流程结构

#### 6.1选择结构

##### 6.1.1  if语句 

单行if

```c++
if()
{
    
}
```

多行if

```c++
if()
{
}
else
{
}
```

多条件if

```c++
if()
{
}
else if()
{
}
else
{
}
```

嵌套if语句

```c++
	int score = 0;
	cout << "请输入高考考试分数" << endl;
	cin >> score;
	if (score > 600)
	{
		cout << "一本" << endl;
		if (score > 700)
		{
			cout << "宁能考入清华大学" << endl;
		}
	}
	else
	{
		cout << "未考入一本" << endl;
	}
```

#### 6.2选择结构

##### 6.2.1三目运算符

​	//三目运算符返回的是变量，可以继续赋值

```c++
	int a = 10;
	int b = 20;
	int c = 0;
	c = (a > b ? a : b);
	cout << "c=" << c << endl;
	//三目运算符返回的是变量，可以继续赋值
	(a > b ? a : b) = 100;
	cout << "a=" << a << endl;
	cout << "b=" << b << endl;
	cout << "c=" << c << endl;
```

##### 6.2.2  switch语句

1.只能是整型或者字符型，不可是一个区间

#### 6.3 循环结构

##### 6.3.1 while

猜数字

```c++
#include<iostream>
using namespace std;
//time系统时间头文件包含
int main()
{
	//添加随机数种子 利用当前
	srand((unsigned int)time(NULL));
	//系统生成随机数
	int num = rand() % 100 + 1;
	cout << num << endl;
	//玩家进行猜测
	int val = 0;
	while (1)
	{
		cin >> val;
		if (val > num)
		{
			cout << "猜测过大" << endl;
		}
		else if (val < num)
		{
			cout << "猜测过小" << endl;
		}
		else
		{
			cout << "恭喜您猜对了" << endl;
			break;
		}
	}

	system("pause");
	return 0;
}
```

##### 6.3.2 do...while循环语句

```c++
do...while和while循环区别在于
```

##### 6.3.3 for嵌套循环

乘法口诀表

```c++
#include<iostream>
using namespace std;
//time系统时间头文件包含
int main()
{
	//乘法口诀表
	for (int i = 1; i <= 9; i++)
	{
		//cout << i << endl;
		for (int j=1;j<=i;j++)
		{
			cout <<  j << "*" << i << "=" << i * j <<" ";
		}
		cout << endl;
	}

	system("pause");
	return 0;
}
```

#### 6.4 跳转结构

##### 6.4.1 go to 语句

```C++
goto FLAG;

FLAG:
```

### 7.数组

#### 7.1一维数组

数组名用途：

1.统计整个数组在内存中的总长度；  sideof(arr)

2.获取数组在内存中的首地址；cout<<arr<<endl

(int)arr 可强制转换十六进制地址值为整型输出

若出错原因为：该地址的整数形式远大于int类型的取值范围；解决办法为：把(int)改为(long long)

```c++
#include<iostream>
using namespace std;
//time系统时间头文件包含
int main()
{
	int arr[5] = { 1,3,2,5,4 };
	cout << "数组逆置前：" << endl;
	for (int i = 0; i < 5; i++)
	{
		cout << arr[i] << endl;
	}
	int start = 0;
	int end = sizeof(arr) / sizeof(arr[0]) - 1;
	while (start < end)
	{
		int temp = arr[start];
		arr[start] = arr[end];
		arr[end] = temp;
		start++;
		end--;
	}
	cout << "数组逆置后：" << endl;
	for (int i = 0; i < 5; i++)
	{
		cout << arr[i] << endl;
	}

	system("pause");
	return 0;
}
```

#### 7.2冒泡排序

![image-20210617214942536](C:\Users\huawei\AppData\Roaming\Typora\typora-user-images\image-20210617214942536.png)

![image-20210617215000214](C:\Users\huawei\AppData\Roaming\Typora\typora-user-images\image-20210617215000214.png)

#### 7.3 二维数组

![image-20210617215350080](C:\Users\huawei\AppData\Roaming\Typora\typora-user-images\image-20210617215350080.png)

 二维数组定义方式

```c++

	//1.数组名[行数][列数]
	int arr[2][3];
	arr[0][0] = 1;
	arr[0][1] = 2;
	arr[0][2] = 3;
	arr[0][3] = 4;
	arr[0][4] = 5;
	arr[0][5] = 6;
	//两层嵌套for循环
	//外层循环打印行，内层循环打印列
```

```c++
	//2.数据名[行数][列数]={{数据1，数据2}，(数据3，数据4)}
	int arr2[2][3] =
	{
		{1,2,3},
		{4,5,6}
	};
```

```c++
	//3.数组名[行数][列数]={数据1，数据2，数据3，数据4}
	int arr2[2][3]={1，2，3，4，5，6}；
```

```c++
	//4.数组名[][列数]={数据1，数据2，数据3，数据4}
     int arr2[][3]={1，2，3，4，5，6}；

```

### 8.函数

#### 8.1 值传递

形参值的改变不会改变实参

#### 8.2 函数的分文件编写

1.创建.h后缀名的头文件;

2.创建.cpp后缀名的源文件；

3.在头文件中写函数的声明；

4.在源文件中写函数的定义；

### 9. 指针

指针所占内存：32位4个字节，64位8个字节

#### 9.1空指针

```c++
//空指针用于给指针变量进行初始化
int *p=NULL;
//空指针不可进行访问

```

#### 9.2野指针

```c++
//野指针
int *p=(int*)0x1100;
```

野指针和空指针都不是申请的空间不可访问

#### 9.3const修饰指针

三种情况

1.常量指针：

指针的指向可以修改，指针指向的值不可以修改

```c++
1.const修饰指针——常量指针
    const int *p=&a;
```

2.指针常量：

指针的指向不可以修改，指针指向的值可以改

```c++
2.const修饰常量——指针常量
    int *const p=&a;
```

3.既修饰指针，又修饰常量：

指针的指向和指针指向的值都不可以修改

```c++
3.const修饰指针和常量
const int const *p;
```

#### 9.4指针和数组

```c++
//利用指针访问数组中的元素
int arr[10]={1,2,3,4,5,6,7,8,9,10};
int *p=arr;
cout<<"第一个元素"<<*p<<endl;
p++;//让指针向后偏移4个字节
cout<<"第二个元素"<<*p<<endl;
```

#### 9.5指针和函数

```c++
//实现两个数字进行交换
//值传递
void swap01(inta,intb)
{
    int temp=a;
    a=b;
    b=temp;
}
//地址传递
void swap02(int* p1,int* p2)
{
    int temp=*p1;
    *p1=*p2;
    *p2=temp;
}
int main()
{
    int a=10;
    int b=20;
    //值传递不会改变实参
    swap01(a,b);
    //地址传递会改变实参
    swap02(&a,&b);
}
```

#### 9.6指针，数组，函数

### 10.结构体

结构体创建变量时Struct可以省略

#### 10.1结构体数组

#### 10.2结构体指针

```c++
struct student
{
    string name;
    int age;
    int score;
};
int main()
{
    //创建学生结构体变量
    student s={"张三"，18，100}；
    //通过指针指向结构体变量
     student *p=&s;
    //通过指针访问
    p->name
}
```

#### 10.3结构体做函数参数

```c++
struct student
{
    string name;
    int age;
    int score;
};
//1.值传递
void printStudent1(struct student s)
{
    cout<<s.name<<endl;
}
//2.地址传递
//形参为指针，可减少占用内存空间，不会拷贝出一个副本
void printStudent2(struct student *p)
{
    cout<<p->name<<endl;
}
int main()
{
    struct student s;
    s.name=
    s.age=
    s.score=
    //值传递
    printStudent1(s);
    //地址传递
    printStudent2(&s);
        
}
```

