# Hello World

## 25.07.16

1. ### **input** 与 **print**

【输入的**全部输出**】

```
name=input("请输入一个人的名字：")
country=input("请输入一个国家的名字：")
print("世界那么大，{}想去{}看看。".format(name,country))
```

【输入的只**输出一部分**】

```
name=input("输入姓名：")
print("{}同学，学好Python，前途无量！".format(name))     
print("{}大侠，学好Python，大展拳脚！" .format(name[0]))  print( "{}哥哥，学好Python，人见人爱！".format(name[1:]))            
```

> [!IMPORTANT]
>
> [n:m]说明输出从n到m不含m的字符串name
>
> 从左往右（正向增，第一个字符记为0，空格也算1个字符）：0,1,2
>
> 从右往左（反向减，最右边那个字符记为-1，空格也算一个字符）：-1，-2，-3



2. ### **行**与**缩进**

> [!IMPORTANT]
>
> **缩进：**Python 使用缩进来表示代码块，缩进的空格数量可以由个人习惯决定，但同一个代码块的缩进空格数必须相同。
>
>
> **多行语句：**Python 的代码一般是一行一条语句，语句之后的分号 ; 可加可不加。但如果要在一行中写多条语句，则需要用分号 ; 隔开每条语句。

```
if True:
   print("true")
  print("true") #缩进不同是错误程序
```

```
if True:
    print("true")
    print("true")
else:
 print("false")
 print("false");#每一个块内的缩进一样即可，这个程序就对了
```

`print("hello") print("world")`想输出在一行，这个就是错误程序。

`print("hello");print("world")`加分号以后就是正确的能输出在一行的程序。

3. ### Python对**大小写敏感**，**标识符不能和保留字相同**

- 开头不能是数字，必须是字母或下划线

- Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：

  `import keyword`
  `print(keyword.kwlist)`

  > [!NOTE]
  >
  > **不能与以下保留字相同：**['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']

4. ### python注释用#或三个‘单引号或三个“双引号

5. ### 格式化输出，使用%操作符，以及字符串转换

> [!NOTE]
>
> 不同占位符的含义：
>
> %s：      作为字符串
> %d：     作为有符号十进制整数
> %u：     作为无符号十进制整数
> %o：     作为无符号八进制整数
> %x：     作为无符号十六进制整数，a～f采用小写形式
> %X：     作为无符号十六进制整数，A～F采用大写形式
> %f：     作为浮点数
> %e，%E： 作为浮点数，使用科学计数法
> %g，%G： 作为浮点数，使用最低有效数位

```
    print("%d + %d = %d"%(a,b,a+b))
    print("%d - %d = %u"%(a,b,a-b))
    print("%d * %d = %d"%(a,b,a*b))
    print("%d / %d = %f"%(a,b,a/b))
```

100 + 200 = 300
100 - 200 = -100
100 * 200 = 20000
100 / 200 = 0.500000

6. ### 合并字符串方法：

- 使用加号（+）运算符：

  ```
  first_name = "John"
  last_name = "Doe"
  full_name = first_name + " " + last_name
  print(full_name)  # 输出：John Doe
  ```

- 使用逗号（,）将多个字符串作为参数传递给print()函数：

  ```
  first_name = "John"
  last_name = "Doe"
  print(first_name, last_name)  # 输出：John Doe
  ```

- 使用字符串的format()方法：

  ```
  first_name = "John"
  last_name = "Doe"
  full_name = "{} {}".format(first_name, last_name)
  print(full_name)  # 输出：John Doe
  ```

- 使用f-string（格式化字符串）：

  ```
  first_name = "John"
  last_name = "Doe"
  full_name = f"{first_name} {last_name}"
  print(full_name)  # 输出：John Doe
  ```

7. ### 字符串长度获取

- 使用len()函数：length = len(target_string)，计算出字符串中单个元素的个数

8. ### 大小写转换

- **upper()**会将字符串中的所有字符都转换为大写，**lower()**则将所有字符转换为小写。除此之外，Python 还贴心的提供了**title()**方法，将字符串所有单词的首字母变成大写，而其他字母依然小写。

- ```
  #将源字符串转换为大写并存入upper_string变量
  
  upper_string = source_string.upper()
  
  #将源字符串转换为小写并存入lower_string变量
  
  lower_string = source_string.lower()
  
  #将源字符串每个词首字母转换为大写并存入title_string变量
  
  title_string = source_string.title()
  ```

9. ### 去除字符串首尾空格

- Python 提供了**strip()**方法，可以去除字符串两侧（不包含内部）全部的空格。【还可以】使用该方法，也可以通过指定参数，去除**两侧指定的特定字符**。

  `strip_string1 = source_string.strip()`
  `string_strip2 = source_string.strip(‘目标字符’)`

- **去除的时候会区分大小写**

  ### e.g. H≠h

  ```
  hello_world = '  **The world ** is big!*    '
  char_hello_world = hello_world.strip('TH *')
  print(char_hello_world)
  #代表去除两侧的空格、*、T、H
  结果输出：he world ** is big!
  #h就没有去除
  ```

  ## 25.07.17

1. ### 字符串查找、切分、替换

【查找】Python 提供了内置的字符串查找方法**find()**，利用该方法可以在一个较长的字符串中查找子字符串。

如果该字符串中，有一个或者多个子字符串，则该方法**返回第一个子串 所在位置 的最左端索引**，若**没有**找到符合条件的子串，**则返回-1**。find()方法的基本使用语法如下：

#### 【查找】`source_string.find(‘sub_string’)`
其中：

source_string：源字符串；

sub_string：待查的目标子字符串；

find：字符串查找方法的语法关键字。

【切分】Python 提供了**split()**方法实现字符串分割。该方法根据提供的分隔符，将一个字符串分割为字符列表，

如果不提供分隔符，则**程序会默认把空格（制表、换行等）作为分隔符**。其基本使用语法如下：

#### 【切分】`source_string.split(‘separator’)`
其中：

source_string：待处理的源字符串；

separator：分隔符；

split：字符串分割方法的关键词。

**还可以用+、/还有空格作为分隔符**，分割字符串。

【替换】Python 提供了**replace()**方法，用以替换给定字符串中的子串。其基本使用语法如下：

#### 【替换】`source_string.replace(‘old_string’, ‘new_string’)`
其中：

source_string：待处理的源字符串；

old_string：被替换的旧字符串；

new_string：替换的新字符串；

replace：字符串替换方法的语法关键词。

2. ## 列表元素增删改

   #### `append()`  `insert()`  `pop()`  `remove()`  等函数

- ### 增加

  （1）在列表尾部添加元素

  在 Python 中，可以使用**append()**方法向一个列表的**尾部追加**一个元素，其基本语法如下：

  #### 【尾部增加】`source_list.append('obj')`
  其中：

  source_list：待修改的列表；

  obj：待插入的元素。

  （2）在列表指定位置添加元素

  Python 也提供了**insert()**方法，可以在列表**任意指定位置插入**元素，其基本语法为：

  #### 【任意位置插入】`source_list.insert(index,'obj')`
  其中：

  source_list：待修改的列表；

  index：待插入的位置索引；

  obj：待插入的元素。

  > [!NOTE]
  >
  > 注意：在 Python 中，列表**起始元素的位置索引为0**。

  ### e.g. 第一个为0，第二个位置为1

  ```
  # 创建并初始化guests列表
  guests=['Zhang san','Li si','Wang wu','Zhao liu']
  # 向guests列表Zhang san后面增加一个名为Hu qi的客人
  guests.insert(1,'Hu qi')
  # 输出新的guests列表
  print(guests)
  
  输出结果：['Zhang san','Hu qi','Li si','Wang wu','Zhao liu']
  ```

- ### 修改

  Python 中修改列表元素的方法为：直接将列表中要修改的元素索引指出，然后为其指定新值。其基本语法如下：

  #### 【修改】`source_list[index] = 'obj'
  其中：

  source_list：待修改的列表；

  index：待修改元素的位置索引；

  obj：待元素的新值。

- ### 删除

  （1）删除**指定位置**的元素

  - ##### del 法

    调用del函数能够删除指定索引位置的元素，其基本语法如下：

    #### `del source_list[index]`
    其中：

    source_list：待修改的列表；

    index：待删除元素的位置索引。

    ```
    # 初始化guests列表
    guests=['Zhang san','Li si','Wang wu','Zhao liu']
    # 将列表中的`Zhang san`删除
    del guests[0]
    # 输出新的guests列表
    print(guests)
    
    输出：['Li si','Wang wu','Zhao liu']
    ```

    

  - ##### pop 法

    该方法将从源列表删除对应元素，同时返回被删除的元素。其基本语法如下：

    #### `deleted_obj = source_list.pop(index)`
    其中：

    deleted_obj：保存被删除元素的变量，可根据需要自由命名；

    source_list：待修改的列表；

    index：待删除元素的位置索引。

    > [!NOTE]
    >
    > 注意:index参数为可选项，**不填则默认删除列表末尾的元素。**

    ```
    # 初始化guests列表
    guests=['Zhang san','Li si','Wang wu','Zhao liu']
    # 将列表中的`Zhang san`删除
    deleted_obj = guests.pop(0)
    # 输出被删除的元素以及删除后的guests列表
    print(deleted_obj)
    print(guests)
    
    输出：Zhang san
    ['Li si','Wang wu','Zhao liu']
    ```

    

  （2）删除**指定值对应的元素**

  Python 还提供了**remove()**方法，可以不需要知道位置，直接通过元素值来删除对应的元素。

  #### `source_list.remove('obj')`
  其中：

  source_list：待修改的列表；

  obj：待删除元素的值。

  > [!NOTE]
  >
  > 注意：如果列表中有多个值为obj的元素，remove仅删除位置索引最靠前的那个元素。

  

3. ### 给列表元素排序  `sort()`

   #### `source_list.sort(reverse=True)`

   其中：

   source_list：待排序的列表；

   sort：列表排序函数的语法关键词；

   reverse：sort函数的可选参数。如果设置其值为True，则进行反向从大到小排序，如果设置为**False或者不填写该参数，则默认进行正向从小到大排序。**

4. ### 处理数字列表的数据

   #### `range()`  `list() ` `sum()`

   **range()函数，能够用来生成一系列连续增加的数字。**其基本使用语法有如下三种：

   1. #### `range(lower_limit,upper_limit,step)`

      lower_limit: 生成系列整数的下限整数，不填该参数则**默认为从0开始**，生成的整数从此数开始，包括该数；

      upper_limit：生成系列整数的上限整数，必填参数，**生成的整数要小于该上限**；

      step：在下限和上限之间生成系列整数之间的间隔步长，不填该参数则默认步长为1。

   2. 结合利用 Python 列表提供的**append()**插入功能创建一个列表。

      ##### e.g.

      ```
      # 声明一个列表变量
      numbers = []
      # 利用append()函数和range()函数向列表插入目标元素
      for i in range(10):  
      #默认步长为1，从0开始，小于10，即0-9
          number = i**2
          #即i^2
          numbers.append(number)
      print(numbers)
      
      输出：[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
      ```

   3. 使用**list()函数**和**range()函数**创建数字列表

      #### data_list = list(range(lower_limit,upper_limit,step))

      其中：

      **list：列表函数的语法关键词；**

      range：函数语法关键词；

      data_list：最终生成的列表变量。

   4. #### 对数字列表的简单计算

      利用这些函数可以轻松找到数字列表的最小值、最大值及进行总和等一系列统计运算。其基本语法如下：

      #### min_value = min(data_list)

      #### max_value = max(data_list)

      #### sum_value = sum(data_list)

      其中：

      min：数字列表求**最小值**的语法关键字；

      max：数字列表求**最大值**的语法关键字；

      sum：数字列表**求和**的语法关键字。

      

5. ### 处理部分列表元素（Python 中称为切片）

Python 切片是对一个列表取其部分元素获得一个子序列的常见操作，切片操作的返回结果类型与被切片的对象一致。要创建一个已有列表的切片，通过指定切片的第一个列表元素和最后一个列表元素的索引号即可。其基本语法如下：

#### `list_slice = source_list[start:end:step]`
其中：

source_list：被切片的源列表；

list_slice：切片后生成的子序列列表；

start：切片起始索引位置，省略则从头开始；

end：切片结束索引位置，省略则切至列表末尾**（不包含end索引位置那个元素，但省略就包括最后一个元素）**；

step：切片步长，可选参数，表示每N个元素取一个，默认为1。

> [!NOTE]
>
> 注意：切片和range()函数一样，Python 会自动**到达所指定切片结束索引位置的前面一个元素停止。**

##### e.g

```
my_menu = ['fish','pork','pizza','carrot']
print(my_menu[1:4:2])
print(my_menu[:3])
print(my_menu[2:])
输出结果：

['pork','carrot']
['fish','pork','pizza']
['pizza','carrot']
```



**负数索引**返回的是离列表末尾相应间隔的元素，列表**末尾元素的索引是从-1开始的**。例如，朋友的菜单是包含我的菜单最后3个菜名：

`my_menu=['fish','pork','pizza','carrot']`
`print(my_menu[-3:])`

输出结果：

`['pork','pizza','carrot']`
