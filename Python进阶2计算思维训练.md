每当我们需要利用程序去修改或分析存储在文本文件中的信息时，就必须先正确地读取文件。要用 Python 程序去修改或分析文本文件中的信息，首先需要将文本文件中的信息读取到内存中。我们既可以将文本文件中的内容一次性读取，也可以按每次一行的方法逐行读取。

本关的目标就是让学习者了解并掌握利用 Python 工具从文件中读取数据的相关知识。

**读取整个文件**
一般我们读取的文件和编写的 Python 文件位于同一目录下，例如在当前目录下我们已经创建了要处理的文件 test.txt ，里面包含的内容为：

Hello,world!
Hello,Python!
Hello,my brothers.

我们运行在同一目录下的 Python 文件 test.py ，代码如下：

```
with open('test.txt') as file_object:
    contents = file_object.read()
    print(contents)
```

程序运行结果：

Hello,world!
Hello,Python!
Hello,my brothers.

**test.py 文件中的第一行代码中有函数open()，用于打开文件，这是我们处理文件的第一步。**函数open()中的参数'test.txt'就是要打开的文件。函数open()返回的是打开文件的对象，第一行代码就是把文本文件 test.txt 打开，**并将其对象保存在file_object变量中**。

**关键字`with`的功能是在不再需要访问文件后自动将文件关闭。**所以我们在这里只是open()打开了文件，但是没有加入close()代码关闭文件，因为 Python 会在处理文件之后自动将文件关闭。

test.py 文件中的第二行代码是使用read()方法读取文本文件 test.txt 的全部内容，并将内容保存在字符串变量contents中，然后通过print()将结果都输出。

如果我们要处理的文本文件和 Python 程序文件不在同一目录下，那么我们就要在open()函数中传入文本文件的绝对路径。

**逐行读取**

我们也可以将文本文件中的数据进行逐行读取，我们要处理的文本文件还是上面的 test.txt ，这时我们可以逐行将 test.txt 的内容输出，代码如下：

```
with open('test.txt') as file_object:
    for line in file_object:
        print(line)
```

输出：

Hello,world!

Hello,Python!

Hello,my brothers.

我们会发现输出结果中每一行内容后面都多了一个空行，这时因为在文件中每一行的末尾都会有一个换行符，而每条print()语句也会加上一个换行符，所以每行末尾都有两个换行符，所以输出之后就会多一个空行。

我们可以采取`rstrip()`方法**消除空行**，代码如下：

```
with open('test.txt') as file_object:
    for line in file_object:
        print(line.rstrip())
```

这时输出的结果中就没有多余的空行了.

`.rstrip()`：是一个字符串方法，用于移除字符串**右侧**（末尾）的空白字符，包括：

- 空格 `' '`
- 换行符 `'\n'`
- 制表符 `'\t'`

**创建一个包含文件各行内容的列表**

在上文中，函数`open()`返回的对象只在`with`代码块内可用，但是我们想在`with`代码块之外的位置使用，这就需要在`with`代码块内创建一个包含文本文件 test.txt 各行内容的列表。例如：

```
with open('test.txt') as file_object:
    lines = file_object.readlines()
```

上述代码中`readlines()`方法就是从文本文件 test.txt 中依次读取每一行，并保存在lines列表中。