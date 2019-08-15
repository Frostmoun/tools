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
