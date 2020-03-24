# matlab

## 第一章

### MATrix LABoratory 矩阵实验室

集命令翻译、科学计算 于一身

### 特征

语法规则简单

MATLAB基本的语言环境提供了数以千计的计算函数

MATLAB是一种脚本式（scripted）的解释型语言

平台无关性（可移植性）

### 特点

功能强大；语言简单、内涵丰富；扩充能力、可开发能力较强；编程易、效率高

### 窗口

命令历史窗口、命令窗口、工作区窗口、当前目录窗口

### 搜索路径

在MATLAB界面选择菜单“File”→“Set Path”；

在命令窗口中运行“pathtool”或“editpath”命令；

### 常见计算函数

sqrt：开平方、exp：指数函数

## 第二章

### 简单的数学运算

直接输入法、存储变量法

### 数据类型

整数：8、16、32、64

浮点数：默认double

复数 ：实部和虚部、complex 函数

逻辑变量 ：01

各种数据类型之间的转换 ：

1）datatype(variable)，其中 datatype 为目标数据类型，variable 为待转化的变量；

2）cast(x,’type’)，将x的类型转化为’type’指定的类型。 

数据类型操作函数 

变量 ：

变量名区分大小写

变量名长度不超过63个字符

变量名必须以字母开始

系统预定义的特殊变量 

## 第三章

### 创建数组

直接输入：A＝[2,5,7；1,3,42]

函数法：zeros(m,n)、ones(m,n)、rand(m,n)、randn(m,n)、diag(A)、magic(m)

截取法：

## 第四章

### 多项式

#### 概念

多项式由一个行向量表示

该向量元素是该多项式的系数

且按降幂次序排列 

#### 函数

poly2sym：行向量转换成多项式

roots：求解多项式的根

poly：已知多项式的根，求解多项式 

conv：多项式的乘法

d=a+b：多项式加法

deconv：n多项式的除法     [q , r]=deconv(c , b)%q是商式，r是余式

polyder：多项式的导数     p = polyder(P,Q)：求P*Q的导函数;[p,q] = polyder(P,Q)：求P/Q的导函数，导数分子存入p,分母存入q

polyval：多项式的求值   F=polyval(p,4)

曲线拟合：[P,S] = polyfit(X,Y,m)

### 函数运算

一元函数的极小值：>> [x,fmin]=fminbnd(fh,0.3,1)

多元函数的极小值：\>>[x,fvalue]=fminsearch(f,[-2,2])%x为坐标值，fvalue为对应x坐标的函数值

fzero：求一元函数的零点

一元函数的积分：  q=quad(fun,a,b)

二重积分：dblquad

三重积分：triplequad

### 练习

![image-20191224132331128](C:\Users\Lan\Desktop\大三上期末复习\image-20191224132331128.png)

## 第五章

### 字符串

#### 定义

字符可以构成一个字符串，或字符数组。 

一个字符串是被视为一个行向量。 

字符串中的每一个字符（含空格），以其 ASCII 码的形式存放于行向量中，是该字符串变量的一个元素

#### 使用

Matlab 用单引号来界定一个字符串。

可以使用方括号[ ]直接连接多个字符串变量，得到一个新字符串变量。

如要输入的字符串中有单引号，则由两个连续的单引号来表示。

若要计算字符串变量的长度（即组成字符串的个数），可用 length 指令。 

#### 命令

double或abs 指令: 查看字符串变量对应的ASCII码

char或setstr 指令: 将 ASCII 码转换为字符串形式 

class：判断变量类型

#### 一个字符数组变量存储多行字符串 

第一种方法是使用二维字符数组

必须先确认每个字符串（即每一行）的长度一样，否则就必须在短字符串结尾补齐空格

第二种方法用char 指令存储多字符串

departments = char(‘ee’,‘cs’,‘econ’)%每行的会自动补空格，以保证每行的元素相同

#### 执行

eval

#### 单元数组

##### 概念

1特殊的数据类型，在一个数组中存放各种不同类型的数据

2单元数组中的每一个元素称为单元cell。

3单元中的数据可以为任何数据类型，包括数值数组、字符、符号对象、其他单元数组和结构体。不同的单元中的数据类型可以不同。

##### 创建

赋值语句

cell函数：cell(2,3) celldisp()

##### 读取

b, d=b{1, 2}、e = b{1,2}(3,1)

#### 结构(structure)

由字段（或域，fields）组成

每个字段可以是任一种Matlab数据类型的数据或变量

与C语言的结构类型相似

#### 结构数组(structure array)

多个结构构成结构数组(structure array)

结构数组的元素就是一个结构

## 第六章

### MATLAB命令的执行方式

交互式命令执行方式（命令窗口）：逐条输入，逐条执行，操作简单、直观，但速度慢，执行过程不能保留。

M文件的程序执行方式：将命令编成程序存储在一个文件中（M文件），依次运行文件中的命令，可以重复进行。

.m

### 程序控制结构

#### 顺序结构

数据的输入：A = input('提示信息'，'选项')；

数据的输出：disp(输出项）

程序的暂停：pause（延迟描述）

#### 选择结构

##### 多分支if语句

语句格式：

if 条件1

​    语句组 1

elseif  条件2

​    语句组  2

…

elseif  条件m

​    语句组  m

else

​    语句组n

end



##### switch语句

switch语句根据表达式的取值不同，分别执行不同的语句，其语句格式：

switch 表达式

case 值1

​        语句组1

case 值2

​        语句组2

…

case 值m

​        语句组m

otherwise

​         语句组 n

end



#### 循环结构

##### for语句

for语句的格式为：

for 循环变量=初值:增量:终值

循环体语句

end



##### while语句

while语句的一般格式为：

while 条件

​       循环体语句

end



##### break语句用于终止循环的执行

   当在循环体内执行到该语句时，程序将跳出循环，继续执行循环语句的下一语句。

##### continue语句控制跳过循环体中的某些语句

​      当在循环体内执行到该语句时，程序将跳过循环体中所有剩下的语句，继续下一次循环。

##### 函数文件的基本结构

函数文件由function语句引导，其基本结构为：

​        function  输出形参表 = 函数名（输入形参表）

​           注释说明部分

​           函数体语句



## 第七章

### 符号运算

#### 符号运算特点

在符号计算中，参与运算的是符号变量而不是数值，使用字符串进行分析。数值运算中必须先对变量赋值，然后才能参与运算。符号运算无须事先对独立变量赋值，运算结果以标准的符号形式表达，可以获得任意精度的解。

#### 符号运算与数值运算区别

#### 符号对象的生成

sym('常量')  

syms a b c

符号表达式的建立：

(1) 用 sym 函数直接建立符号表达式。

(2) 使用已经定义的符号变量组成符号表达式。

#### 符号表达式的操作和转换

findsym(expr)：查找符号表达式的符号变量

##### 符号表达式的化简

(1)pretty函数：给出排版形式的输出结果。pretty不能有输出参数

(2) collect函数：对符号变量合并同类项，多个符号变量，可以指定按某个符号变量合并同类项。

(3) expand函数---将符号表达式展开成多项式形式。

(4) horner函数---将符号表达式写成嵌套形式。

(5) factor函数---将符号表达式写成因式的形式。

(6) simplify函数---利用各种恒等式对符号表达式化简。

(7)[N,D]=numden(f)--- N为通分后的分子，D为通分后的分母



##### 符号表达式的替换

subs(f,x,a) 

### 符号极限、微积分和级数求和

#### 符号极限

limit(f,x,a): 计算![image-20191224183938888](C:\Users\Lan\Desktop\大三上期末复习\image-20191224183938888.png)

limit(f,a): 当默认变量趋向于 a 时的极限

limit(f): 计算当默认变量趋向于0 时的极限

limit(f,x,a,'right'): 计算右极限

limit(f,x,a,'left'): 计算左极限



#### 符号微分

g=diff(f,v)：求符号表达式  f 关于 v 的导数

g=diff(f)：求符号表达式  f 关于默认变量的导数

g=diff(f,v,n)：求  f 关于 v 的 n 阶导数

g=diff(f,n)：求  f 关于默认变量的 n 阶导数



#### 符号积分

int(f,v,a,b): 计算定积分![image-20191224184052072](C:\Users\Lan\Desktop\大三上期末复习\image-20191224184052072.png)

int(f,a,b): 计算关于默认变量的定积分

int(f,v): 计算不定积分![image-20191224184058498](C:\Users\Lan\Desktop\大三上期末复习\image-20191224184058498.png)

int(f): 计算关于默认变量的不定积分



#### 符号求和

symsum(f,v,a,b): 求和![image-20191224184123320](C:\Users\Lan\Desktop\大三上期末复习\image-20191224184123320.png)

symsum(f,a,b): 关于默认变量求和



### 方程求解

代数方程求解：solve(f,v)

微分方程求解：dsolve('eqn1','condition','var')

### 积分变换

#### 傅立叶(Fourier)变换

fourier(fx,x,t)  求函数f(x)的傅立叶像函数F(t)。

ifourier(Fw,t,x)  求傅立叶像函数F(t)的原函数f(x)

#### 拉普拉斯(Laplace)变换

laplace(fx,x,t)  求函数f(x)的拉普拉斯像函数F(t)。

ilaplace(Fw,t,x)  求拉普拉斯像函数F(t)的原函数f(x)

## 第八章

### 绘图基本操作

plot(y) 

plot(x, y)

plot(x1, y1, x2, y2, …)

plotyy(x1, y1, x2, y2)   

<img src="C:\Users\Lan\Desktop\大三上期末复习\image-20191224184632114.png" alt="image-20191224184632114" style="zoom:50%;" />

#### plot(x,y,string)：

title(‘图形名称’)

xlabel(‘x轴说明’)

ylabel(‘y轴说明’)

text(x,y,’图形说明’)%x,y为坐标

gtext(‘说明文字’)%用鼠标拖动来确定说明文字的位置

legend(‘string1’,’string2’,…)%图例中的文本通过字符串string1，string2等指定



### 相关命令

创建绘图窗口：figure(n)

保持当前窗口图像：hold on    hold off

显示网格：grid on    grid off

划分绘图区域：subplot(m, n, k)

### 特殊二维绘图函数

 bar –––– 绘制条形图

 polar –––– 绘制极坐标图

 hist –––– 绘制统计直方图

 stairs –––– 绘制阶梯图

 stem –––– 绘制火柴杆图

 rose –––– 绘制统计扇形图

 area –––– 区域图

 pie –––– 饼图

 loglog----绘出以log10-log10为坐标刻度的对数图

 semilogx---x轴为log10刻度，y轴为线性刻度

semilogy---y轴为log10刻度，x轴为线性刻度

### 三维曲线和曲面

三维线图：plot3(x,y,z,‘s’),

三维网线图（mesh）和曲面图（surf）

#### colormap设定和获取当前色图的函数。

autumn 从红色平滑变化到橙色，然后到黄色。

bone 具有较高的蓝色成分的灰度色图。该色图用于对灰度图添加电子的视图。

### 练习

![image-20191224185308530](C:\Users\Lan\Desktop\大三上期末复习\image-20191224185308530.png)

## 第十一章

### Simulink简介

Simulink是基于MATLAB的框图设计环境，可以用来对各种动态系统进行建模、分析和仿真

Simulink模型文件的扩展名为.mdl

### Simulink的特点

交互式建模、交互式仿真、任意扩充和定制功能

### Simulink打开

在MATLAB命令窗口中输入simulink，或在功能区中单击simulink按钮，就可启动Simulink。Simulink浏览器(Simulink Library Browser)窗口随即打开。
在Simulink浏览器(Simulink Library Browser)窗口单击新建按钮，就可创建模型