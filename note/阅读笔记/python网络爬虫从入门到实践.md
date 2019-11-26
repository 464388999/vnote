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