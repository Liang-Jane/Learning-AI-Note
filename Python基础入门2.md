## 元组与字典

## 【元组】

元组看起来犹如列表，但元组使用圆括号（）而不是[]来标识，而且列表的元素可以修改，但**元组的元素不能修改。**

因为元组具有不可变的特性，所以在能用元组替代列表的地方最好都使用元组，这样代码更安全。

1. 创建元组

   元组创建很简单，只需要在括号()中添加元素，元素之间用逗号隔开。元组中只包含单个元素时，需要在该元素后面添加逗号。例如：

   `menu1 = ('meat','fish','chicken')`
   `menu2 = ('meat',)`

   `menu3 = tupel(list1)`  **\\将列表转换为元组\\**

2. 访问元组

   元组和列表一样，可以使用下标索引来访问元组中的值。

   menu = ('meat','fish','chicken','carrot')
   print(menu[0])
   print(menu[1:3])

   输出结果：

   meat
   ('fish', 'chicken')

3. 修改元组：**不支持修改哈，亲**

4. 元组内置函数：

5. 元组和列表一样，都有一些内置函数方便编程。例如：**就是没有插入、删除的函数哈**

   `len(tuple)`：计算元组中元素个数；

   `max(tuple)`：返回元组中元素的最大值；

   `min(tuple)`：返回元组中元素的最小值；

   `tuple(seq)`：将列表转换为元组。

## 【字典】

字典和列表一样，都是 Python 中十分重要的可变容器模型，都可以存储任意类型元素。

字典是 Python 最强大的数据类型之一，**通过键-值对的方式建立数据对象之间的映射关系。**

字典的每个键-值对用冒号:分割，每个键-值对间用逗号,分隔开，字典则包含在{}中。列表格式如下：

#### `d = { key1 : value1, key2 : value2 }`

与键相关联的值可以是数字、字符串、列表乃至字典。事实上，可将任何 Python 对象用作字典中的值。

1. ### 访问字典中的值

   要获取与键相关联的值，可依次指定字典名和放在方括号内的键，如下所示：

   ```
   # 创建并初始化menu字典
   
   menu = {'fish':40, 'pork':30, 'potato':15, 'noodles':10}
   
   # 获取并返回menu字典中键'fish'键对应的值
   
   print(menu['fish'])
   输出结果：
   
   40
   ```

2. ### 添加键-值对

   要添加键-值对时，可依次指定字典名、键和键对应的值。下面在字典menu中添加两道菜的菜名和价格：

   ```
   # 创建并初始化menu字典
   menu = {'fish':40, 'pork':30, 'potato':15, 'noodles':10}
   # 向menu字典中添加菜名和价格
   menu['juice'] = 12
   menu['egg'] = 5
   # 输出新的menu
   print(menu)
   
   输出结果：
   {'fish': 40,'pork': 30,'potato': 15,'noodles': 10, 'juice': 12,'egg': 5}
   ```

   > [!NOTE]
   >
   > 注意：字典中键-值对的排列顺序和添加顺序没有必然联系。**Python 不关心字典中键-值对的排列顺序，而只关心键与值的对应关系。**
   > 同理，字典和列表一样，可以先创建一个空字典，然后可以不断向里面添加新的键-值对。

   

3. ### 修改字典中的值

   要修改字典中的值，可直接指定字典中的键所对应的新值。

   ```
   例如，将menu中的fish价格改为50：
   
   # 创建并初始化menu字典
   menu = {'fish':40, 'pork':30, 'potato':15, 'noodles':10}
   # 修改menu字典中菜fish的价格
   menu['fish'] = 50
   # 打印输出新的menu
   print(menu)
   输出结果：
   
   {'fish': 50, 'pork': 30, 'potato': 15, 'noodles': 10}
   ```

   

4. ### 删除键-值对

   使用**del方法**时，要指定字典名和要删除的键。

   ```
   例如，在menu菜单中删除键noodles和它的值：
   
   # 创建并初始化menu字典
   menu = {'fish':40, 'pork':30, 'potato':15, 'noodles':10}
   # 删除noodles键值对
   del menu['noodles']
   # 打印输出新的menu
   print(menu)
   输出结果：
   
   {'fish': 40, 'pork': 30, 'potato': 15}
   ```

## 遍历(注意for循环里的缩进问题和带冒号:)

Python 字典中包含大量数据，它和列表一样，支持遍历操作。Python有多种遍历字典的方式，可以遍历字典的所有键-值对、键或值。

1. ### 遍历字典中的键-值对

   Python 为字典类型提供了**items()**方法与**for循环**，items()方法会**将字典里的所有的键与值一起返回。**

   ```
   例如，餐馆有一个菜单包含了菜名和价格信息，菜名和价格顾客都需要知道，可以通过遍历输出menu字典的键和值来实现：
   
   # coding = utf-8
   # 创建并初始化menu菜单字典
   menu={'fish':'40','pork':'30','potato':'20','lamb':'50'}
   # 利用items()方法遍历输出键和值
   for key,value in menu.items():
       print('\nkey:'+key)
       print('value:'+value)
   输出结果：
   
   key:fish
   value:40
   key:pork
   value:30
   key:potato
   value:20
   key:lamb
   value:50
   ```

   items()方法每次都将对应的键和值指定到key和value变量中，然后用for循环输出。

2. ### 遍历字典中的键

   Python 为字典类型内置了**keys()**方法，该方法会**将字典里的键遍历出来。（也要结合for循环）**

   ```
   # 创建并初始化menu菜单字典
   menu={'fish':'40','pork':'30','potato':'20','lamb':'50'}
   # 利用keys()方法遍历输出键
   for key in menu.keys():
       print('food_name:'+key)
   输出结果：
   
   food_name:fish
   food_name:pork
   food_name:potato
   food_name:lamb
   输出结果表示，keys()方法每次都是将menu菜单中的键输出，显示菜名。
   ```

   

3. ### 遍历字典中的值

   Python 为字典类型内置了**values()**方法，该方法会**将字典里的值遍历出来。（也要结合for循环）**

   ```
   # 创建并初始化menu菜单字典
   menu={'fish':'40','pork':'30','potato':'20','lamb':'50'}
   # 利用values()方法遍历输出值
   for value in menu.values():
       print('food_price:'+value)
   输出结果：
   
   food_price:40
   food_price:30
   food_price:20
   food_price:50
   ```

   

## 嵌套（列表有字典、字典里有列表...）

Python 的列表和字典可以存储任意类型的元素，所以我们可以将字典存储在列表中，也可以将列表存储在字典中，这种操作称为嵌套。

1. ### 列表里存字典

   ```
   将3份菜单用字典的方式存储菜名和价格，然后将这3份菜单字典存储在一个列表中，例如：
   
   # 创建3个菜单字典，包含菜名和价格
   menu1 = {'fish':40, 'pork':30, 'potato':20,'noodles':15}
   menu2 = {'chicken':30, 'corn':55, 'lamb':65,'onion':12}
   menu3 = {'bacon':36, 'beaf':48, 'crab':72,'eggs':7}
   # 将3个菜单字典存储到列表menu_total中
   menu_total = [menu1,menu2,menu3]
   # 输出列表
   print(menu_total)
   
   输出结果：
   [{'fish': 40, 'pork': 30, 'potato': 20, 'noodles': 15}, {'chicken': 30, 'corn': 55, 'lamb': 65, 'onion': 12}, {'bacon': 36, 'beaf': 48, 'crab': 72, 'eggs': 7}]
   ```

   

2. ### 字典里存列表

   比如一份菜单，菜名作为键，而值我们想是这道菜的配料，那么我们就可以将这些配料作为列表存储，然后作为值存储在字典中。

   ```
   # 初始化menu菜单，里面包含配料列表
   menu = {'fish':['vinegar','soy','salt'], 'pork':['sugar','wine']}
   # 输出pork这道菜的配料
   print('The burding of pork is:',menu['pork'])
   
   输出结果：
   The burding of pork is: ['sugar', 'wine']
   ```

3. ### 字典里存字典

   一份总菜单，包含2个子菜单，每个子菜单都包含菜名和价格。例如：

   ```
   # 创建一个字典menu_sum，里面包含两个子菜单字典menu1和menu2
   menu_sum = {
       'menu1':{'fish':40, 'pork':30, 'potato':20,'noodles':15},
       'menu2':{'chicken':30, 'corn':55, 'lamb':65,'onion':12}
   }
   # 输出menu1和menu2中的菜名和价格
   print(menu_sum['menu1'])
   print(menu_sum['menu2'])
   输出结果：
   
   {'fish': 40, 'pork': 30, 'potato': 20, 'noodles': 15}
   {'chicken': 30, 'corn': 55, 'lamb': 65, 'onion': 12}
   ```

   

## 【命名元组 namegtuple】

1. ### 创建命名元组

   命名元组的构造函数接受两个参数**typename，field_names**：

   使用`collections`函数创建命名元组，命名元组由两部分组成：

   1）**typename**：元组的名字；
   2）**field_names**：元组各个元素的名称，也就是属性名称。

   ```
   比如：collections.namedtuple("Point",["x","y"])
   ```

   **这里point就是命名元组类名字**。

   **["x","y"]**就是命名元组的两个属性

   

   第二个参数["x","y"]也可以写成"x y"或者"x,y"，即用空格或者逗号隔开属性名，即：

   `collections.namedtuple("Point","x y")`
   `collections.namedtuple("Point","x,y")`
   我们可以将其赋值给一个变量：

   `Point = collections.namedtuple("Point","x,y")`
   `p = collections.namedtuple("Point","x,y")` #**变量名不一定要和第一个参数相同**
   以上得到的**变量Point或者p并不直接是一个元组对象，它只是一个类**，如果要创建它的实例，则需要像创建类实例一样调用它：

   `p1 = Point(x = 0, y = 0)`
   `p2 = p(x = 1, y = 1)`
   这样就创建了两个实例p1，p2，他们的内容分别是x = 0,y = 0，x = 1,y = 1。

2. ### 访问命名元组的元素

   上面通过collections.namedtuple创建的**命名元组类，实际上是元组类的子类**，因此命名元组也可以**通过索引访问元素：**

   print(p1[0])
   print(p1[1])

   输出：

   0

   0

   命名元组也可以**通过属性访问：**

   print(p2.x)
   print(p2.y)
   得到的结果：
   1
   1

3. ### 修改元素

   如果需要修改元组的元素，则不能简单的使用p1.x = 1，**需要调用成员函数_replace()**，它会返回一个包含新值的新实例

   `p1 = p1._replace(x = 1) #将p1的x值从0换到1`

