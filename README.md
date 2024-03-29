# BMTP 语言的一份友善说明书
## 语言介绍
BMTP语言，全称“BASIC in Mathematics Textbook of PEP”，中文全称“人教数学课本BASIC语言”，是人民教育出版社的《普通高中课程标准实验教科书数学3》第一 章《算法初步》中提到的一种“程序设计语言”。其语句形式和语法规则与BASIC语言类似。

我们小组历时三个月开发了这门语言，并在深圳中学范围内宣传，旨在激起深圳中学同学的编程兴趣，让更多人能将在课本上学习到的算法投入实践。我们周围有同学在学习了必修三课本后，对于这门新的语言跃跃欲试，但发现这是一门不存在的语言。

数学书为了让同学们把注意放在算法学习而非计算机语言本身，省去了BASIC语言中和计算机有关的部分。我们将这种语言实现出来，并添加了一些语言特性，让BMTP语言成为一门正真的为高中生设计的入门级解释性编程语言。
## 软件下载
[64位版本下载](https://github.com/BMTP-language/BMTP/raw/master/v1.0.0/compiled/visual_studio/Release/x64/bmtp.exe)  [32位版本下载](https://github.com/BMTP-language/BMTP/raw/master/v1.0.0/compiled/visual_studio/Release/x86/bmtp.exe)

这两个是使用visual_studio编译器编译的可执行文件，兼容性比较强，如果不兼容可以自行下载源码编译。

[源码链接](https://github.com/BMTP-language/BMTP)

## 使用方法
BMTP语言是一门高级语言，计算机无法读懂高级语言，所以需要解释器来把高级语言翻译给计算机（也就是翻译成一堆0和1）。刚才我们下载的东西叫“解释器”，它用来解释我们写的程序。使用方法就是很简单的，把程序交给解释器。
#### 示例
我们先创建一个文件，文件名叫`test.bxs`。文件内容为
```
INPUT a
INPUT b
c=MAX(a,b)'MAX(a,b)=a和b中的最大值
PRINT c
```
'为注释符号，它后面的所有东西（到该行行末）不会被执行。
然后把这个文件拖到`bmtp.exe`里，也就是我们的解释器。接下来会有一个小黑板，你输入第一个数字，按回车，然后输入第二个数字，它就会输出两个数字中较大的一个。什么，你说它闪退了？这是因为计算机计算地太快，~~肉眼无法捕捉到计算结果~~（在后续版本我们会添加程序暂停功能的！！）。建议在程序最后一行添加一个输入，以暂停程序。
例如`INPUT end`
这里面a，b，c都是变量，必修三数学书上有详细的说明，这里就不再补充了。
INPUT和PRINT的用法都和必修三书中所说的一模一样。
FOR语句，WHILE语句，DO-LOOP语句的用法也都与书中一样，这里不再作说明。

注意：PIRNT后不能接表达式。错误示例：`PRINT a+b`
## 语言特性介绍
### 精度

变量默认是高精度浮点数，可计算的有效位数为`1000000`，这意着这个语言本身就是一个超精度计算器，大至<a><img src="https://latex.codecogs.com/gif.latex?10^{10^{6}}" title="10^{10^{6}}" /></a>,小至<a><img src="https://latex.codecogs.com/gif.latex?10^{-10^{6}}" title="10^{-10^{6}}" /></a>都可以直接运算。

#### 示例：

就算e的小数点前10000位，预计时间5~10s，测试用的i5-7200u用了6.5s左右。
```
SET digit 10000
PRINT EXP(1)
INPUT end
```
理论上可以计算到1000000位，但时间大盖要一个月。
SET digit 为设置精度，默认为100，最大为100000。

### 数组
使用`VAR array name`可以定义名字为`name`的数组，初始长度默认为1。使用`name_i`可以读取数组的第i位。数组会自动扩大至已赋值的最大位。没赋值的位初始值为`0`。如果越位读取会报错。

#### 示例
```
VAR array a
a_10=10
PRINT a_5 '此处将输出0 
```
#### 线性筛素数
```
SET numbertype int64
INPUT " 输 入 筛 选 范 围 n";n
VAR array valid
VAR array ans
i=2
tot=0
WHILE i<=n
  valid_i=1
  i=i+1
WEND
i=2
WHILE i<=n
IF valid_i=1 THEN
  ans_tot=i
  tot=tot+1
END IF
j=0
WHILE j<tot AND i * ans_j <=n
  valid_(i * ans_j)=0
  IF i MOD ans_j=0 THEN
    j=tot
  END IF
  j=j+1
  WEND
  i=i+1
WEND
PRINT " 小 于 n 的 质 数 为 : \n";ans
END
```

### 逻辑运算符

`<`,`<=`,`>`,`>=`,`==`

`AND`,`OR`,`NOT`


### 本项目将持续更新！
