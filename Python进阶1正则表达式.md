# 正则表达式

是对字符串操作的一种逻辑公式，就是用事先定义好的一些特定字符、及这些特定字符的组合，组成一个“规则字符串”，来筛选出符合这个规则的内容。

**可以简单理解为：一个强大的搜索工具中，正则表达式就是你要搜索内容的条件表达式。**

- ### Python 正则模块中常用的功能函数：

**re.findall（）函数**

作用：遍历整个字符串，可以获取其中所有匹配的字符串，返回一个列表。
一般用法：
`re.findall(r'正则表达式'，'要匹配的文本')`

e.g.

在命令行使用re.findall()函数 **匹配单词to**

```
import re
text = "0537-146987425,0537-299656897,The moment you think about giving up,think of the reason why you held on so long. Total umbrella for someone else if he, you’re just not for him in the rain.Never put your happiness in someone else’s hands.Sometimes you have to give up on someone in order to respect yourself. aaaa bbbbcc d dddddd"
print(re.findall(r'to',text))

```

匹配在text中**以g开头的所有单词**：

`print(re.findall(r'\bg\w*?\b',text))`

查找**字母长度为4的单词**：

`print(re.findall(r'\b\w{4}\b',text))`

查找出**xxxx-xxxxxxxxx格式的数据**：

`print(re.findall(r'\d{4}-\d{8}',text))`

- ### **正则表达式元字符**

这是因为正则表达式中的“公式”代表的含义你都不了解。想要学好正则表达式，你就要熟悉这些元字符代表的含义，除了多练习和多记忆没有什么好办法了。以下为一部分常用元字符的介绍，剩余部分用到的时候再去熟悉：

| 元字符 | 功能说明                                   |
| ------ | ------------------------------------------ |
| ^      | 匹配字符串的开始                           |
| $      | 匹配字符串的结束                           |
| .      | 匹配除换行符以外的任意字符                 |
| \d     | 匹配数字                                   |
| \b     | 匹配单词头或单词尾                         |
| \w     | 匹配任何字母、数字以及下划线               |
| \s     | 匹配任何空白字符，包括空格、制表符、换页符 |
| \B     | 与\b相反,匹配非单词边界                    |
| \W     | 与\w相反                                   |
| \S     | 与\s相反                                   |
| {m,n}  | {}前的字符或子模式重复至少m次，至多n次     |

- ### Python 正则模块中常用的功能函数：（接上）

**compile()函数**

编译正则表达式模式，返回一个对象的模式（可以把那些常用的正则表达式编译成正则表达式对象，这样可以提高一点效率）。

格式：`re.compile(pattern,flags=0)`

```
import re
text = "The moment you think about giving up,think of the reason why you held on so long."
text1 = "Life is a journey,not the destination,but the scenery along the should be and the mood at the view."
rr = re.compile(r'\w*o\w*')
print(rr.findall(text))   #查找text中所有包含'o'的单词
print(rr.findall(text1))   #查找text1中所有包含'o'的单词
```

其中：

`pattern`： 编译时用的表达式字符串（即正则表达式）；

`flags`：（可选）编译标志位，用于修改正则表达式的匹配方式，如：是否区分大小写，多行匹配等。

常用的flags有：

| 标志                 | 含义                                                     |
| -------------------- | -------------------------------------------------------- |
| `re.S(DOTALL)`       | 使匹配包括换行在内的所有字符                             |
| `re.I（IGNORECASE）` | 使匹配对大小写不敏感                                     |
| `re.L（LOCALE）`     | 做本地化识别（locale-aware)匹配，法语等                  |
| `re.M(MULTILINE)`    | 多行匹配，影响^和$                                       |
| `re.X(VERBOSE)`      | 该标志通过给予更灵活的格式以便将正则表达式写得更易于理解 |
| `re.U`               | 根据Unicode字符集解析字符，这个标志影响\w,\W,\b,\B       |

**match()函数**

在字符串刚开始的位置匹配，**在开头匹配到**目的字符便返回，如果开头没有目的字符将匹配失败，返回None。

格式：`re.match(pattern, string, flags=0)`

```
print(re.match('edu','educoder.net').group())
print(re.match('edu','www.educoder.net').group())

输出：
edu

Traceback (most recent call last):
File "<stdin>", line1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'
```

> [!NOTE]
>
> 注：`match()函数`返回的是一个`match object`对象，而match object对象有以下方法输出：
>
> `group()`：返回被正则匹配的字符串；#上面代码使用的
> `start()`：返回匹配开始的位置；
> `end()`：返回匹配结束的位置；
> `span()`：返回一个元组包含匹配 (开始，结束) 的位置；
> `groups()`：返回正则整体匹配的字符串，可以一次输入多个组号，对应组号匹配的字符串。

**search()函数**

`re.search()`函数会在字符串内查找模式匹配，**只要找到第一个匹配然后返回**。如果字符串没有匹配，则返回`None`。

格式：`re.search(pattern, string, flags=0)`

```
print(re.search('edu','www.educoderedu.net').group())
print(re.search('eduaaa','www.educoderedu.net').group())

输出：
edu

Traceback (most recent call last):
File "<stdin>", line1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'
#第二组字符串内部就没有eduaaa
```

> [!CAUTION]
>
> `match()`和`search()`比较类似，它们的区别在于：
>
> **match()只匹配字符串的开头**，如果开头没有出现目的字符串，**即使后面出现了也不会进行匹配**；
>
> 而**search()函数会在整个字符内匹配，只要找到一个目的字符串就返回。**



**finditer()函数**

**找到正则匹配的所有子串，把它们作为一个迭代器返回。**

搜索字符串，返回一个`Match`对象的迭代器（包含匹配的开始和结束的位置，如下图中的`i`所示）。

格式：`re.finditer(pattern, string, flags=0)`

```
itext = re.finditer(r'\d+','12 edueduedu44coder deducoder, 11skdh   ds 12')      #匹配所有的数字
for i in itext:
    print(i)
    print(i.group())
    print(i.span())   #span()返回一个元组包含匹配 (开始,结束) 的位置
    
输出：
<sre.SRE Match object; span = (0,2), match = '12'> 
	#i
12
	#i.group()
(0,2)
	#i.span()
```

**split()函数**

按照能够匹配的子串，将string分割后返回列表。

格式：`re.split(pattern, string)`；

可以使用`re.split`来分割字符串，如：`re.split(r'\s+', text)`将字符串，**按空格分割成一个单词列表。**

以数字为分割符，将字符串分割：

`print(re.split(r'\d+','asas2kdjs4jds5djdfj1djf0'))`

输出：

`['asas', 'kdjs', 'jds', 'djdfj', 'djf',' ']`



**sub()函数**

使用re**替换string中每一个匹配的子串后，返回替换后的字符串。**

格式：`re.sub(pattern, repl, string, count)`

用`-`替代`,`如下：

```
import re
text = "aaa,bbb,ccc,ddd"
print(re.sub(r',', '-', text))
```

输出：

aaa-bbb-ccc-ddd



**subn()函数**

返回替换次数。

格式：`subn(pattern, repl, string, count=0, flags=0)`
解释：用A替换123中的1，结果为A23，repl就是指的A。

把所有的数字替换为A：

`print(re.subn('\d','A','1asd2dkjf34'))`

输出：`(‘AasdAdkjfAA', 4)`

subn()不仅返回了替换后的字符串，还返回了替换的次数。
