# python网络爬虫从入门到实践
## 第一章网络爬虫入门
### 爬虫流程
获取网页>解析网页(提取数据)>存储数据 
获取网页：给网址发送请求，该网址会返回整个网页的数据
解析网页：从整个网页的数据中提取想要的数据
存储数据：将数据存储下来，可以存储在csv或数据库中。
### 技术实现
获取网页：
基础技术：requests、urllib和selenium
进阶技术：多进程多线程抓取、登录抓取、突破IP封禁和利用服务器抓取
解析网页：
基础技术：re正则表达式、BeautifulSoup和lxml
进阶技术：解决中文乱码
存储数据：
基础技术：存入txt文件和存入csv文件
进阶金属：存入MySQL数据库和MongoDB数据库
## 第二章编写第一个网络爬虫
### 常用数据类型
#### 字符串(string)
一般用来存储类似“句子”的数据，并放在单引号（'）或双引号（"）中。
```
string1 = 'Python Web Scraping'
string2 = "by Santos"
string3 = string1 + " " + string2
print (string3)
```
*Python Web Scraping by Santos*
#### 数字(number)
整数(int)和浮点数(float)，两种类型间可以相互转换。
```
int1 = 7
float1 = 7.5
trans_int = int(float1)
print (trans_int)
```
*7*
#### 列表(list)
列表能够包含任意种类的数据类型和任意数量。
```
list1 = ['Python','Web','Scrappy']
list2 = [1,2,3,4,5]
list3 = ["a",2,"c",4]
```
索引(从0开始)：
```
print("list1[0]:",list1[0])
print("list2[1:3]:",list2[1:3])
```
*list1[0]: Python
list2[1:3]: [2,3]*

修改值：
```
list1[1] = "new"
print (list1)
```
*['Python','new','Scrappy']*

添加值
```
list1.append("by Santos")
print (list1)
```
*['Python','new','Scrappy','by Santos']*
#### 字典(Dictionaries)
字典是一种可变容器模型，字典有“字”（直译为键值，key）和“值”（value），使用字典就像是自己创建一个字典和查字典的过程。每个存储的值都对应着一个键值key。key必须唯一，值不需要唯一，值可以取任何数据类型。
```
namebook = {"Name": "Alex", "Age": 7, "Class": "First"}
print (namebook["Name"]) #可以把相应的键值放入括号，提取值
print (namebook) #也可以直接输出整个字典
```
*Alex
{'Age': 7, 'Name': 'Alex', 'Class': 'First'}*

遍历访问字典中的每一个值：
```
#循环提取整个dictionary的key和value
for key,value in namebook.items():
    print (key,value)
```
*Class First
Age 7
Name Alex*
### 条件语句和循环语句
#### 条件语句
条件只有True和False两个值，当if判断条件成立时才执行后面的语句；当条件不成立时，执行else后面的语句。
```
book = "python" #定义字符串book
if book == "python": #判断变量是否为'python'
    print ("You are studying python.") #条件成立时输出
else:
    print ("wrong.") #条件不成立时输出
```
*You are studying python.*

如需判断多种条件，就需要用到elif
```
book = "java"
    if book == "python": #判断变量是否为'python'
        print ("You are studying python.") #条件成立时输出
    elif book == "java": #判断变量是否为'java'
        print ("You are studying java.") #条件成立时输出
    else:
        print ("wrong.") #条件不成立时输出
```
*You are studying java.*

条件语句注意不要缺少冒号(:)。
#### 循环语句
循环语句用来多次执行一个代码片段，分为for循环和while循环。
for循环能在一个给定的顺序下重复执行。
```
citylist = ["Beijing", "Shanghai", "Guangzhou"]
for eachcity in citylist:
       print (eachcity)
```
*Beijing
Shanghai
Guangzhou*

也可以使用range()进行循环,先用len(citylist)得到列表的长度为3，然后range(3)会输出列表[0,1,2],输出结果和上面相同。
```
citylist = ["Beijing", "Shanghai", "Guangzhou"]
for i in range(len(citylist)):
       print (citylist[i])
```
*Beijing
Shanghai
Guangzhou*

while循环能不断重复执行，只要满足一定条件。
```
count = 0
while count < 3:
    print (count) #打印出0,1,2
    count += 1 #与count = count + 1一样
```
*0
1
2*
### 函数
如果代码庞大复杂，可以定义一些函数(Functions)，使得代码易读，将代码切分成块，可以重复使用，并且容易调整顺序。
自带函数，如sum()和abs()，可以直接调用。
```
print (sum([1,2,3,4])) #对系列进行求和计算
print (abs(-1)) #返回数字的绝对值
```
*10
1*

自定义函数，函数包括输入和输出参数，某些函数输入和输出参数可以不用指明。
```
#定义函数
def calulus (x) :
    y = x + 1
    return y
#调用函数
result = calulus (2)
print (result)
```
*3*

参数必须要正确写入函数中，函数的参数也可以为多个，也可以是不同的数据类型，例如可以是两个参数，分别是字符串和列表型。
```
#定义函数
def fruit_function (fruit1, fruit2) :
    fruits = fruit1 + " " + fruit2[0] + " " +fruit2[1]
    return fruits
#调用函数
result = fruit_function("apple", ["banana", "orange"])
print (result)
```
*apple banana orange*

### 面向对象编程
面向对象编程
把函数进行分类和封装后放入对象中，使得开发更快、更强。
```
class Person:   # 创建类
    def __init__(self, name, age): #__init__()方法称为类的构造方法,注意左右都是两个下划线
        self.name = name
        self.age = age
    def detail(self): #通过self调用被封装的内容
        print (self.name)
        print (self.age)
obj1 = Person('santos', 18)
obj1.detail()  # Python将obj1传给self参数，即：obj1.detail(obj1)，此时内部self＝obj1
```
*santos
18*

函数式编程
```
def detail(name, age) :
    print (name)
    print (age)
obj1 = detail('santos', 18)
```
*santos
18*

使用函数式编程只需要写清楚输入输出变量并执行函数即可；使用面向对象的编程方法，首先要创建封装对象，然后通过对象调用呗封装的内容。
如果各个函数之间独立且无共用的数据，选用函数式编程；如果各个函数之间有一定的关联性，选用面向对象编程更好。
#### 封装
封装分为两步：
封装内容
调用被封装的内容
##### 封装内容
```
class Person: #创建类
    def __init__ (self, name, age):
        self.name = name
        self.age = age
    obj1 = Person('santos', 18)
#将"santos"和18分别封装到obj1及self的name和age属性
```
self在这为形式参数（即形参），当执行obj1 = Person('santos', 18)时，self等于obj1,此处将santos和18分别封装到obj1及self的name和age属性中。结果是obj1有name和age属性，其中name="santos",age=18。
##### 调用被封装的内容
调用被封装的内容时有两种方式：通过对象直接调用和通过self间接调用。
通过对象直接调用obj1对象的name和age属性:
```
class Person:
    def __init__ (self, name, age):
        self.name =name
        self.age = age
obj1 = Person ('santos', 18) #将"santos"及18分别封装到obj1及self的name和age属性
print (obj1.name) #直接调用obj1对象的name属性
print (obj1.age) #直接调用obj1对象的age属性
```
*santos
18*

通过self间接调用时，python默认会将obj1传送给self参数，即obj1.detail(obj1)。此时方法内部的self=obj1,即self.name='santos'，self.age=18：
```
class Person:
    def __init__ (self,name,age):
        self.name = name
        self.age = age
    def detail (self): #通过self调用被封装的内容
        print (self.name)
        print (self.age)
obj1 = Person('santos', 18)
obj1.detail() #python将obj1传递给self参数，即obj1.detail(obj1)，此时内部self=obj1
```
*santos
18*
#### 继承
继承是以普通的类为基础建立专门的类对象。子继承父的某些特性。
比如
猫可以：喵喵叫、吃、喝、拉、撒
狗可以：汪汪叫、吃、喝、拉、撒
分别为猫和狗创建类
```
#此为伪代码 无法执行
class 猫:
    def 喵喵叫(self):
        print ('喵喵叫')
    def 吃(self):
    # do something
    def 喝(self):
    # do something
    def 拉(self):
    # do something
    def 撒(self):
    # do something
class 狗:
    def 汪汪叫(self):
        print ('汪汪叫')
    def 吃(self):
    # do something
    def 喝(self):
    # do something
    def 拉(self):
    # do something
    def 撒(self):
    # do something
```
其中吃、喝、拉、撒是猫狗共同的特性，可以用继承的思想代替代码中的重复编写。
即
动物：吃喝拉撒
猫：喵喵叫
狗：汪汪叫
```
class Animal:
    def eat(self):
        print ("%s 吃 " %self.name)
    def drink(self):
        print ("%s 喝 " %self.name)
    def shit(self):
        print ("%s 拉 " %self.name)
    def pee(self):
        print ("%s 撒 " %self.name)
class Cat(Animal):
    def __init__ (self, name):
        self.name = name
    def cry(self):
        print ('喵喵叫')
class Dog(Animal):
    def __init__ (self, name):
        self.name = name
    def cry(self):
        print ('汪汪叫')
c1 = Cat('小白家的小黑猫')
c1.eat()
c1.cry()
d1 = Dog('胖子家的小瘦狗')
d1.eat()
d1.cry()
```
*小白家的小黑猫 吃 
喵喵叫
胖子家的小瘦狗 吃 
汪汪叫*
#### 错误处理
可以用try/except语句来捕获异常
```
try:
    result = 5/0 #除以0会产生运算错误
except Exception as e: #出现错误会执行except
    print (e) #把错误打印出来
```
*division by zero*

如果不想打印错误，可以使用pass空语句。
```
try:
    result = 5/0 #除以0会产生运算错误
except: #出现错误会执行except
    pass #空语句，不做任何事情
```
### 简单爬虫
获取页面
```
#!/usr/bin/python
# coding: utf-8
import requests #引入包requests
link = "http://www.santostang.com/" #定义link为目标网页地址
#定义请求头的浏览器代理，伪装成浏览器
headers = {'User-Agent' : 'Mozilla/5.0 (Windows; U; Windows NT6.1; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6'}
r = requests.get(link, headers= headers) #请求网页
print (r.text) #r.text是获取的网页内容代码
```
提取数据
```
#!/usr/bin/python
# coding: utf-8
import requests #引入包requests
from bs4 import BeautifulSoup
link = "http://santostang.com/" #定义link为目标网页地址
#定义请求头的浏览器代理，伪装成浏览器
headers = {'User-Agent' : 'Mozilla/5.0 (Windows; U; Windows NT6.1; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6'}
r = requests.get(link, headers= headers) #请求网页
soup = BeautifulSoup(r.text, "html.parser")#使用BeautifulSoup解析
#找到第一篇文章标题，定位到class是"post-title"的h1元素，提取a，提取a里面的字符串，strip()去除左右空格
title = soup.find("h1", class_="post-title") .a.text.strip()
print (title) #r.text是获取的网页内容代码
```
存储数据
```
#!/usr/bin/python
# coding: utf-8
import requests #引入包requests
from bs4 import BeautifulSoup
link = "http://santostang.com/" #定义link为目标网页地址
#定义请求头的浏览器代理，伪装成浏览器
headers = {'User-Agent' : 'Mozilla/5.0 (Windows; U; Windows NT6.1; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6'}
r = requests.get(link, headers= headers) #请求网页
soup = BeautifulSoup(r.text, "html.parser")#使用BeautifulSoup解析
#找到第一篇文章标题，定位到class是"post-title"的h1元素，提取a，提取a里面的字符串，strip()去除左右空格
title = soup.find("h1", class_="post-title") .a.text.strip()
print (title) #r.text是获取的网页内容代码
#打开一个空白的txt,然后使用f.write写入刚刚的字符串title
with open('title_test.txt',"a+") as f:
    f.write(title)
```
### 基础巩固
试题1:
划定范围,从最下的奇数往上增加，每次增加2。
```
count = 1
while count < 101:
    print (count)
    count = count + 2
```
参考答案：
用for循环，判断返回的是否是奇数，如果是则输出。
```
for i in range(1,101):
    if i % 2 == 1:
        print (i)
```
试题2：
纠结于将单个字符删除，并想着用for循环依次输出，想复杂了。
参考答案(1)：
使用str.replace()函数进行替换
```
str1 = '你好$$$我正在学Python@#@#现在需要&%&%&修改字符串'
str2 = str1.replace('$$$',' ').replace('@#@#',' ').replace('&%&%&',' ')
print (str2)
```
参考答案(2):
使用正则表达式
import re
str1 = '你好$$$我正在学Python@#@#现在需要&%&%&修改字符串'
str2 = re.sub('[$@#&%]+', ' ',str1)
print (str2)
试题3：
循环的嵌套使用
```
for j in range(1,10):
    for k in range(1,10):
        s = j * k
        print (j,'x',k,'=',s)
```
参考答案：
```
for i in range(1,10):
    for j in range(1,i+1):
        print ("%dx%d=%d\t" % (j, i, i*j), end="")
    print(" ")
```
试题4：
嵌套循环的使用，没做
参考答案(1)：
```
def calcute_profit(I):
    I = I / 10000
    if I <= 10:
        a = I * 0.1
        return a * 10000
    elif I <=20 and I > 10:
        b = 0.25 + I * 0.075
        return b * 10000
    elif I <=40 and I >20:
        c = 0.75 + I * 0.05
        return c * 10000
    elif I <=60 and I >40:
        d = 1.55 + I * 0.03
        return d *10000
    elif I <=100 and I > 60:
        e = 2.45 + I * 0.015
        return e * 10000
    else:
        f = 2.95 + I *0.01
        return f * 10000
I = int(input('净利润：'))
profit = calcute_profit(I)
print ('利润为%d元时，应发奖金总数为%d元' % (I, profit))
```
参考答案(2)：
```
def calcute_profit(I):
    arr = [1000000, 600000, 400000, 200000, 100000, 0]
    #这应该就是各个分界值，把它们放在列表里方便访问
    rat = [0.01,0.015,0.03,0.05,0.075,0.1]
    #这是各个分界值所对应的奖金比例值
    r = 0 #这是总奖金的初始值
    for idx in range(0, 6): #有6个分界，值当然要循环6次
        if I > arr[idx]:
            r = r + (I - arr[idx]) * rat[idx]
            I = arr[idx]
    return r
I = int(input('净利润:'))
profit = calcute_profit(I)
print ('利润为%d元时，应发奖金总数为%d元' % (I, profit))
```
试题5：
对字典进行排序，将字典转换为另一种方式进行排序。参考答案将其转换成元组列表表示排序。
参考答案：
```
import operator
x = {1:2,3:4,4:3,2:1,0:0}
sorted_x = sorted(x.items(), key=operator.itemgetter(1))
print (sorted_x)
```
*[(0, 0), (2, 1), (1, 2), (4, 3), (3, 4)]*
## 第三章静态网页抓取
