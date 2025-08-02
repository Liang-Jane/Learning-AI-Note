基于类创建对象，每个对象都自动具备通用行为，并且类创建对象的过程也称为实例化。

类的定义与声明是同时进行的，在用class关键字声明一个类之后，此类就被定义了。

- ### 声明类

```
class ClassName(bases_classes):
    '类文档字符串'
    class_suite     # 类体
```

class后面接着是类名ClassName，类名的开头通常是大写。

类名后面的`(bases_classes)`表示这个类是由哪个类继承来的，如果没有合适的继承类，就使用`object`类，object类是所有类都会继承的基类。类文档字符串是对类所进行的说明，可以通过`ClassName.__doc__`查看。

```
class Book(object):
    '书籍类'
    bookList = ['python','java','c++','ruby']
    for book in bookList:
        print(book)
```

- ### 定义类

类里面的各种方法用`def`声明进行定义。**`__init__()`定义的变量，在的函数中后面无需再定义了**，因为init已经初始化了，是默认执行的。

```
class Book(object):
    '书籍类'
    def _init_(self,name,author,data,version):
        self.name = name
        self.author = author
        self.data = data
        self.version = version
    def sell(bookName,price):
        print("%s的销售价格为%d" %(bookName,price))
```

**类中的方法一定要通过实例的句点方法去调用。**

在实例化一个对象后，Python 会检查是否实现了`__init__()`方法。如果没有实现`__init__()`方法，则不会做其它的操作，直接返回对象，实例化过程完毕。而`__init__()`方法是用来给类本身初始化的，支持带参数的初始化。 **一定要先有init，然后定义好self的属性参数，后面的方法部分如果引入的不是实例本身的属性，在声明加入进去，否则不用加入，只需要括号内有self**

```
class Book:
    def __init__(self,bookname,price,author): #一定要先有init，然后定义好self的参数
        self.bookname = bookname
        self.price = price
        self.author = author
    def sell(self):
        print("%s书本的价格为%d" %(self.bookname,int(self.price)))
book = Book("python","45","aas") #创建实例
book.sell()
```

类的数据属性只与类绑定，不属于任何实例。类的数据属性也可以称为静态变量，它通常用来跟踪与类相关的值。类的数据属性使用的并不多，一般都是用实例数据属性。类中还有很多特殊属性，具体如下:

`ClassName.__name__`：类ClassName的名字；
`ClassName.__doc__`：类ClassName的文档字符串；
`ClassName.__bases`__：类ClassName的所有父类构成的元组；
`ClassName.__dict__`：类ClassName的属性；
`ClassName.__module__`：类ClassName定义所在的模块；
`Instance.__class__`：实例Instance所对应的类。

- ### self 到底是啥？

定义方法时，`self`总是作为第一个参数传递的。`self`代表实例本身，**`self.变量`代表调用此实例的变量，`self.方法`代表调用实例的方法。**

**因为声明方法时已经传入self，所以在调用时self就不用明确传入了，此时实例是隐含的。**

```
#调用绑定方法
class bindExample:
    def bindMethod(self):
        print("绑定方法调用实例")
be = bindExample()
be.bindMethod()
```

```
#调用非绑定方法
class bindExample:
    def bindMethod(self):
        print("非绑定方法调用实例")
be = bindExample()
bindExample.bindMethod(be)
```

- ### 静态方法

在声明静态方法的时候，使用函数修饰符`@staticmethod`。**固定搭配**

```
class StaticMethood:
    @staticmethod
    def statictest():
        print("这是静态函数")
StaticMethood.statictest()
```



- ### 类方法

在声明类方法的时候，使用函数修饰符`@classmethod`。**固定搭配**

```
class ClassMethod:
    @classmethod
    def classtest(cls):
        print(cls)
        print("这是类方法")
cm = ClassMethod()
cm.classtest()
```

结果为：

```
<class '__main__.ClassMethod'>
这是类方法
```

- ### 导入模块（所有类）

```
import ModuleName
```

通常这个模块就是要导入的那个类所在的文件`*.py`，所以调用类的方法为:

```
object = ModuleName.ClassName()
object.属性
object.方法
```

我们在导入时一定要知道我们需要的这个类或方法属于这个模块。

- ### 导入单个或多个类

```
from ModuleName import ClassName1,ClassName2,...
```

调用类的属性和方法的语句：

```
object = ClassName()
object.属性
object.方法
```

在这种方法中，若导入的类名相同，则后面导入的类将会覆盖前面导入的类。

**导入模块中所有类**

`from ModuleName import *`

调用类的属性和方法的语句为：

```
object = ClassName()
object.属性
object.方法
```

在这种方法中，若导入的模块中含有名字相同的类，则类与类之间也会产生覆盖。

- ### 继承父类

通过继承，子类可以继承其父类所有的属性和方法，这在很大程度上增强了代码的重用。

举个例子：动物就是父类，它具有着所有动物都有的共性，而鱼和豹子是子类，它们不仅具有共性：呼吸、奔跑、觅食，还有着自己独特的特征：游泳、爬树。

**父类**

也称基类，其声明方法与一般的类的声明方法一样。父类中存在着一些公共的属性和方法，子类继承于父类。

**子类**

子类继承于父类，拥有父类中的属性和方法，它自己也可根据实际情况声明一些属于自己的属性和方法。子类声明方法：

```
class subClass(parentClass1,parentClass2,parentClass3,……):
    class_suite
```

**类名后的括号里填的就是所继承的父类的名称。**

```
class ParentClass:
    static_var = 100
    def parentMethod(self):
        print("这是父类")
class SubClass(ParentClass):
    def subMethod(self):
        print("这是子类")
sc = SubClass()
print(sc.static_var)
sc.parentMethod()
sc.subMethod()
print("%s所属的父类为%s" %(sc.__class__,SubClass.__bases__))
```

结果为：

```
100
这是父类
这是子类
<class '__main__.SubClass'>所属的父类为(<class '__main__.ParentClass'>,)
```

没有父类的子类base属性为空。

如果继承导入模块里的类，继承的时候需要：模块名.父类名

- ### 继承父类+覆盖方法（overriding）

在子类继承父类的方法时，若子类需要这个方法具有不同的功能，那么可以通过覆盖（overriding）来重写这个方法。

只需要在子类里再写一个与父类中一样的方法，实现自己想要实现的功能，就能覆盖。

```
class Parent:
    def sayHello(self):
        print("hello,i am class parent")
class Subclass(Parent):
    def sayHello(self):
        print("hello,i am class subclass")
sc = Subclass()
sc.sayHello()

#输出：
hello,i am class subclass
```

Subclass继承了Parent类，但是因为它在类中重写了sayHello()，所以在创建实例后，调用的是重写后的sayHello()。

**在重写了父类中的方法后，也可以调用父类中的被重写方法。**

这时就是去调用一个未绑定的父类方法。例如：

```
Parent.sayHello(sc)

#输出：
hello,i am class parent#还是父类的结果，说明子类改写方法不影响父类方法
```

还可以在子类的重写方法里显示调用。

```
class Parent:
    def sayHello(self):
        print("hello,i am class parent")
class Subclass(Parent):
    def sayHello(self):
        Parent.sayHello(self)
        print("hello,i am class subclass")
sc = Subclass()
sc.sayHello()

#输出：
hello,i am class parent
hello,i am class subclass
```

但是最好的方法是在子类的重写方法里使用`super()`内建方法。

```
class Parent:
    def sayHello(self):
        print("hello,i am class parent")
class Subclass(Parent):
    def sayHello(self):
        super(Subclass,self).sayHello()		
#super法，没有什么额外参数需要处理就是空括号
        print("hello,i am class subclass")
sc = Subclass()
sc.sayHello()
```

- ### 不可变类型子类化

假定我们需要处理大量的浮点数，将浮点数四舍五入后得到最后的结果。这时我们可以定义这样一个类，用来进行这个操作。

```
class RoundFloat(float):
    def __new__(cls, val):
        return float.__new__(cls,round(val,1))
#round()函数是用于对数字进行四舍五入，并可以指定保留的小数位数的函数


print(RoundFloat(2.6557))
```

结果为：2.7

在这个类里面，通过调用父类的构造器来创建对象，然后实例化float、RoundFloat。这里我们仅仅是从一种类型中派生而来，我们可以使用`super()`内建函数去捕获对应的父类，然后调用父类的`__new__()`方法进行实例化。例如：

```
class RoundFloat(float):
    def __new__(cls, val):
        return super(RoundFloat,cls).__new__(cls,round(val,1))
print(RoundFloat(2.6557))
```

```
 实现以下内容：
 # 填入使用super()内建函数去捕获对应父类以调用它的__new__()方法来计算输入数值的绝对值的代码
 # 求一个数的绝对值的函数为abs()
 # 返回最后的结果
class ChangeAbs(int):
    def __new__(cls, val):      
        return super(ChangeAbs,cls).__new__(cls,abs(val))
#容易看出来在super函数里直接加其他函数，就能改变其父类方法的功能:abs()
        
        ########## End ##########
```



- ### 可变类型子类化

子类化一个可变类型与子类化不可变类型很类似，但是我们可能不需要使用`__new__()`或者是`__init__()`，因为一般情况下我们定义的类所继承到的类型的默认行为就足够我们用了。

```
class SortedKeyDict(dict):
    def keys(self):
        return sorted(super( SortedKeyDict, self).keys())
d = SortedKeyDict((('zhangsan', 1), ('lisi', 2),('wangwu', 3)))
print("By iterator:".ljust(12), [key for key in d])
print("By keys():".ljust(12), d.keys())
```

结果为：

`By iterator: ['zhangsan', 'lisi', 'wangwu']`
`By keys():   ['lisi', 'wangwu', 'zhangsan']`

- ### 多重继承

多重继承就是允许子类继承多个父类，子类可以调用多个父类的方法和属性。

但是，当多个父类拥有相同方法名的方法时，我们通过方法名调用父类方法就有一定的顺序。

#董守哲：我是小笨蛋，嘻嘻嘻

```
class A(object):
    def test(self):
        print("this is A.test()")
class B(object):
    def test(self):
        print("this is B.test()")
    def check(self):
        print("this is B.check()")
class C(A,B):
    pass
class D(A,B):
    def check(self):
        print("this is D.check()")
class E(C,D):
    pass
```

![预览大图](https://data.educoder.net/api/attachments/RGg5WlY3bkRRZjJ6YmlRdFJzOGRZQT09)

在我们调用E.test()时，在类A和类B中都存在这个方法。但是由于在多重继承中遵循广度优先的方式，所以程序最先搜索类E，然后再搜索类C和类D。如果还没找到，再到类A中查找。若类A中存在这个方法，则调用这个方法，若在类A中也没有找到，则再到类B中查找。

调用E.test()结果为：

this is A.test()

如果调用E.check()方法，那么先到类E中查找，然后在类C中查找，再到类D中查找。在类D中找到这个方法，调用这个方法。

调用E.check()的结果为：

this is D.check()

- ### 类里的内建函数

对于类、实例和其它对象而言，存在着一些内建函数，这些内建函数无需定义，可直接调用。



1）`issubclass()`

issubclass()是一个布尔函数，这个函数用来**判断一个类是否是另外一个类的子类或者子孙类。**

如果给出的子类确实是给出的父类的子类，则返回True，否则返回False。它的语法如下：

`issubclass(subclass, parentclass)`

parentclass也可以是一个包含若干个父类的元组，只要子类属于元组中某一个父类，则返回True，否则返回False。

2）`isinstance()`

isinstance()是一个布尔函数，这个函数用来**判断一个对象是否是给定类的实例。**

若是给定类的实例或是给定类的子类的实例，则返回True，否则返回False。

`isinstance(object,class)`

3）`hasattr()、getattr()、setattr()、delattr()`这几个函数可以在各种对象下工作，不限于类和实例。

**【属性】是对象绑定的变量或方法**

`hasattr()`是布尔型的，它用于**判断一个对象是否有一个特定的属性**，一般用于在调用某个属性前检查属性是否存在。

```
class testClass(object):
  foo = 100
  def __init__(self,name):
      self.name = name
test = testClass('theName')
print(hasattr(test,'name'))#test这个实例里面有name属性
print(hasattr(testClass,'foo'))#testClass这个类里面有foo属性
```

**【属性】是对象绑定的变量或方法**

 `getattr()`是用来获取对象的属性或者方法。若返回的是对象，则返回对象的值，若返回的是对象的方法，则返回方法的内存地址。

`setattr()`是用来给对象的属性赋值。若属性不存在，就先创建属性然后再赋值。

```
class testClass(object):
  foo = 100
  def __init__(self,name):
      self.name = name
test = testClass('theName')
setattr(test,'fool','200')
setattr(test,'foo','50')
print(getattr(test,'fool'))
print(getattr(test,'foo'))
```



`delattr()`是用来从一个对象中删除属性。



`dir()`
作用在**实例**上时，显示实例变量、实例所在的类、基类中定义的方法和属性；
作用在**类**上时，显示类与它的基类的`__dict__`内容；
作用在**模块**上时，显示此模块的`__dict__`内容；
dir()不带参数时，显示调用者的局部变量。

```
class testClass(object):
    foo = 100
    def __init__(self,name):
        self.name = name
test = testClass('theName')
print(dir(test))
```



`super()`函数的作用就是找出相应的类的父类，然后调用父类的方法与属性。

```
class parentClass:
    def __init__(self):
        self.name = "parent"
    def tell(self):
        print("this is parentClass")
class subClass(parentClass):
    def tell(self):
        print("this is subClass")
        parentClass.tell(self)
sc = subClass()
sc.tell()

输出：
this is subClass
this is parentClass
```

在这个示例中，我们在调用父类的方法时是通过非绑定的方式调用，这样的调用方式增大了代码的耦合性。如果我们要修改subClass的父类，则在子类的调用中也要修改相应代码。如果代码量庞大的话，这个工作几乎很难完成，所以我们采用super方法。例如：

```
class parentClass:
    def __init__(self):
        self.name = "parent"
    def tell(self):
        print("this is parentClass")
class subClass(parentClass):
    def tell(self):
        print("this is subClass")
        super(subClass,self).tell()
 #这里super代替了parentclass的出现，其实主要是容易忘子类的父类的名称，这个super直接不需要你记名称。
sc = subClass()
sc.tell()
输出：
this is subClass
this is parentClass
```

上面的例子中，我们**利用super()函数将寻找父类的任务交给子类**，这样既可保证代码的安全，修改起来也很方便。



`vars()`是用来返回对象的属性及其值的一个字典。如果没有给出对象，则返回当前调用位置的属性和属性值。



训练：

```
import specialmethodtest
sc = specialmethodtest.subClass()
# 请在下面填入判断subClass是否为parentClass的子类的代码，并输出结果
########## Begin ##########
print(issubclass(specialmethodtest.subClass, specialmethodtest.parentClass))
########## End ##########
# 请在下面填入判断sc是否为subClass实例的代码，并输出结果
########## Begin ##########
print(isinstance(sc,specialmethodtest.subClass))
########## End ##########
# 请在下面填入判断实例sc是否包含一个属性为name的代码，并输出结果
########## Begin ##########
print(hasattr(sc,'name'))
########## End ##########
# 请在下面填入将sc的属性name的值设置为subclass的代码
########## Begin ##########
setattr(sc,'name','subclass')
########## End ##########
# 请在下面填入获取sc的属性name的值的代码，并输出结果
########## Begin ##########
print(getattr(sc,'name'))
########## End ##########
# 请在下面填入调用subClass的父类的tell()方法的代码
########## Begin ##########
super(specialmethodtest.subClass,sc).tell()
########## End ##########
```

```
输出：
True
True
True
subclass
this is parentClass
```

- ### 类的私有化

在默认的情况下，Python 中的属性都是公开的（public），这就意味着此类所在的模块和导入了这个类的模块都可以访问到这个类中的属性和方法。但有时我们不希望外界直接访问某方法或属性，此时我们可以将这个方法和属性私有化。本关的任务就是让学习者掌握类的私有化。

1) 在属性或方法前添加**双下划线**将其变为私有。

在这种方法下，要调用私有属性就在名字前加上单下划线和类名。利用这种调用方法，就可以很好地避免当子类变量名与父类变量名相同时覆盖父类的变量。

```
class privatization(object):
    def __init__(self,var):
        self._var = var
        self.__var = var
        self.__var__ = var
        self.varation = var
pr = privatization(2)
BAG
print(pr.__var__)
print(pr.varation)
print(pr._privatization__var)

输出：
2
2
2
2
```

**从类里导入私有属性：要在类名前加一个下划线print(pr._privatization__var)**

2) 在一个模块中以单下划线开头的变量和函数被默认当做内部函数。

当我们使用`from module import *`来导入模块时，这些不会被导入。但如果使用`import module`来导入整个模块，这部分还是会被导入，那么就可以用`模块名.类名`来访问。

在 Python 中，以双下划线开头和双下划线结尾的是一些特殊的方法。比如`__init__()、__del__()`等。Python 官方建议不要以这样的方式来定义自己的变量或函数。

- ### 包装

包装就是把已存在的程序重新打包，使这个程序更加适合当前应用环境。包装就是**对已存在对象的属性功能进行调整，删除不需要的、添加或是修改已存在的功能，以达到自己所理想的规格，并装换成另外一种更适合当前使用场合的对外接口。**

包装包括定义一个类，它的实例拥有标准类型的核心行为。

例如，我们需要处理一个数据，处理这个数据需要一系列的步骤，我们可以将这些步骤写到一个类里面。每当应用于不同的场景时，就将各种适合于此场景的方法包装成类，且原对象的属性和方法依然可以调用。

```
class Wrap(object):
    def __init__(self,obj):     # 声明了构造函数，模拟要包装对象的构造方法，目的是把obj隐藏起来
        self.__obj = obj     # __obj就是这个被包装对象的核心
    def get(self):    		 # 获取__obj对象
        return self.__obj
    def __repr__(self):
        return 'self.__obj'
    def __str__(self):     	# 转换__obj对象
        return str(self.__obj)
   
    def __getattr__(self,thelist):	#授权，包含一个寻找属性函数，如果没有就在__obj对象里新建一个thelist
        return getattr(self.__obj,thelist)
```

- ### 授权

**而授权是包装特有的一个属性**，通过授权，可以使当前类调用传入对象已存在的属性。

授权是包装的一个特性，采用已存在的功能达到最大限度的代码重用。在包装中我们可以新建、修改或删除已有的功能，**授权的过程就是将更新的功能交由新类来处理，已存在的功能就授权给对象的默认属性。**`self.__obj,newattr`

实现授权，一定要覆盖`__getattr__()`方法。其在代码里包含一个对`getattr()`内建函数的调用，调用`getattr()`得到默认对象的属性（数据属性或者方法）并返回它，以便于访问或者调用。

当引用一个属性时，解释器首先会在局部名称空间中查找那个名字，比如一个自定义的方法或局部实例属性。如果没有在局部字典中找到，则搜索类名称空间，以防一个类属性被访问。最后，如果两类搜索都失败了，搜索则对原对象开始授权请求，此时`__getattr__()`会被调用。

- ### 对象销毁（垃圾回收）

Python 的垃圾回收机制使用了引用计数这一机制来追踪内存中的对象。

```
x = 12
y = x
z = y
```

对象的引用计数在下列情况下增加：

对象被创建时；
创建了另一个别名时；
被作为参数传递给函数时；
成为容器对象的一个元素时。

当别名被重新赋值时，源对象的引用计数减1。

对象的引用计数在下列情况下减少：

- 一个本地引用离开了其作用范围时，比如函数结束；
- 对象别名被销毁时；
- 对象本身被销毁时。

**当对象的引用计数变为0时，它被垃圾回收。**

另一种情况是循环引用。循环引用是指两个对象互相引用，且都没有外部的对象对它们进行引用。

```
class delObject:
    def __init__(self):
        self.var = 100
    def __del__(self):
        class_name = self.__class__.__name__
        print("对象%s销毁" %class_name)
do1 = delObject()
do2 = do1
do3 = do1
print(id(do1))
print(id(do2))
print(id(do3))
del(do1)
del(do2)
del(do3)
```

结果为：

```
2176419869752
2176419869752
2176419869752
对象delObject销毁
```

