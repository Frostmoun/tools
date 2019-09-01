# 字符串
``````
## 转义字符
+ 用一个特殊的方法表示出一系列不方便写出的内容,比如回车键,换行键,退格键
- 借助反斜杠表示转义
- 不同系统对换行操作有不同表示
``````
```python
s = "Let's go'"
ss = 'Let\'s go'
s2 = "c:\\user"
s3 = "I want \r\n TV"
print(s)
```

``````
## 格式化
- 把字符串按照一定格式打印或者填充
- 格式化的两种方法
    - 利用百分号(%)
        - %d:整数占位符
        - %s:字符串占位符
    - 利用format函数
        - 直接用format函数进行格式化
        - 用{}和:代替%号,后面用format带参数完成  
``````
```python
s = "I am %s, i am %d years old"
print(s)
print(s%("Tang", 18))
s1 = "I am {0} years old, I love {1} and I am {0} years old".format(18, "game")
s2 = "I am {1} years old, I love {0} and I am {1} years old".format("game", 18)
print(s1)
print(s2)
```

## 内建函数
1. a
    - a1
    - > swdadadwaddsadada
    - > asdasdasdasdasdaddadddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddd
    - a2
2. b
3. c
> ## 这是一个标题。
> 
> 1.   这是第一行列表项。
> 2.   这是第二行列表项。
> 
> 给出一些例子代码：
> 
>       return shell_exec("echo $input | $markdown_script");


## 参数
#### 普通参数
#### 默认参数
#### 关键字参数
    - 不容易混淆,一般实参和形参只是按照位置一一对应即可,容易出错
    - 使用关键字参数, 可以不考虑参数位置
```python
# 关键字参数案例
def stu(name, age, addr):
    print("I am a student")
    print("我叫 {0}， 我今年 {1}岁了， 我住{2}".format(name, age, addr))
    
    
n = "jingjing"
a = 18
addr = "我家"

# 普通参数，只按照位置传递，容易出错
stu(a, n, addr)


def stu_key(name="No name", age=0, addr="No addr"):
    print("I am a student")
    print("我叫 {0}， 我今年 {1}岁了， 我住{2}".format(name, age, addr))
    
    
n = "jingjing"
a = 18
addr = "我家"

# 普通参数，只按照位置传递，容易出错
stu_key(age=a, name=n, addr=addr)
```

#### 收集参数
> - 把没有位置, 不能和定义时的参数位置相对应的参数,放入一个特定的数据结构中
> - 语法
>
>       def func(*args):
>           func_body
> - 参数名args可以改变,约定俗成这样写
> - 参数名args前需要有*
> - 收集参数可以和其他参数共存
```python
# 收集参数代码
# 函数模拟一个学生进行自我介绍，但具体内容不清楚
# args把他看做一个list
def stu( *args):
    print("Hello 大家好，我自我介绍以下，简答说两句：")
    # type函数作用是检测变量的类型
    print(type(args))
    for item in args:
        print(item)


stu("liuying", 18, "北京大通州区", "wangxiaojing", "single")

stu("周大神")
```
1.关键字收集参数
> - 把关键字参数按字典格式存入收集参数
> - 语法
>
>       def func(**kwargs):
>           func_body
> - kwargs约定俗成
> - 调用的时候,把多余的关键字参数放入kwargs
> - 访问kwargs需要按字典格式访问
```python
# 收集参数案例
# 自我介绍
# 调用的时候需要使用关键字参数调用
def stu( **kwargs):
    # 在函数体内对于kwargs的使用不用带星号
    print("Hello 大家好，我先自我介绍一下：")
    print(type(kwargs))
    # 对于字典的访问，python2 和python3有区别
    for k,v in kwargs.items():
        print(k, "---", v)
    
stu(name="liuying",  age=19, addr="北京大通州区", lover="王晓静", work="Teacher")

print("*" * 50)

stu(name="周大神")
```
2.收集参数混合调用的顺序问题
> - 收集参数,关键字参数,普通参数可以混合使用
> - 使用规则:普通参数和关键字参数优先
> - 定义的时候一般找普通参数,关键字参数,收集参数tuple,收集参数dict
```python
# 收集参数混合调用案例
# stu模拟一个学生的自我介绍
def stu(name, age, *args, hobby="没有", **kwargs):
    print("Hello 大家好")
    print("我叫 {0}， 我今年{1}大了。".format(name, age))
    if hobby == "没有":
        print("我没有爱好， so sorry")
    else:
        print("我的爱好是{0}".format(hobby))
        
    print("*" * 20)   
    
    for i in args:
        print(i)
    
    print("#" * 30)
    
    for k,v in kwargs.items():
        print(k, "---", v)
        
        
# 开始调用函数
name = "liuying"
age = 19


# 调用的不同格式
stu(name, age)

stu(name, age, hobby="游泳")

stu(name, age, "王晓静", "刘石头", hobby="游泳", hobby2="烹饪", hobby3="跟不同女生聊天")
```
3.收集参数的解包问题
> - 把参数放入list或者字典中,直接把list/dict中的值放入收集参数中
> - 对dict进行解包需要用两个**
> - 语法:参看案例
```python
# 收集参数的解包问题

def stu(*args):
    print("哈哈哈哈哈")
    # n 用来表示循环次数
    # 主要用来调试
    n = 0
    for i in args:
        print(type(i))
        print(n)
        n += 1
        print(i)
        
        
#stu("liuying", "liuxiaoyhing", 19, 200)

l = ["liuying", 19, 23, "wangxiaojing"]
 
#stu(l)
# 此时，args的表示形式是字典内一个list类型的元素，即 arg = (["liuying", 19, 23, "wangxiaojing"],)
# 很显然跟我们最初的想法违背


# 此时的调用，我们就需要解包符号，即调用的时候前面加一个星号
stu(*l)
```
4.返回值
> - 函数和过程的区别:有无返回值
> - 需要用return显示返回内容,如无返回值,则返回none
> - 推荐无论有无返回值,都以return结束
```python
# 返回值示例

def func_1():
    print("有返回值呀")
    return 1

def func_2():
    print("没有返回值")
     
    
f1 = func_1()
print(f1)

f2 = func_2()
print(f2)
```

5.函数文档
> - 函数文档的作用是对当前函数提供使用相关的参考信息
> - 写法:在函数内部开始的第一行使用三引号字符串定义符
> - 文档查看:使用help函数,如help(func);使用doc,如func.__doc__
```python
def stu(name, age):
    '''
    这是文档的文字内容
    :param name: 表示学生的姓名
    :param age: 表示学生的年龄
    :return: 此函数没有返回值
    '''
    pass


print(help(stu))

print("*" * 20)

print(stu.__doc__)
```
## 内置数据结构(变量类型)
> - list
> - set
> - dict
> - tuple ## list(列表)
> - 一组由顺序的数据的组合
> - 访问:使用下标操作(索引);列表的位置从0开始
> - 分片操作:对列表进行任意一段的截取
### List
```python
# 1, 创建空列表
l1 = []
# type是内置函数，负责打印出变量的类型
print(type(l1))
print(l1)

# 2. 创建带值的列表
l2 = [100]
print(type(l2))
print(l2)

# 3. 创建列表，带多个值
l3 = [2,3,1,4,6,4,6]
print(type(l3))
print(l3)

# 4. 使用list()
l4 = list()
print(type(l4))
print(l4)
# 分片操作
# 注意截取的范围，包含左边的下标值，不包含右边的下标值
print(l[1:4])

# 下标值可以为空，如果不写，左边下标值默认为0， 右边下标值为最大数加一，即表示截取到最后一个数据
print(l[:])
print(l[:4])
print(l[2:])
# 分片之负数下标
print(l)
# 下面显示的是为空，因为默认分片总是从左向右截取
# 即正常情况，分片左边的值一定小于右边的值
print(l[-2:-4])
print(l[-4:-2])
# 如果分片一定左边值比右边大，则步长参数需要使用负数
# 此案例为一个list直接正反颠倒提供了一种思路
print(l[-2:-4:-1])
```

```python
# del:删除命令
a = [1, 2, 3, 4, 5, 6]
del a[2]
print(a)

# 使用+连接两个列表,使用*相当于n个列表连接
b = ['a','b']
c = a + b
d = c * 2
print(b)
print(c)
print(d)
# in 和 not in
e = 2
f = 12
print(e in d)
print(f not in d)
```

```python
# 链表的遍历

a = [1, 2, 3, 4, 5, 6]
for i in a:
    print(i)

for i in range(1,10)
    print(i)
print(type(range(1,10)))

#双层列表循环
a = [["one", 1], ["two", 2], ["three", 3] ]
for k, v in a:
    print(k, "--", v)

# 双层列表循环变异
a = [["one", 1, "eins"], ["two", 2], ["three", 3,4,5,6,8] ]
for k, v in a:
    print(k, "--", v)

a = [["one", 1, "eins"], ["two", 2,"zwei"], ["three", 3,"drei"] ]
#这个例子说明，k，v,w的个数应该跟解包出来的变量个数一致
for k,v,w in a:
    print(k, "--", v, "--",w)

