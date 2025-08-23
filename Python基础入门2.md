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

   元组和列表一样，都有一些内置函数方便编程。例如：**就是没有插入、删除的函数哈**

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
       print('key:'+key)
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

   比如一份菜单，菜名作为键，而值是这道菜的配料，那么我们就可以将这些配料作为列表存储，然后作为值存储在字典中。

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

   使用`collections.namedtuple`函数创建命名元组，命名元组由两部分组成：

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

   **还可以通过字典创建命名元组：[(10 封私信) 译｜一文看完 Python 命名元组 - 知乎](https://zhuanlan.zhihu.com/p/272116203)**

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

4. #### 【实战演练】

   根据右边编辑器中各个函数中的提示，将函数Begin-End区间代码补充完整，使得程序能够正常运行并输出正确的结果。编辑区的3个函数，将按照如下顺序被调用：

       p = CreatePoint()
       PrintPoint(p)
       p = IncX(p)
       PrintPoint(p)
       p = IncY(p)
       PrintPoint(p)
   提示：后两个函数需要用到函数_replace()。
   ####测试说明
   正确的补充代码后，应该得到的结果：
   当前位置:x = 0,y = 0
   当前位置:x = 1,y = 0
   当前位置:x = 1,y = 1

   ```
   import collections
   
   # 首先定义一个Point的namedtuple类型
   Point = collections.namedtuple('Point', ['x', 'y'])
   
   def CreatePoint():
       # ********** Begin ********** #
       return Point(0, 0)  # 创建初始点(0,0)
       # ********** End ********** #
   
   def IncX(p):
       # ********** Begin ********** #
       return p._replace(x=p.x + 1)  # x坐标加1
       # ********** End ********** #
   
   def IncY(p):
       # ********** Begin ********** #
       return p._replace(y=p.y + 1)  # y坐标加1
       # ********** End ********** #
   
   def PrintPoint(p):
       print("当前位置:x = %d,y = %d" % p)
   ```

   



## 计数器

计数器是一个无序容器，用于记录各种值出现的次数。它采用键值对的形式存储，要记录的值作为key，这个**值出现的次数作为value**，value值可正可负。

1. ### 创建计数器
   要创建一个计数器实例，可以调用它的无参构造函数：

   #### `c = collections.Counter()`

   这样就创建了一个空的计数器实例c。

   也可以从list，tuple，dict，字符串等**可迭代对象(iterable)**创建：

   #### `c = collections.Counter(['a','a','b','b','c']) #从list创建`
   #### `c = collections.Counter(('a','a','b','b','c')) #从tuple创建`
    #### `c = collections.Counter({'a':2,'b':2,'c':1}) #从dict创建`
   #### `c = collections.Counter("aabbc") #从字符串创建`
   上面四条语句创建出来的计数器c都是相同的：
   `{'a': 2, 'b': 2, 'c': 1}`

   最后，你也可以直接指定键值对，来创建计数器：

   #### `c = collections.Counter(a=2,b=2,c=1)`
   创建出来的计数器c，与上面四条语句创建的计数器c是相同的。

2. ### 访问元素

   **计数器是dict的子类**，因此可以像使用dict那样访问计数器元素：

   `print(c['a'])`
   `print(c['b'])`
   `print(c.c)`
   得到的结果是：
   2
   2
   1
   **不过与dict不同的是，当访问计数器中不存在的元素的时候，不会产生异常，而是返回0，**比如：

   `print(c['d']) #c中没有d元素，但不会发生异常`
   上面的代码能够正常运行，并且结果是：0

3. ### 增加计数与减少计数

   要改变计数器中某一元素的值，除了可以使用操作dict的方式：c.a = XXX外，计数器还提供了两个成员函数**update和subtract**。

   【增加】**update函数**接受一个可迭代对象，然后将这个对象中各种值出现的次数加到计数器中，比如：

   #### `c.update("aabbcd") #字符串也是可迭代对象`
   上面这行语句执行后，c的值从原来的：
   `{'a': 2, 'b': 2, 'c': 1}`
   **增加到了：**
   `{'a': 4, 'b': 4, 'c': 2, 'd': 1}`

   

   【减少】**subtract函数**与update函数类似，不过它是从计数器中减去可迭代对象中各种值出现的次数，比如：

   c.subtract("aabbcd")
   上面这行语句执行后，c的值从原来的：
   {'a': 4, 'b': 4, 'c': 2, 'd': 1}
   **减少到了：**
   {'a': 2, 'b': 2, 'c': 1, 'd': 0}

4. ### 删除元素

   从上面的例子可以发现，当计数器中一个元素的值减少到0时，它并不会自动从计数器中删除，如果要删除元素，可以使用del函数：

   #### `del(c['d'])`
   上面这行语句执行后，c的值从原来的：
   `{'a': 2, 'b': 2, 'c': 1, 'd': 0}`
   变成了：
   `{'a': 2, 'b': 2, 'c': 1}`
   即元素d被删除了。

5. ### TopN操作

   计数器还提供了一个**获取出现次数最多的n个元素的成员函数most_common**，它返回包含这些元素的list，比如：

    `top1 = c.most_common(1) #出现次数最多的元素`
    `print(top1)
   top2 = c.most_common(2) #出现次数最多的两个元素`
    `print(top2)
   all = c.most_common() #不提供参数则返回所有元素`
   `print(all)`
   得到的结果是：
   `[('a', 2)]`
   `[('a', 2), ('b', 2)]`
   `[('a', 2), ('b', 2), ('c', 1)]`

   > [!NOTE]
   >
   > 注意：如果有多个元素的值相同，那么它们之间的顺序是不可确定的，不要在它们的顺序上作任何假设。

   

## 双向队列

双向队列是一种能在**队列两端都进行入队、出队操作的数据结构**，比普通的队列更加灵活也更加复杂。

1. ### 创建双向队列deque

   就像计数器Counter，双向队列可以调用无参构造函数创建一个空队列，也可以使用可迭代对象创建，并初始化一个队列，比如：

   ```
   d = collections.deque() #创建一个空队列
   d = collections.deque(['a','b','c']) #从list创建
   d = collections.deque(('a','b','c')) #从tuple创建
   d = collections.deque({'a':0,'b':1,'c':2}) #从dict创建
   d = collections.deque("abc") #从字符串创建
   ```


   第一行语句创建一个空队列，下面四行语句创建了含有元素a，b，c的队列，要注意**当从dict创建时，使用的是它的键key，而不是值value。**

2. ### 增加与删除元素

   双向队列与list类似，也有`append`和`pop`这两个成员函数，他们的作用分别是**向队列的右边增加元素**和**从队列的右边删除并返回一个元素**，比如：

   ```
   d.append('d') #向右边增加一个元素'd'
   print(d)
   d.pop() #从右边删除一个元素
   print(d)
   得到的结果：
   deque(['a', 'b', 'c', 'd'])
   deque(['a', 'b', 'c'])
   ```

   与append，pop相对应的，还有一组**对队列左边进行操作**的函数：`appendleft`，`popleft`，用法也与前面的一组类似：

   ```
   d.appendleft('+') #向左边增加一个元素'+'
   print(d)
   d.popleft() #从左边删除一个元素
   print(d)
   得到的结果：
   deque(['+', 'a', 'b', 'c'])
   deque(['a', 'b', 'c'])
   ```

   双向队列**还提供了一对操作**：`extend`和`extendleft`，用于**将一个可迭代对象的所有迭代值，依次加入到队列的右边或者左边：**

   ```
   d1 = collections.deque()
   d1.extend("123")
   print(d1)
   d1 = collections.deque()
   d1.extendleft("123")
   print(d1)
   得到的结果是：
   deque(['1', '2', '3'])
   deque(['3', '2', '1'])
   ```

   可以注意到，上下两个结果的值的**顺序是相反的。**

   【震荡队列】：是将奇、偶数分两侧加入队列

## 有序字典OrderedDic(od)

有序字典和普通的dict基本上是相似的，只有一点不同，那就是**有序字典中键值对的顺序会保留插入时的顺序。od = ([(),()])，列表装元组，数据很安全！**

1. ### 创建有序字典

   有序字典的创建方法和普通的dict类似，不过由于多了保留顺序的功能，因此在使用可迭代对象创建有序字典时，可以对它先排个序，让创建出来的字典元素也是有序的：

   这里使用的**sorted函数**，它返回对一个可迭代对象排序后的结果，如果可迭代对象的元素不能直接进行比较（比如元素是一个list或tuple等），则需要指定**key函数**。

   这里使用**lambda表达式** `lambda s:s[0]`和`lambda s:s[1]`，**分别指定key为data中每个元素（tuple类型）的第一个元素和第二个元素。**

   ```
   data = [('a',1),('b',3),('c',2)]
   od = collections.OrderedDict(sorted(data,key=lambda s:s[0]))#按数据中key值的大小排序
   print(od)
   od = collections.OrderedDict(sorted(data,key=lambda s:s[1]))#按数据中value值的大小排序
   print(od)
   ```

   得到的结果：
   OrderedDict([('a', 1), ('b', 3), ('c', 2)])
   OrderedDict([('a', 1), ('c', 2), ('b', 3)])

2. ### 修改顺序

   有序字典提供了一个**move_to_end函数**，这个函数可以**将指定的键值对移动到最前面或者最后面，即最左边或最右边：**

   ```
   dt = collections.OrderedDict()
   dt['a'] = 0
   dt['b'] = 1
   dt['c'] = 2
   dt.move_to_end('b',last = False) #将`b`键值对移动到最前方
   print(dt)
   dt.move_to_end('b',last = True) #将`b`键值对移动到最后方
   print(dt)
   ```

   得到的结果：
   OrderedDict([('b', 1), ('a', 0), ('c', 2)])
   OrderedDict([('a', 0), ('c', 2), ('b', 1)])

   #### 实战

   根据提示，在右侧编辑器Begin-End区间补充代码，实现函数功能：读取n(n>0)行输入，以每一行的数据为key，行号（从0开始）为value，建立n对键值对，然后将他们按照key排序后，放入一个有序字典，最后输出这个有序字典。

   测试输入：
   3
   a
   c
   b
   预期输出：
   OrderedDict([('a', 0), ('b', 2), ('c', 1)])

   测试输入：
   4
   A
   B
   D
   C
   预期输出：
   OrderedDict([('A', 0), ('B', 1), ('C', 3), ('D', 2)])

   ```
   import collections
   def Func():
       pairs = []
       n = int(input())
       for s in range(n):
           k = input()
       # ********** Begin ********** #
           pairs.append((k, s))#这里两个圆括号是因为，最外层是append()函数自带的哈，不包起来的话，append只能插入一个元素。
       od = collections.OrderedDict(sorted(pairs,key=lambda s:s[0]))
   
   
       # ********** End ********** #
       print(od)
   ```

   

## 默认字典(defaultdict)

默认字典的功能与dict基本相同，**但在访问一个不存在的key时，默认字典会提供一个默认值，**而不是引发异常。

1. ### 创建默认字典

   默认字典的构造函数接受一个工厂函数`default_factory`作为参数，可以将一个类型名看做是一个工厂函数，比如`list`，`tuple`，`str`等。
   这个函数会在要**生成默认值的时候无参调用**，如果使用类型名作为工厂函数，则这个类型必须要有**无参构造函数**，比如：

   ```
   dd = collections.defaultdict(int) #使用int作为工厂函数
   print(dd['a']) #访问不存在的key:'a'
   dd = collections.defaultdict(tuple) #使用tuple作为工厂函数
   print(dd['a']) #访问不存在的key:'a'
   dd = collections.defaultdict(str) #使用str作为工厂函数
   print(dd['a']) #访问不存在的key:'a'
   
   class Test:
       def __init__(self,name): #只有一个构造函数，而且它有一个参数
           print("init")
   dd = collections.defaultdict(Test) #使用自定义类型Test作为工厂函数
   print(dd['a']) #运行到这里就会出现异常，原因是Test类没有无参的构造函数
   ```

   直到最后一行语句之前，上面的结果是：
   `0`
   `()`

   ` `

   第三行是字符串的默认值：空字符串。

   如果不提供工厂函数，那么默认值的功能就失效了，此时默认字典与普通dict表现的功能一致：

   ```
   dd = collections.defaultdict()
   print(dd['a']) #虽然dd是一个默认字典，但由于没有指定工厂函数，没办法产生一个默认值，因此还是会发生异常
   ```

   

