#1.2 你的第一个C++程序
##内容简介
* IDE的基本使用
* Hello World程序!
* 程序代码框架讲解
* 练习以及实验

<b><font color="red">注意！所有的代码都不要直接复制，即使是对着抄来打一遍，也不要直接复制过去，自己动手才能印象更深刻。</font></b>

 这一讲的主要从打开IDE开始一步一步完成我们的第一个程序：Hello World程序，这个程序将在屏幕上显示一段文字，那么，我们就开始吧!

##控制台应用程序是什么，为什么是控制台
 当前我们所编写出的程序都被称为控制台应用程序(看起来漆黑漆黑的)。
>控制台应用程序在执行时没有自己的界面，依靠控制台来进行字符串的输入和输出。

 控制台应用程序的用户通常只关注数据而不是界面。事实上任何软件(包括拥有漂亮用户界面的那些软件)的核心并不在于程序看起来有多么好看，而是这个程序有多么"能干"，也就是说界面并不会对一个程序的行为造成多大影响，仅仅只是和用户之间的交流方式不同而已。
 对于初学者来说，我们关注的是如何把程序写好，而不是把程序写漂亮，如果非要写漂亮的话，也只需要很少的工作就可以给程序安上外壳。

##配置IDE的语言
 Dev C++默认是全英文界面的，如果觉得不习惯可以将界面语言改为中文，更改方式如下：
 选择菜单栏的[Tools->Environment Options]，在右边可以看到Language的选项，选择中文(或者任何你想要的语言)即可。

##总之先让程序运行起来
 首先打开下载好的Dev C++，在菜单栏中选择：文件->新建->源代码，然后我们就可以在中间的编辑区输入代码啦!
 首先明确一条C++语言的基本规则：
 <b>C++中一条语句必须以分号`;`结束，注意观察代码和之后的解释来明确"语句"的概念。</b>
 在编辑区输入以下内容(注意，行号不需要输入)：
```
1 #include <iostream>
2 using namespace std;
3 int main()
4 {
5    cout << "Hello World!";
6    return 0;
7 }
```
 然后，在工具栏上找到以下几个按钮：
 
 ![1.2.1](http://cdn.sinacloud.net/tamce-cdn/cpp/1.2.1.png)
 
 这几个按钮从左到右分别是：编译，运行，编译运行，全部重新编译。
 点击编译按钮，这时软件会提示我们要把源代码保存到一个地方，注意选择文件类型为"C++ source file(C++源代码文件)"，之后我们就可以在保存源代码的地方看到产生的exe文件了，可以直接双击打开，也可以点击"运行"按钮来运行。

 运行结果是什么呢？一个黑色窗口快速闪烁，之后便消失不见。
 这是因为程序执行得太快了，执行完所有的指令后就直接退出了。
 但是我们需要看到程序执行的结果啊!以下有两种解决方案。
1. 在代码的第5和第6行之间插入一行:"cin.get();"，这样，源代码看起来就会像这样：
```
1 #include <iostream>
2 using namespace std;
3 int main()
4 {
5     cout << "Hello World!";
6     cin.get();
7     return 0;
8 }
```
2. 在Dev C++的环境选项[工具->环境选项]中找到:"在return之后暂停控制台程序"，并勾选这个选项，这样子代码不需要修改，从Dev C++中运行时就会自动停下，我们就可以看到结果啦，像下面这张图一样。

![1.2.2](http://cdn.sinacloud.net/tamce-cdn/cpp/1.2.2.png)

* 注意在"----------------------"以上的才是我们程序的输出，下面的内容是由Dev C++自动产生的数据，包括程序执行的事件以及返回值信息，另外如果是直接双击打开编译生成的exe程序，这些信息是不会产生的。

 无论你决定使用哪种方法来观察输出，现在请先按照第一种方案来完成我们的这个程序，本节的最后会有关于此内容的一个小实验~
 即使你决定使用第一种方法，也不要忘记你可以简单的通过第二种方法来简单观察你程序的运行时间，这真的是很方便的功能~

##代码解释
 看整个源代码的部分，我们发现第一行的代码似乎最奇怪，风格与其他代码格格不入，因为这一行代码带了一个"#"开头，而且在IDE中，这一整行代码都变成了同一种颜色（IDE中用不同颜色标记代码作用是为了区分关键字等，便于阅读）。这一行代码其实是一条预处理语句
>带有"#"开头的语句通常都是预处理语句，也叫编译指令，用于拓展程序设计的环境，也就是说这些指令是控制编译器所做的事情的，它并不属于C++语言的一部分。

 我们看代码的内容：
####\#include语句
```
1 #include <iostream>
代码第一行包含了一个头文件。
```
 "include"是包含的意思，一对尖括号将这个文件名圈了起来并告知了这个文件的位置，这条代码是告诉编译器："这个源代码要编译成可执行程序需要这个东西"，我们包含的是一个[头文件]，简单理解为：这个文件中有系统提供的某些功能，我们需要使用某个功能的时候只需要把相应的文件拿出来用就可以了。
 那么，被我们所包含的'iostream'里面都有些什么东西呢？从文件名来理解，i-o-stream[in-out-stream]意思是输入、输出、流，也就是说，标准库中使用流来进行输入输出的东西都在这里面，因此，要实现控制台程序的输入和输出就需要包含这个文件。
>* 标准库全名标准模版库[Standard Template Libarary, STL]提供了很多已经实现的功能，目前已经成为了C++语言标准的一部分因此不需要额外下载即可直接使用标准库的所有文相关件。
>* "流[stream]"是一种数据的传输方式，将数据以连续、动态的方式传输，这里的输入输出流就是使用流的传输方式向显示器发送数据，以及从键盘接受数据。

<br />

####using语句和命名空间
```
2 using namespace std;
代码第二行使用了一个名叫std的命名空间。
```
 using意为使用，namespace意为命名空间(名字空间)。
 代码作用何在？命名空间是为了防止命名重复而设计的一个东西，因为我们在编程时使用到其他人提供的东西是很常见的事情，但是不同人的代码中可能会有不同的东西使用了相同的名称，这样就会出现冲突，比如说甲使用了x这个名字，乙也使用了x这个名字，因此甲所编写的代码和乙所编写的代码放到一起用的时候x所指的东西就不明确了。
 那么如何解决冲突？总不可能把所有重复的名称都改过来吧？通常的做法是，提供代码的一方把所有的名称放进一个命名空间，比如甲把x放进了一个叫做a的命名空间内(众多其他名字也可以一起放进a中)，乙把x放进了一个叫做b的命名空间内，这样，使用甲提供的x的时候就可以使用这样的语法：`a::x`，而使用乙提供的x则使用`b::x`，在使用时<b>必须</b>说明这个名字在哪一个命名空间中，<b>除非</b>在代码中声明使用整个命名空间，就像这样:`using namespace a;` 这样声明过后使用甲的x只需要写:`x`即可，而使用乙的x时依旧需要使用`b::x`。
 
 通过以上的解释，我们不难理解第二行代码的作用，使用一个叫做std的命名空间，为什么要使用这个命名空间？哪些名字在这个命名空间中？
>* cout和cin在std命名空间中。
>* 标准库的所有名字都在std命名空间中。

####main函数，程序入口
```
3 int main()
4 {
  ...
8 }
这是一个main函数，是程序的入口
```
 一个过程要能够执行，则必须要有开始，有结束。
 对于一个程序来说也是如此，程序要开始运行，一定有一个起始的地方，同时也有一个结束的地方。在C++中，main函数是每一个可以独立运行的程序必不可少的部分，因为程序运行时将首先执行这里面的代码。
 main函数到底是什么？函数指什么？简单来说函数[Function]也可以被称为过程或者方法，或者说函数包含了一块代码，这一块代码在一对大括号`{}`之间。
 关于函数具体的内容将在以后的章节中讨论。
 这里我们只需要了解，需要执行的代码要写在main函数的[函数体]内，而main函数就是main函数，名字不能改变，它前面的`int`也不可省略。
>函数体就是指被大括号`{}`圈起来的部分，而函数头指的就是除了函数体的那部分，这里的函数头就是：`int main()`
>一个程序通常有且只有一个main函数

####输出！输出！
```
5 cout << "Hello World!";
显示 Hello World 消息
```
 如何在控制台上显示信息？我们可以很方便的使用iostream文件内提供的对象：`cout`，只需要使用`cout`就可向控制台输出文字了。
 将`cout`和要输出的东西用`<<`连接起来，就可以把这个数据放到输出流中了，然后数据就会被带到屏幕上被我们所看见。
 嗯？你说双引号？那是因为`Hello World`是一个数据，而不是一串代码，因此使用双引号来表明这是一个字符串。
>* 字符串，字符串成串
>* 字符，一个文字符号
>* cout意为:`console-out`控制台输出
>* `<<`这个符号在语法上的意义就像是`1+2`中的加号一样，只是进行的操作不是加法运算，而是输出操作罢了。

####让我们停下一小会
```
6 cin.get();
等待用户按下回车
```
 同`cout`的字面意思相同，`cin`意为`console-in`即控制台输入。
 这里使用了`cin`的一个`get`方法来获取用户的输入，直到用户按下回车程序才会继续执行。
 关于如何把用户输入的东西利用起来将在以后的章节讨论。
>* 方法——也就是函数（还记得main函数吗）
>* 句点的意义可以理解为"的"，`cin.get()`——`cin的get方法`

####结束程序
```
7 return 0;
返回0值，结束程序
```
 我们之前提到main函数是程序的入口位置，程序的出口在哪儿呢？实际上，main函数执行完毕后程序就会结束。
 使用`return`语句来返回一个值，并且结束当前函数的执行。
>* 返回值用于标记函数的执行情况，main函数的返回值标记了整个程序的执行情况，通常取0表示程序正常关闭了。
>* 当执行到main函数的反大括号时`}`函数也会自动结束，但不写return语句是不符合标准的写法，而关于return的更多信息将在以后的章节讨论。

##练习/实验
 这部分的练习请一定要自己主动完成，尽量不要上网查找资料，要的是一个探究的过程。

1. 尝试编写一个空白程序（什么都不做但是可以运行）。
2. 改变代码，输出自己想要输出的内容。
3. 尝试输出一些"奇怪"的东西
    1.双引号`"`
    2.换行
4. 如果不使用`using namespace std;`这条语句，那么代码应该怎么修改？

若是有本文任何错误和讲的不清楚的地方欢迎大家批评指正，也欢迎大家留下宝贵的意见或者提出自己的疑问。
 <tamce@outlook.com> / [tamce](http://www.tamce.cn/)

---

![CC BY-NC-SA](http://cdn.sinacloud.net/tamce-cdn/by-nc-sa.png)

 此C++教程由[Tamce](http://www.tamce.cn/)创作，采用[知识共享 署名-非商业性使用-相同方式共享 4.0](http://creativecommons.org/licenses/by-nc-sa/4.0/) 国际许可协议进行许可。

 This tutorial is written by [Tamce](http://www.tamce.cn), shared under the licence of [Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](http://creativecommons.org/licenses/by-nc-sa/4.0/).
