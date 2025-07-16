# Hello World



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
  `string_strip2 = source_string.strip(目标字符)`

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

  
