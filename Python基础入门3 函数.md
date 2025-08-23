程序的三大结构：顺序结构、选择结构、循环结构



程序的第三大结构是循环结构。在此结构中，通过一个判断语句来循环执行一个代码块，直到判断语句为假时跳出循环。循环语句分为**while循环、for循环、循环嵌套和迭代器。**循环语句中有一个语句`break`，通过这个语句可以**跳出整个循环**。

1. ### while

   while语句的基本形式为：

   ```
   while 判断条件1：
       循环语句
   ```

   当判断条件1为true时，执行循环语句，直到判断条件1为假。例如：

   ```
   count = 0
   while(count <= 10):
       print("现在计数为:",count)
       count += 1
   ```

   - 输入while True:  代表 无限循环开始。当条件为"真"时循环 → 而 `True` 永远为真，所以会**一直循环**。创建一个"无限循环"，直到内部用 `break` 主动终止。

2. ### break

   ```
   while 判断条件1：
       循环语句
       判断条件2：
       break
   ```

   当判断条件1为true时执行循环语句。若此时判断条件2为true，执行break跳出while循环，若判断条件2一直为false，则执行while循环，一直到判断条件1为false。
   例如：

   ```
   count = 0
   while(count <= 10):
       print("现在计数为:",count)
       count += 1
       if(count > 5):
           break
   ```

3. ### for 循环

**for循环可以遍历序列成员**，直到序列中的成员全部都遍历完后才跳出循环。循环语句中有一个**continue**语句，这个语句的作用是**跳出当前循环。**

for语句的基本形式为：

```
for iteration_var in sequence:
    循环语句
```

依次遍历序列中的成员，执行循环语句。例如：

```
list = ['python','java','c','c++']
for book in list:
    print("当前书籍为:",book)
```

4. ### continue 语句

   ```
   for iteration_var in sequence:
       循环语句
       if 判断语句1：
       continue
   ```

当遍历序列时，如果判断语句1为真，则执行continue语句，跳出当前循环，直接进入下一次循环。例如：

```
list = ['python','java','c','c++']
count = 0
for book in list:
    count += 1
    if count == 3:
        continue
    print("当前书籍为:",book)
```

5. ### 循环嵌套

- #### for循环嵌套
  for循环嵌套的基本形式为：

```
for iteration_var in sequence:
    for iteration_var in sequence:
        循环语句
```

例如：

```
for x in range(1,10):
    for y in range(0,x):
        result = x + y
        print(result)
```

- #### while循环嵌套
  while循环嵌套的基本形式为：

  ```
  while 判断条件：
  	while 判断条件：
            循环语句
  ```

  例如：

  ```
  x = 1
  y = 0
  while x < 10:
      while y < x:
          result = x + y
          print(result)
          y += 1
      x += 1
      y = 0
  ```

  

6. ### 迭代器（Iterator）

   迭代器用来循环访问一系列元素，它不仅可以迭代序列，也可以迭代不是序列但是表现出序列行为的对象。

   #### 迭代器的优点
   - 迭代器访问与for循环访问非常相似，但是也有不同之处。对于支持随机访问的数据结构如元组和列表，迭代器并无优势。因为迭代器在访问的时候会丢失数据索引值，但是如果遇到无法随机访问的数据结构如集合时，迭代器是唯一访问元素的方式；

   - 迭代器仅仅在访问到某个元素时才使用该元素。在这之前，元素可以不存在，所以迭代器很适用于迭代一些无法预先知道元素总数的巨大的集合；

   - 迭代器提供了一个统一的访问集合的接口，定义**`iter()`**方法对象，就可以使用迭代器访问。

   【判断是否为可迭代对象】可直接作用于for循环的数据类型如list、tuple、dict等统称为可迭代对象:`Iterable`。**使用isinstance()可以判断一个对象是否是可迭代对象。**

   ```
   from collections import Iterable
   result = isinstance([],Iterable)
   print(result)
   result = isinstance((),Iterable)
   print(result)
   result = isinstance('python',Iterable)
   print(result)
   result = isinstance(213,Iterable)
   print(result)
   ```

   结果为：

   True
   True
   True
   False

   可以被**`next()函数`**调用并不断返回下一个值的对象称为迭代器:`Iterator`。next()函数访问每一个对象，直到对象访问完毕，返回一个StopIteration异常。

   

   **使用isinstance()可以判断一个对象是否是Iterator对象。**例如：

   ```
   from collections import Iterator
   result = isinstance([],Iterator)
   print(result)
   result = isinstance((),Iterator)
   print(result)
   result = isinstance((x for x in range(10)),Iterator)
   print(result)
   ```

   结果为：

   False

   False

   True

   #### 定义迭代器

   当自己定义迭代器时，需要定义一个类（class）。类里面包含一个`__iter__()`函数，这个函数能够返回一个带`__next__()`方法的对象。例如：

   ```
   class MyIterable:
       def __iter__(self):
           return MyIterator()
   class MyIterator:
       def init(self):
           self.num = 0
       def __next__(self):
           self.num += 1
           if self.num >= 10:
               raise StopIteration
           return self.num
   ```

   #### 复制迭代器

   迭代器当一次迭代完毕后就结束了，再次调用便会引发StopIteration异常。

   如果想要将迭代器保存起来，可以使用复制的方法:`copy.deepcopy():x = copy.deepcopy(y)`，不可使用赋值的方法，这样是不起作用的。

7. ### 顺序结构

8. ### 选择结构

- #### if-else语句

  基本形式为：

  ```
  if 判断语句1：
      step1
  else:
      step2
  ```

  当判断语句1为真时，执行step1，否则执行step2。例如：

  ```
  name = 'choose'
  #判断变量name是否为'choose'
  if name == 'choose':
      print("条件成立")
  else:
      print("条件不成立")
  ```

- #### if-elif-else 语句

  当判断条件有多个时，使用elif语句，基本形式为：

  ```
  if 判断语句1：  
     step1  
  elif 判断语句2：  
     step2  
  elif 判断语句3：  
     step3  
  ……
  else:  
     step
  ```

  当判断语句1为真时，执行step1，当判断语句1为假、判断语句2为真时执行step2，……，最后判断语句都为假时执行step。例如:

  ```
  userId = 43
  #判断员工号
  if userId == 10:
      print("这是10号员工")
  elif userId == 22:
      print("这是22号员工")
  elif userId == 18:
      print("这是18号员工")
  else:
      print("员工ID为:",userId)
  ```

- #### 三元操作符

  三元操作符也是根据条件判断执行哪一个代码块，但它的最大特点是不需要像if-else语句那样写多行代码，而是只需一行代码。

  三元操作符的基本格式为：

  ```
  result = x if x < y else y
  ```

  其中，x < y为判断语句。若x < y为真则result = x，否则result = y。

9. ### 内置函数

- #### 数学运算

  **abs()：**返回数值的绝对值，例如：

  ```
  abs(-4)
  输出：4
  ```

  **divmod()：**返回两个数值的商和余数，例如：

  ```
  divmod(7,2)
  输出：(3,1)
  ```

  **max()：**返回元素中的最大值，例如：

  ```
  max(2,6,1,7)
  输出：7
  ```

  **min()：**返回元素中的最小值，例如：

  ```
  min(2,6,1,7)
  输出：1
  ```

  **sum()：**返回传入元素之和，例如：

  ```
  sum((1,2,3,4))
  输出：10
  sum([1,2,3,4])
  输出：10
  sum((1,2,3,4),-10)
  输出：0
  ```

- #### 类型转换

  **bool()：**根据传入的参数的逻辑值创建一个新的布尔值，例如：

  ```
  bool()
  输出：False
  bool(1)
  输出：True
  bool(0)
  输出：False
  bool('str')
  输出：True
  ```

  **int()：**根据传入的参数创建一个新的整数；

  **float()：**根据传入的参数创建一个新的浮点数，例如：（不提供参数，返回0.0）

  **complex()：**根据传入的参数创建一个新的复数，例如：（两个参数都不提供时，返回0j）

  ```
  complex()   
  输出：0j
  complex('2+4j')
  输出：(2+4j)
  complex(1,2)
  输出：(1+2j)
  ```

  

- #### 序列操作

  **all()：**判断可迭代对象的每个元素是否都为True值，例如：【与】

  ```
  >>> all([1,2,3])     # 列表中每个元素逻辑值均为True，返回True
  True
  >>> all([0,1,2])     # 列表中0的逻辑值为False，返回False
  False
  >>> all(())     # 空元组
  True
  ```

  **any()：**判断可迭代对象的元素是否有为True值的元素，例如：【或】

  ```
  >>> any([0,1,2])     # 列表元素有一个为True，则返回True
  True
  >>> any([0,0])     # 列表元素全部为False，则返回False
  False
  >>> any([])     # 空列表
  False
  ```

  **sorted()：**对可迭代对象进行排序，返回一个新的列表。例如：

  ```
  >>> a = ['a','b','d','c','B','A']
  >>> a
  ['a', 'b', 'd', 'c', 'B', 'A']
  >>> sorted(a)     # 默认按字符ascii码排序
  ['A', 'B', 'a', 'b', 'c', 'd']
  ```

  

- #### 文件操作

  **open()：**使用指定的模式和编码打开文件，返回文件读写对象。例如：

  ```
  # t为文本读写，b为二进制读写
  >>> a = open('test.txt','rt')
  >>> a.read()
  some text
  >>> a.close()
  ```

10. #### 调用函数

- 我们要在调用函数时，需要正确调用函数的名称和参数，例如我们定义了一个加法函数：

```
def plus(a,b):
    return a+b
```

我们在调用`plus()函数`时，如果传入的参数类型不对，会报`TypeError`错误。而且有时我们传入的参数类型不是规定类型的话，就算调用函数运行结果没有报错，也会产生逻辑错误。例如：

```
# 定义plus函数，作用是求两个正整数之和
def plus(a,b):
    return a+b
# 调用plus函数，参数类型为'1','2'
print(plus('1','2'))
```

输出：12

虽然上述例子的程序运行结果没有报错，但是结果却**与我们的预期不符**，因为我们的本意是调用plus()函数实现两个整数的加法。

但是如果我们传入的是字符串类型的数值时，结果就是两个字符串的拼接。**所以一定要注意传入参数的类型。**

当我们传入正常类型的参数时，传入的参数个数不一致时，也会报`TypeError`错误。例如：

```
# 定义plus函数，作用是求两个正整数之和
def plus(a,b):
    return a+b
# 调用plus函数，参数为1,2,3
print(plus(1,2,3))
```

结果报错：`TypeError: plus() takes 2 positional arguments but 3 were given`

因为plus()函数允许有且仅有2个参数，但是却在调用时传入了3个参数，所以程序报错。

11. ### 模块（Module）

    在 Python 程序的开发过程中，为了代码维护的方便，我们可以把函数进行分组，分别放到不同的.py文件里。这样，每个文件包含的代码就相对较少，这个.py文件就称之为一个模块（Module）。

    模块能够让我们有逻辑地组织 Python 代码段，模块中能够定义函数、类和变量，模块里也可以包含可执行的代码。

    #### **引入模块**

    1. **import 模块名**

    **`模块名.函数名`**这种调用方式可以避免特殊情况的发生。引入模块的时候，**调用函数必须加上模块名**，防止重名:

    **`import math`**

    **`print(math.fabs(-2))`**

    2. **from 模块名 import 函数名1, 函数名2...**

    通过这种方式导入函数的时候，**调用函数时就只能给出函数名**，而不能给出模块名。

    如果想**一次性引入模块math中所有的函数**，可以通过如下方式导入：

    **`from math import *`**  

    #### 自定义模块

    每个 Python 文件都可以看作一个模块，模块的名字就是 Python 文件的名字。所以我们完全可以自己写一个 Python 文件，作为自己定义的模块。例如，我们编写了my_module.py文件，里面定义了plus()函数：

    ```
    # my_module.py
    def plus(a,b):
        return a+b
    ```

    之后我们就可以在其他 Python 文件中先引入my_module，然后通过my_module.plus(a,b)来调用my_module.py文件中的plus()函数。我们也可以直接通过from my_module import plus来导入plus()函数。

12. ### Python内置模块

    1. **os模块**：文件和目录，用于提供系统级别的操作；
    2. **sys模块**：用于提供对解释器相关的操作；
    3. **json模块**：处理JSON字符串；
    4. **logging**: 用于便捷记录日志且线程安全的模块；
    5. **time&datetime模块**：时间相关的操作，时间有三种表示方式；
    6. **hashlib模块**：用于加密相关操作，代替了md5模块，主要是提供SHA1、SHA224、SHA256、SHA384、SHA512和MD5算法；
    7. **random模块**：提供随机数。

    Python 的内置模块中也有很多使用十分方便的内置函数。

    1. **dir()函数**：dir()函数是一个排好序的字符串列表，**其内容是一个模块里定义过的名字**，包含在一个模块里定义的所有模块、变量和函数。例如：

    ```
    # 导入内置math模块
    import math
    # 调用math模块中的dir()函数
    content = dir(math)
    # 输出math模块中所有模块、函数和变量的名字
    print(content)
    ```

    程序输出了math模块中所有模块、函数和变量的名字。特殊字符串变量`__name__`是指向模块的名字，变量`__file__`是指向该模块的导入文件名。

    2. **globals()和locals()函数**：globals()和locals()函数可被用来返回全局和局部命名空间里的名字。

       如果在函数内部调用的是globals()函数，那么返回的是所有在该函数里能够访问的全局名字。如果在函数内部调用的locals()函数，返回的是能够在该函数里访问的局部命名。globals()函数和locals()函数的返回类型都是字典，所以名字们能用keys()函数摘取。

    3. **reload函数**：当一个模块被导入到一个脚本中后，程序只会将模块顶层部分的代码执行一次。

       因此，如果我们想再次执行模块顶层部分的代码，可以用reload()函数。该函数便会重新将之前导入过的模块导入。格式如下：

    ```
    reload(module_name)
    ```

    在这里，module_name要直接放模块名，而不能是一个字符串形式。例如，我们想重载hello模块：`reload(hello)`

13. ### 递归函数

    定义一个函数fact(n)，实现的功能是对输入的正整数n进行n!运算； 调用函数fact(n)，对输入的正整数n进行阶乘运算，并输出计算结果。

    **我的错误代码，将for与递归混为一谈：**

    ```
    n = int(input())
    # 请在此添加代码，对输入的正整数n进行阶乘运算，并输出计算结果。
    def fact(n):
        a = 1
        for i in range(1 , n+1):
            a *= i 
            fact(n) = a
        print(fact(n))
        return fact(n)
    fact(n)
    ```

    

    **for循环的代码：**

    ```
    # 输入正整数n
    n = int(input())
    
    # 定义阶乘函数
    def fact(n):
        a = 1
        for i in range(1, n+1):
            a *= i
        return a
    
    # 调用函数并输出结果
    print(fact(n))
    ```

    **递归函数**

    ```
    def fact(n):
        if n == 1:  # 终止条件
            return 1
        return n * fact(n-1) # 递归调用
    
    print(fact(5))  # 输出 120
    ```

    tips:

    1. **使用for循环，定义`fact(n)`函数：**
       - 初始化`a = 1`作为累乘变量
       - 使用`for`循环从1乘到n
       - 最后返回计算结果一定得是`a`，而不是fact(n)
       - 不用调用函数
    2. **递归三要素**
       - **终止条件**（如 `n == 1`）
       - **问题分解**（如 `sum_n(n) = n + sum_n(n-1)`）
       - **递归调用必须向终止条件靠近**（如 `n-1`）

##### e.g2 将输入的一个正整数分解质因数，并将结果输出。

```
# coding=utf-8

# 输入一个正整数
x = int(input())
result = []
i = 2
# 请在此添加代码，将输入的一个正整数分解质因数
########## Begin ##########
def Fjzy_num(n,i,result):
   
    if n == 1:
        return result
    if n % i == 0:
        result.append(i)
        return Fjzy_num(n/i,i,result)
    else:
        return Fjzy_num(n,i+1,result)   
Fjzy_num(x,i,result)
########## End ##########

# 输出结果，利用map()函数将结果按照规定字符串格式输出
print(x,'=','*'.join(map(str,result)))
```



11. ### lambda函数（匿名函数）

lambda函数又称匿名函数，匿名函数顾名思义就是没有名字的函数。

匿名函数不需要return来返回值，lambda函数表达式本身的计算结果就是返回值。例如，我们可以用lambda函数定义一个加法，计算两个整数相加：

```f = lambda x,y:x+y
f = lambda x,y:x+y
print(f(1,2))
```

结果为：3

例如，现在有一个整数列表，要求按照列表中元素的绝对值从小到大排列。

普通：

```
# 给出一个包含正数和负数的列表
list1 = [2,3,-5,0,-4,-8,-1]
# 定义一个函数，返回输入值的绝对值
def f(x):
    return abs(x)
# 利用sorted函数对列表中的元素根据绝对值的大小升序排序
list2=sorted(list1, key=f)
# 输出新列表
print(list2)
```

使用lambda函数：

```
# 给出一个包含正数和负数的列表
list1 = [2,3,-5,0,-4,-8,-1]
# 利用sorted函数对列表中的元素根据绝对值的大小升序排序
list2=sorted(list1, key=lambda x: abs(x))
# 输出新列表
print(list2)
```

15. ### map()和reduce()函数

这两个函数都是应用于序列的处理函数，map()用于映射，reduce()用于归并。

- #### map()函数

  map()函数会根据传入的函数对指定的序列做映射。map()函数接收两个参数，一个是function函数，另一个参数是一个或多个序列。map()函数会将传入的函数依次作用到传入序列的每个元素，并把结果作为新的序列返回。map()函数的定义为：

  `map(function, sequence[, sequence, ...]) -> list`

  例如，我们要对一个列表序列中的每个数值元素进行平方运算，结合上一关提到的lambda函数的例子，程序代码如下：

  ```
  r = map(lambda x: x ** 2, [1, 2, 3, 4,])
  print(list(r))
  ```

  当map()函数的第二个参数中存在多个序列时，会依次将每个序列中相同位置的元素一起做参数并调用function函数。例如，要对map()函数传入的两个序列中的元素依次求和，程序代码如下：

  ```
  r = map(lambda x, y: x + y, [1, 2, 3, 4, 5], [6, 7, 8, 9, 10])
  print(list(r))
  ```

  [7,9,11,13,15]

  > [!NOTE]
  >
  > 当map()函数传入的序列有多个时，我们要注意function函数的参数数量，应和map()函数传入的序列数量相匹配。

- #### reduce()函数

  reduce()函数把传入的函数**作用在一个序列[x1, x2, x3, ...]上，且这个函数必须要接收两个参数。**reduce()函数把第一次计算的结果继续和序列中的下一个元素做累积计算。reduce()函数的定义为：

  `reduce(function, iterable,[initializer])`

  function参数是有两个参数的函数，reduce()函数依次在序列中取元素，并和上一次调用function函数的结果做参数，然后再次调用function函数。例如：

  ```
  from functools import reduce
  r = reduce(lambda x, y: x + y, [1, 2, 3, 4, 5],6)
  print(r)
  ```

  > [!NOTE]
  >
  > 当不提供初始值时（即第三个参数），`reduce()` 会默认用**可迭代对象的第一个元素**作为初始值。
  
  即`r = reduce(lambda x, y: x + y, [1, 2, 3, 4, 5])`
  
  可写为：`r = reduce(lambda x, y: x + y, [ 2, 3, 4, 5],1)`
