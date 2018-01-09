# **symlib**

1.  Overview 介绍

本软件是一个带GUI的符号数学运算工具。

2. Usage 使用

define symbols:定义数学符号。

如：

    x,y,z
或
     
     f(x)
等。
Transform strings into instances of Symbols.

expression:输入数学表达式。如：

    1/(sqrt(5)+2*sqrt(2))
可接受按钮中的数学表达式，如微分方程：

    Derivative(f(x),x)-f(x)
及

    f(x).diff(x)+f(x)**2+f(x)
等。

output:输出结果。
如：

    (-sqrt(x)*y + x*sqrt(y))/(x*y*(x - y))



expand:展开表达式。
此命令无需定义符号，即define_symbols区无需输入字符。

如展开高次乘法,输入：

    (x+y)**3
则输出:

    x**3 + 3*x**2*y + 3*x*y**2 + y**3

Expand expression.


series:泰勒级数展开.
此命令需要定义符号，及展开的阶数，点击按钮会弹出对话框，
在对话框中输入阶数，中间用英文逗点分隔。
如展开6阶的三角函数sin(x),在define_symbols中输入
x,在弹出的窗口中输入0,6,则会得到输出：
    
    x - x**3/6 + x**5/120 + O(x**6)

Series expansion of expr.

latex:将数学表达式转换为LaTeX格式。
此命令无需定义符号。
如输入：

    exp(I*x)
则得到：

    exp(I*x)

Convert the given expression to LaTeX representation.

rational:数值约分。
此命令无需定义符号。
在expression中输入数值，中间用逗点分隔。
如输入：

    7,119
则得到：
    
    1/17

Represents integers and rational numbers.

simplify:化简表达式。
此命令无需定义符号。
如输入：

    (x+2)**2-(x+1)**2
则得到：
    
    2*x + 3
Simplify expression.

radsimp:分母有理化。
若对数值进行分母有理化，则无需定义符号。

如输入：

    1/(sqrt(5)+2*sqrt(2))
则得到：

    (-sqrt(5) + 2*sqrt(2))/3
若对符号表达式进行分母有理化，则需定义符号。

如定义x,y,输入：

    1/(y*sqrt(x)+x*sqrt(y))
则得到：

    (-sqrt(x)*y + x*sqrt(y))/(x*y*(x - y))
Rationalize the denominator by removing square roots.

factor:因式分解。
此命令无需定义符号。
如输入：

    15*x**2+2*y-3*x-10*x*y
则得到：

    (3*x - 2*y)*(5*x - 1)
Compute the factorization of expression.

collect:收集表达式中指定符号的有理指数次幂的系数。
根据需要指定符号。
如表达式为：

    a*x**2+b*x+1
若指定符号为x，则输出为：

    {1: 1, x: b, x**2: a}
含义为：变量x的零次项系数为1,一次项系数为b,二次项系数为a.

若指定符号为a,则输出为：

    {1: b*x + 1, a: x**2}
含义为：变量a的零次项系数为b*x+1,一次项系数为x**2.

若指定符号为b,则输出为：
 
    {1: a*x**2 + 1, b: x}
含义为：变量b的零次项系数为a*x**2+1,一次项系数为x.
Collect additive terms of an expression.

cancel:符号约分.
此命令无需定义符号。
如输入：

    (x**3-1)/(x-1)
则输出为：

    x**2 + x + 1

Cancel common factors in a rational function ``f``.

ratsimp:通分。
此命令无需定义符号。
如输入：

    x/(x+y)+y(x-y)
则输出为：

    -y/(x + y) + y(x - y) + 1
Put an expression over a common denominator, cancel and reduce.

integrate:定/不定积分。
此命令需要定义符号，及积分的上下限，点击按钮会弹出对话框，
在对话框中输入积分上下限，中间用英文逗点分隔。
如定义变量为:x;积分上下限为:0,2*pi;被积函数为：

    x*sin(x)
则会得到输出：
    
    -2*pi
Compute definite or indefinite integral of one or more variables.

intergral:积分表达式.

若是不定积分，只需输入积分变量及表达式，如：

    sin(x)/x
则会得到输出：
    
    Integral(sin(x)/x, x)
若是定积分，需输入积分变量、表达式，在弹窗中输入积分的上下限,如:0,1
则会得到输出：
    
    Integral(sin(x)/x, (x, 0, 1))
Represents unevaluated integral.

roots:求方程的根.
此命令需定义符号。
如输入：

    x**3-6*x**2+9*x
则输出为：

    {0: 1, 3: 2}
意思是方程的第一个根为x=0,第二个根为x=3.

Computes symbolic roots of a univariate polynomial.

solve:解方程.
此命令需定义符号。
解一元方程，如输入：

    x**3-6*x**2+9*x
则输出为：

    [{x: 0}, {x: 3}]
意思是方程的第一个根为x=0,第二个根为x=3.

解多元方程，,定义未知变量为x,y,如输入：

    x*y-1,x-2
则输出为：

    [{x: 2, y: 1/2}]
意思是方程的第一个根为x=2,第二个根为x=1/2.

暂时不能求解LambertW类型的多元非线性方程,如输入：

    x*exp(x)-1
则输出为：

    [{x: LambertW(1)}]
并不意味着此方程无解，只是本软件不能将其解出。
Algebraically solves equations and systems of equations.

derivative:导函数.
此命令需可以不在define_symbol区定义符号，但需在弹窗中输入变量及阶数。
如对函数sin(y)求二阶导函数,需在弹窗中输入：y,2;

则输出为：

    Derivative(sin(y), y, y)
Carries out differentiation of the given expression with respect to symbols.

limit:求极限.
此命令需定义符号。
如求函数 sin(x)/x 在 x=0 处的极限，在弹窗中输入0：

则输出为：

    1
如求函数 1/x 在x-> 无穷处的极限，在弹窗中输入oo:
则输出为：

    0
如求函数 1/x 在x=0 处的左极限，在弹窗中输入0,-,
则输出为：

    -oo
Compute the limit of e(z) at the point z0.

diff:直接求导.
此命令需可以不在define_symbol区定义符号，但需在弹窗中输入变量及阶数。
如对函数sin(x*2)求二阶导数,需在弹窗中输入：x,2;

则输出为：

    -4*sin(2*x)
Differentiate f with respect to symbols.

dsolve:解微分方程.
此命令需定义方程。
如求微分方程Derivative(f(x),x)-f(x),需在define_symbol去中输入：f(x);

则输出为：

    Eq(f(x), C1*exp(x))
含义为f(x)=C1*exp(x)。

Solves any (supported) kind of ordinary differential equation and system of ordinary differential equations

linsolve:求线性方程组.
此命令需定义符号。
求解线性方程组，输入：

    x+y-1,x-y+3
则输出为：

    {(-1, 2)}
求解非正定的线性方程组，输入：

    x+y+z-1,x+y+2*z-3
则输出为：

    {(-y - 1, y, 2)}
含义为x=-y-1,y=y,z=2.

Solve system of N linear equations with M variables.

solveset:求高次方程.
此命令需定义符号
求解一元高次方程,输入：

    x**3-6*x**2+9*x
则输出为：

    {0, 3}
如求解方程sin(x)-1=0,输入：

    sin(x)-1
则输出为：

    ImageSet(Lambda(_n, 2*_n*pi + pi/2), Integers())
另外，EmptySet()表示方程无解。
如输入方程：

    exp(x)
则输出为：

   EmptySet()
Solves a given inequality or equation with set as output.

trigimp:化简三角函数。
此命令无需定义符号。
如输入：

    sin(x)**2+2*sin(x)*cos(x)+cos(x)**2
则输出为：

    sin(2*x) + 1
reduces expression by using known trig identities.

expand_trig:展开三角函数。
此命令无需定义符号。
如输入：

    sin(2*x+y)
则输出为：

    (2*cos(x)**2 - 1)*sin(y) + 2*sin(x)*cos(x)*cos(y)
Wrapper around expand that only uses the trig hint.


## Todo:
完善对输入符号的支持。

## Feedback:
有任何疑问或建议欢迎反馈。



