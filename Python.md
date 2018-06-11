#  Python

## 一 、基础

   python: 理论上科学计算、图形化开发、系统脚本、web服务器、网络爬虫、服务器集群自动化运维

   sublime :  http://www.sublimetext.com/3

### 1.1 基本类型、语法

          ~~~~
- 大小写区分
- int一样，地址也是一样的；
- 变量引用计数；
- 当引用变量为0的时候，内存自动管理回收；
- del可以直接释放资源，变量名删除，引用计数减一；
   意思：在python中如果已经为10值a,b=10的时候也是引用这个地址，只不过引用计数加一；俩是一个地址；
          ~~~~

~~~~python
 # 例子如下：
# coding: UTF-8  #中文=====
print("我我!")
a =123
b =123 
print(id(a))
print(id(b))
print(type(a)) 
---结果----------
31188288
31188288
<type 'int'>

---------------------------------
python没有{}，都是通过缩进表示代码块的关系；
def add(x,y):
	z=x+y
	return z
res = add(200,60)
print(res) 
~~~~

常用表达式

~~~~
算数表达式
    + - **取幂 *乘号 /除  a//b除取整数  a%b除取余
逻辑表达式
    not a  /   a and b  / a or b 
    a is b (a和b是一个对象)  | a is not b (a和b不是一个对象)
关系表达式
    ==    != / <>      >    <   >= <=
位运算
    -a
    a  << n     a>>n  a右移n位
    a & b    按位取与    a | b  a和b按位取或
    a^b   a和b按位异或
    
~~~~

### 1.2  常见语法

if  for

~~~~
if-else
   if condition:
   		
   else
   		
----------
if-elif-else
    if condition:
    	...
    elif condition:
     	...
    else:
        ...
===========
  while condition:
  		...
============
   for var in sequence:
  break continue 含义不变 
~~~~

### 1.2.3 列表、元祖、数组

~~~python
1） 列表 []  元素可以加等修改，可以存任意数据类型
list1=["ab","de","cq","de"]
list2=[12,34,56]
list1.append( 123) # 1.列表可以存任意数据类型
list1.append(list2) 
list1=  list1 + ["dsds","sdsd"]  # 2. + 列表可以直接加列表
------result:----------------
['ab', 'de', 'cq', 'de', 123, [12, 34, 56], 'dsds', 'sdsd']
print(list1[0:2])  # 获取前三个元素 
print(list1[-2])   # 获取倒数第二个元素
print(len(list1))  # 列表长度  
print(2*list1)     #  * ->列表元素重复N倍
print('c' in list1) #  元素是否存在列表中
列表中的函数
print(cmp(list1,list2))  # false ; 比较元素是都一样
print(max(list2) )       # 获取最大值  
print(list1.count("ab")) #元素出现的次数
list1.append("cmdss")   #列表队尾加元素
list1.extend(list2)     #列表末尾加其他序列 
list1.pop()                #移除队列的最后一个元素
list1.remove("de")         #移除列表指定元素
list1.sort()              #排序
-----------------------------------------------------
2）元祖：() 元祖不能修改 =相当于是const修饰的列表
t =(1,2,3,6,"sdh")
二维元祖：
t1 =[(1,2),(4,5)]
-----------------------------------------------------
3）字典：{}  key-value  ，相当于java的map json
dict = {'alic':'A+','grade':123,'className':'slksd'}
print(dict['grade'])
print(dict.keys())
print(dict.values())
----result:-----------
 123
['grade', 'className', 'alic']
[123, 'slksd', 'A+']  

dict1={('test','hai'):'1232312',"dskjdsk":"23232",123232:"dsljdsl","other":{"val":"kdssd"}}
dict1['dskjdsk']='true'
dict1.clear()

dict2 ={['23','45']:"w3232"}#报错 、：不能以list作为字典的key


dict2 ={"key1":{"name":"xi","class":5},"friends":["Bob","holla"],"normal":1}
dict0=dict2  
dict3 =dict2.copy() #浅复制
print( id(dict2)) 
print( id(dict0))  # 引用地址跟dict2完全一样
print( id(dict3))
--------
30956536
30956536
38951368 
dict2["normal"]=0 # dict0跟着dict2一起变；dict3是浅复制，复制的是最外层的值，dict2值变，不会影响dict3
print("-----------")
print(dict2)
print(dict0)
print(dict3)
-----------
{'key1': {'name': 'xi', 'class': 5}, 'friends': ['Bob', 'holla'], 'normal': 0}
{'key1': {'name': 'xi', 'class': 5}, 'friends': ['Bob', 'holla'], 'normal': 0}
{'key1': {'name': 'xi', 'class': 5}, 'friends': ['Bob', 'holla'], 'normal': 1}
------------
dict2['friends'].append("morany")   #dict0跟着dict2一起变是正常的；
dict2['key1']['name']='zhang' 
# 而dict3是浅复制，对于子对象只是复制了其引用地址，key1和friends相当于是有俩地址指向它们，
# 所以dict2变的时候，dict3中的俩地址指向是一块内容，也会跟着变 
print(dict2)
print(dict0)
print(dict3)
---------------
{'key1': {'name': 'zhang', 'class': 5}, 'friends': ['Bob', 'holla', 'morany'], 'normal': 0}
{'key1': {'name': 'zhang', 'class': 5}, 'friends': ['Bob', 'holla', 'morany'], 'normal': 0}
{'key1': {'name': 'zhang', 'class': 5}, 'friends': ['Bob', 'holla', 'morany'], 'normal': 1}
---------------
dictmm = dict2.fromkeys( dict2)  # 根据已有的字典创建相同结构的字典
print(dictmm)
dictm2 = dict2.fromkeys(("class","fds")) #创建时指定key
print(dictm2)
---------
{'key1': None, 'friends': None, 'normal': None}
{'fds': None, 'class': None}

~~~

### 1.2.4 字符串以及特殊函数

