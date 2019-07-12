### 标题

signal函数的解析
void (*signal(int sig, void (*func)(int)))(int)

---

### 时间

2017-6-7

---

### 内容

1.可以把函数先转化成看得懂的形式
void(*)(int) signal(int sig,void (*func)(int))
它是一个返回void(*)(int)函数指针的一个函数
typedef void(*handle)(int)
于是原函数就变成了
handle signal(int sig,handle h)
2.按照从里到外，从右到左分析式子
signal右边是括号，表明它是函数
左边是*号，表明它的返回值是指针，是返回一个指针的函数
右边是括号，表明是函数，是返回一个指向有一个参数的函数的指针的函数
左边是void，表明返回值为空，是返回一个指向返回void有一个参数的函数的指针的函数

---

### 注释



---

### 获取路径

http://learn.jser.com/cprogramming/c-function-signal.html

---

### 其他

typedef 定义一个类型
int a ：定义一个变量a
typedef int a ：定义一个类型a
void (*fun)() ：定义一个函数fun
typedef void(*fun)() :定义一个函数类型fun

---





