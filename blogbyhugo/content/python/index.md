---
title: "Python"
date: 2024-06-25T23:17:01+08:00
draft: false
lastmod:
tags: []
slug:
---

`/` 除 `//` 整除

- `bin` 转二进制
- `int` 转十进制
- `hex` 转16进制
- `oct` 转8进制

```
    ['技能1','技能2','技能3','技能4'][0]
    '技能1'
    ['技能1','技能2','技能3','技能4'][0:2]
    ['技能1','技能2']
```

单元素元组表示 (1,)   (1)会认为是数学运算符

-

### 序列

- str
- list
- tuple

### 切片

- [1,12,34][0:3]

```Python
    3 in [1,2,3,4,5]
    len([1,2,3,4,5])
    max([1,2,3,4,5])
    ord() asico码
```

##### 集合

{1,2,3,4}
 集合特性  不重复  不能用索引

```
{1,2,3,4,5} - {3,4} 差集
{1,2,3,4,5} & {3,4} 交集
{1,2,3,4,5} | {3,4，7} 并集
```

空的集合 定义 set()

值类型 ： int str tuple
引用类型：list set dict

-

>tuple list 区别

tuple 不可变

>== 与 is
is 判断内存地址

对象的三个特征 id,value,type
is, == , isinstance

位运算

- & 按位与
- | 按位或
- ^ 按位异或
- ~ 按位取反
- << 左移动
- >> 右移动

---
`not > and > or`

```Python
a=1 b=2 c=3
a or b and c   1    //and 优先级高于 or
```

a or b  返回 a 或 b的值  简写思路

```
#range实现间隔取数 ，python中切片更简洁
a = [1,2,3,4,5,6,7,8]

for i in range(0,len(a),2):
    print(a[i],end=' | ')

b = a[0:len(a):2]
print(b)
```

##### 模块

```
c7:
__all__ = ['a','b','c']
a = 2
b = 3
c = 4


import t.c7
from t.c7 import *
```

```
    设置递归限制次数
```

##### 函数

序列解包

```Python
    def damage(skill1,skill2)
        damage1 = skill1*2
        damage2 = skill2*3
        return damage1, damage2
        
    skill1_damage, skill2_damage = damage(3,6)
```

>1.必须参数
>2.关键字参数
>3.默认参数

<font color=red>必须参数</font>
    el:   add(x,y)

    关键字参数
    
    add(y=1,x=3)

##### 类

构造函数

```
    只能返回none
    def __init__(self，name,age):
        
```

```

class Student():
    name = ''
    age = 0
    sum1 = 0

    def __init__(self,name,age):
        self.name = name
        self.age = age
        print(age)
        print(name)
        #实例方法访问类变量的二种方法
        print(Student.sum1)
        print(self.__class__.sum1)  

    def showme(self):
        print(self.name + str(self.age))


student = Student('konan',26)
# student.name = 'konan'
student.showme()
```

```
    self.__score = score  __dict__中为 _Student__score
    student1.__score = -1 会动态添加
```

- 变量
  - 类变量
  - 实例变量
- 方法
  - 实例方法
  - 类方法
  - 静态方法
- 构造函数
- 成员可见性
- 面向对象3大特性
  - 继承性

```from b2 import Human

class Student(Human):
    def __init__(self,school,name,age):
        self.school = school
        Human.__init__(self,name,age)



student1 = Student('光明小学','konan',18)

print(student1.__dict__)
```

- 封装性
- 多态性

--

##### 正则表达式

index('python') > -1 判断是否存在

字符集
 [a-z]
 数量词
 [a-z]{3}

```
import re

a=  'c#|Objective-c|php|Python|'

result = re.findall('[A-Za-z-]{3,11}',a)

print(result)
```

默认是贪婪的
非贪婪 ？

---

```
import re

a=  'c#|Objective-c|php|Python|'

# ? 非贪婪
result = re.findall('[A-Za-z-]{3,11}?',a)

print(result)

# *前面的字符 0 或多次
# + 一次或多次
# ？0或1次  

b = 'pytho-python-pythonn'

#注意这里会返回3个，
result2 = re.findall('python?',b)


#边界匹配

qq = '100000000001'

r = re.findall('^\d{4,8}$',qq)


a2 = 'PythonPythonPythonPythonPython'
# 组
r2 =re.findall('(Python){3}',a2)
if  r2 :
    print('YES')
else:
    print('NO')
print(r2)

# 模式

#.匹配除换行符\n之外其他所有字符

a3 = 'Python|C#\n|PythonPythonPython'
# re.I 忽略大小写  re.S 所有字符
r3 =re.findall('(Python){3}',a2,re.I | re.S)

# sub方法 替换字符串

r4 = re.sub('C#','go',a3,0) # 0无限替换


a5 = 'Python|C#\n|PythonC#PythonC#Python'

def convert(value):
    matched = value.group()
    return '??' + matched + '??'
r5 = re.sub('C#',convert,a5)
print(r5)

# 重点 函数规则调用
s = 'A8C3721D86'
def convert(value):
    if int(value.group()) >= 6:
        return '9'
    else:
        return '0'

res = re.sub('\d',convert,s)

print(res)

# findall  match  search   span()  group()

# group 组概念
s2  = 'lift is short,i use python'
res2 = re.search('lift(.*)python',s2)
print(res2.group(1))
print(re.findall('lift(.*)python',s2))


s3  = 'lift is short,i use python,i love python'
res3 = re.search('lift(.*)python(.*)python',s3)
print(res3.group(0,1,2))
```

---

##### JSON

```
#序列化
json.dumps()

#反序列化
json.loads()
```

---

##### 枚举

`class VIP(Enum)`

```Python
from enum import Enum,unique
@unique
class VIP(Enum):
    GREEN = 1
    YELLOW = 2
    RED = 3
    RED_ALIAS = 3
#打印所有，包括别名
for v in VIP.__members__.items():
    print(v)
```

##### 闭包

```
def f1():
    y = 0
    def f2(value):
        nonlocal y
        y = y + value
        return y
    return f2

fun = f1()
print(fun(2))
print(fun(4))
```

```
# 匿名函数
#lambda x,y: x + y

#python中三元运算  
# x if x > y else y
```

###### 高级函数

>map函数
>
```Python
#map 函数
list_x = [1,2,3,4,5,6,7,8]
def square(x):
    return x * x
r = map(lambda x: x * x,list_x)
print(list(r))
```

>reduce函数
>
```Python
from functools import reduce
list_x = [1,2,3,4,5,6,7,8]
r = reduce(lambda x,y: x + y,list_x)
print(r)
```

>filter函数
>
```Python
list_x = [1,0,0,1,0,1]
r = filter(lambda x: x,list_x)
```

--

#### 装饰器

```
#装饰器
import time
def decorator(func):
    def wrapper(*args, **kw):
        print(time.time())
        func(*args,**kw)
    return wrapper

@decorator
def f1(name,age):
    print('this is f1' + name + age)

f1('konan','18')

@decorator
def test1(name, age , **kw):
    print(name + age)
    print(kw)

test1('konan','18',a=1,b=2,c=3)
```

-

#### 爬虫

```Python
from urllib import request
import re
import json

class Spider():
    url = 'https://www.panda.tv/cate/lol'
    root_reg = '<div class="video-info">([\\s\\S]*?)</div>'
    name_reg = '</i>([\\s\\S]*?)</span>'
    number_reg = '<span class="video-number">([\\s\\S]*?)</span>'
    def __fetch_content(self):
        r = request.urlopen(Spider.url)
        #bytes
        htmls = r.read()
        htmls =  str(htmls, encoding='utf-8')
        return self.__handle(htmls)
    

    def __handle(self, res):
        # 非贪婪
        result = re.findall(Spider.root_reg,res)
        
        anchors = []
        for html in result:
            name = re.findall(Spider.name_reg,html)
            
            # name =  name.strip()
            # name = re.sub('/(^\s*)|(\s*$)/g', "",name,0)
            number = re.findall(Spider.number_reg,html)
            anchor = {"name":name, "number":number}
            anchors.append(anchor)
        # print(json.dumps(anchors))
        return anchors
    
    def __refine(self, anchors):
        l = lambda anchor: {
            'name':anchor['name'][0].strip(),
            'number':anchor['number'][0]
        }
        return map(l,anchors)
    def __sort(self, anchors):
        anchors = sorted(anchors,key=self.__sort_seed, reverse=True)
        return anchors
    def __sort_seed(self, anchor):
        r = re.findall('\\d*',anchor['number'])
        number = float(r[0])
        if '万' in anchor['number']:
            number *= 10000
        return number
    def __show(self, anchors):
        for rank in range(0, len(anchors)):
            print('rank:  ' + str(rank + 1) + ' :  ' + anchors[rank]['name']+ '  ' + anchors[rank]['number'])
    def go(self):
        anchors = self.__fetch_content()
        anchors = list(self.__refine(anchors))
        anchors = self.__sort(anchors)
        self.__show(anchors)
        # print(json.dumps(anchors))

spider = Spider()
spider.go()

# a=  'c#|Objective-c|php|Python|'

# # ? 非贪婪
# result = re.findall('[A-Za-z-]{3,11}?',a)

# print(result)

# <div class="video-info">
#                       <span class="video-title" title="（接包天）一些小小的黑科技">（接包天）一些小小的黑科技</span>
#                                             <span class="video-nickname" title="阿枫丶丶丶">
#                                                                         <i class="icon-host-level icon-host-level-6" data-level="6"></i>
#                                                                         阿枫丶丶丶                      </span>
#                                             <span class="video-number">2748</span>
#                                             <span class="video-station-info">
#                         <i class="video-station-num">3人</i>
#                                                </span>
#                                           </div>
```

---

## 总结

- BeautifulSoup
- Scrapy
- 爬虫、反爬虫、反反爬虫
- 代理IP库

-

## 杂记

`列表推导式`

```Python
a = (1,2,3,4,5,6,7,8)
b = (i**2 for i in a if i>5)
```

```Python
student = {
    'hahh': 12,
    'fdgh':23,
    'fsdg':34
}
# 取出字典所有key
b = [key for key,value in student.items()]
```

判断空值

```
if not a

而非 if a is None
```
