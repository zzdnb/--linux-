##    Linux课程总结

Terminal 操作终端相当于屏幕

批量操作



目录：

根目录/

下面有 bin（里面有可执行文件），etc，var底下有log,lib（有头文件），

proc（进程相关的一些信息），下面有cpuinfo





cp 文件 地址/名称  复制、黏贴，重命名

mv 修改名称

看进程:top  ps -ef  ps -aux  

关掉进程： 先top去找到PID ，再去kill -9 PID

shift + F 按照内存排序

查看类型：type

## 基础命令

    (1) ctrl c: 取消命令，并且换行
    (2) ctrl u: 清空本行命令
    (3) tab键：可以补全命令和文件名，如果补全不了快速按两下tab键，可以显示备选选项
    (4) ls: 列出当前目录下所有文件，蓝色的是文件夹，白色的是普通文件，绿色的是可执行文件
    (5) pwd: 显示当前路径
    (6) cd XXX: 进入XXX目录下, cd .. 返回上层目录
    (7) cp XXX YYY: 将XXX文件复制成YYY，XXX和YYY可以是一个路径，比如../dir_c/a.txt，表示上层目录下的dir_c文件夹下的文件a.txt
    (8) mkdir XXX: 创建目录XXX
    (9) rm XXX: 删除普通文件;  rm XXX -r: 删除文件夹
    (10) mv XXX YYY: 将XXX文件移动到YYY，和cp命令一样，XXX和YYY可以是一个路径；重命名也是用这个命令
    (11) touch XXX: 创建一个文件
    (12) cat XXX: 展示文件XXX中的内容
    (13) 复制文本
        windows/Linux下：Ctrl + insert，Mac下：command + c
    (14) 粘贴文本
        windows/Linux下：Shift + insert，Mac下：command + v
    安装：apt install silversearcher-ag    
    ag xxx
    可视化文件目录
    apt install tree
    tree xx
    
    查看数量
    ls | wc -l

## tmux和vim

```c++
1. tmux教程
    功能：
        (1) 分屏。
        (2) 允许断开Terminal连接后，继续运行进程。
    结构：
        一个tmux可以包含多个session，一个session可以包含多个window，一个window可以包含多个pane。
        实例：
            tmux:
                session 0:
                    window 0:
                        pane 0
                        pane 1
                        pane 2
                        ...
                    window 1
                    window 2
                    ...
                session 1
                session 2
                ...
    操作：
        (1) tmux：新建一个session，其中包含一个window，window中包含一个pane，pane里打开了一个shell对话框。
        (2) 按下Ctrl + a后手指松开，然后按%：将当前pane左右平分成两个pane。
        (3) 按下Ctrl + a后手指松开，然后按"：将当前pane上下平分成两个pane。
        (4) Ctrl + d：关闭当前pane；如果当前window的所有pane均已关闭，则自动关闭window；如果当前session的所有window均已关闭，则自动关闭session。
        (5) 鼠标点击可以选pane。
        (6) 按下ctrl + a后手指松开，然后按方向键：选择相邻的pane。
        (7) 鼠标拖动pane之间的分割线，可以调整分割线的位置。
        (8) 按住ctrl + a的同时按方向键，可以调整pane之间分割线的位置。
        (9) 按下ctrl + a后手指松开，然后按z：将当前pane全屏/取消全屏。
        (10) 按下ctrl + a后手指松开，然后按d：挂起当前session。
        (11) tmux a：打开之前挂起的session。
        (12) 按下ctrl + a后手指松开，然后按s：选择其它session。
            方向键 —— 上：选择上一项 session/window/pane
            方向键 —— 下：选择下一项 session/window/pane
            方向键 —— 右：展开当前项 session/window
            方向键 —— 左：闭合当前项 session/window
        (13) 按下Ctrl + a后手指松开，然后按c：在当前session中创建一个新的window。
        (14) 按下Ctrl + a后手指松开，然后按w：选择其他window，操作方法与(12)完全相同。
        (15) 按下Ctrl + a后手指松开，然后按PageUp：翻阅当前pane内的内容。
        (16) 鼠标滚轮：翻阅当前pane内的内容。
        (17) 在tmux中选中文本时，需要按住shift键。（仅支持Windows和Linux，不支持Mac，不过该操作并不是必须的，因此影响不大）
        (18) tmux中复制/粘贴文本的通用方式：
            (1) 按下Ctrl + a后松开手指，然后按[
            (2) 用鼠标选中文本，被选中的文本会被自动复制到tmux的剪贴板
            (3) 按下Ctrl + a后松开手指，然后按]，会将剪贴板中的内容粘贴到光标处


2. vim教程
    功能：
        (1) 命令行模式下的文本编辑器。
        (2) 根据文件扩展名自动判别编程语言。支持代码缩进、代码高亮等功能。
        (3) 使用方式：vim filename
            如果已有该文件，则打开它。
            如果没有该文件，则打开个一个新的文件，并命名为filename
    模式：
        (1) 一般命令模式
            默认模式。命令输入方式：类似于打游戏放技能，按不同字符，即可进行不同操作。可以复制、粘贴、删除文本等。
        (2) 编辑模式
            在一般命令模式里按下i，会进入编辑模式。
            按下ESC会退出编辑模式，返回到一般命令模式。
        (3) 命令行模式
            在一般命令模式里按下:/?三个字母中的任意一个，会进入命令行模式。命令行在最下面。
            可以查找、替换、保存、退出、配置编辑器等。
    操作：
        (1) i：进入编辑模式
        (2) ESC：进入一般命令模式
        (3) h 或 左箭头键：光标向左移动一个字符
        (4) j 或 向下箭头：光标向下移动一个字符
        (5) k 或 向上箭头：光标向上移动一个字符
        (6) l 或 向右箭头：光标向右移动一个字符
        (7) n<Space>：n表示数字，按下数字后再按空格，光标会向右移动这一行的n个字符
        (8) 0 或 功能键[Home]：光标移动到本行开头
        (9) $ 或 功能键[End]：光标移动到本行末尾
        (10) G：光标移动到最后一行
        (11) :n 或 nG：n为数字，光标移动到第n行
        (12) gg：光标移动到第一行，相当于1G
        (13) n<Enter>：n为数字，光标向下移动n行
        (14) /word：向光标之下寻找第一个值为word的字符串。
        (15) ?word：向光标之上寻找第一个值为word的字符串。
        (16) n：重复前一个查找操作
        (17) N：反向重复前一个查找操作
        (18) :n1,n2s/word1/word2/g：n1与n2为数字，在第n1行与n2行之间寻找word1这个字符串，并将该字符串替换为word2
        (19) :1,$s/word1/word2/g：将全文的word1替换为word2
        (20) :1,$s/word1/word2/gc：将全文的word1替换为word2，且在替换前要求用户确认。
        (21) v：选中文本
        (22) d：删除选中的文本
        (23) dd: 删除当前行
        (24) y：复制选中的文本
        (25) yy: 复制当前行
        (26) p: 将复制的数据在光标的下一行/下一个位置粘贴
        (27) u：撤销
        (28) Ctrl + r：取消撤销
        (29) 大于号 >：将选中的文本整体向右缩进一次
        (30) 小于号 <：将选中的文本整体向左缩进一次
        (31) :w 保存
        (32) :w! 强制保存
        (33) :q 退出
        (34) :q! 强制退出
        (35) :wq 保存并退出
        (36) :set paste 设置成粘贴模式，取消代码自动缩进
        (37) :set nopaste 取消粘贴模式，开启代码自动缩进
        (38) :set nu 显示行号
        (39) :set nonu 隐藏行号
        (40) gg=G：将全文代码格式化
        (41) :noh 关闭查找关键词高亮
        (42) Ctrl + q：当vim卡死时，可以取消当前正在执行的命令
    异常处理：
        每次用vim编辑文件时，会自动创建一个.filename.swp的临时文件。
        如果打开某个文件时，该文件的swp文件已存在，则会报错。此时解决办法有两种：
            (1) 找到正在打开该文件的程序，并退出
            (2) 直接删掉该swp文件即可
```

## shell语法

### 创建

创建脚本时要在前面加上`#! /bin/bash`

运行时要加权限`chmod +x ./test.bash`

解释执行时不需要权限： bash ./test.sh

### 注释

单行注释： `#`

多行注释: `:>>EOF  EOF `  EOF可以被替换

### 变量

**注意定义时不能有空格**

定义是 name1=“ name” ，‘ name’，name都可以

变量输出时用`${name1}` `$name1 `

定义只读命令：readonly name  或者是 declare -r name

删除变量: unset name1

自定义变量为环境变量：export name1  或者declare -x name1  检验方式：新开一个bash，输出环境变量name1 退出方式：ctrl + d, 或者是exit

环境变量变为自定义变量：declare +x name1

输出单引号' '里的东西时，不能转义，并且不能输出变量

输出双引号或者不加引号，能转义或者是输出变量

```shell
echo zzd ${name} \"hh\"
```

获取字符串长度：${#name}

```shell
 name="zzdnb,,," 
 echo ${name:0:5} 
 输出：zzdnb
```

参数	说明

${}变量替换

```
$#	代表文件传入的参数个数，如上例中值为4
$*	由所有参数构成的用空格隔开的字符串，如上例中值为"$1 $2 $3 $4"
$@	每个参数分别用双引号括起来的字符串，如上例中值为"$1" "$2" "$3" "$4"
$$	脚本当前运行的进程ID
$?	上一条命令的退出状态（注意不是stdout，而是exit code）。0表示正常退出，其他值表示错误 相当于return 0
$(command)	返回command这条命令的stdout（可嵌套）就是标准输出 sout
`command`	返回command这条命令的stdout（不可嵌套） sout
```



比如说输出 echo ${ls}

```shell
#! /bin/bash

echo "文件名:"$0
echo "第一个参数："$1
echo "第二个参数："$2
echo "第三个参数："$3
echo "第四个参数："$4

echo $#
echo $*
echo $@
echo $$                                                                                                                                                                                                      
echo $?
echo `ls`
echo $(ls)


acs@69e63c00215c:~$ ./test.sh 1 2 3 4
文件名:./test.sh
第一个参数：1
第二个参数：2
第三个参数：3
第四个参数：4
4
1 2 3 4
1 2 3 4
780
0
1 homework main.cpp test.sh
1 homework main.cpp test.sh
```

### 数组

初始化数组：
格式:

```shell
# array=(1 "2" abc yxc)
array[0]=acv
array[1]=asdasd
array[1000]=yxcc
echo ${array[0]}
echo ${array[1]}
echo ${array[1000]}  
```

初始化的时候可以用数组初始化，也可以直接给下标赋值，中间可以空着数



读取整个数组

```
${array[@]}  # 第一种写法
${array[*]}  # 第二种写法
```

数组长度

```
${#array[@]}
${#array[*]}

```

### expr命令

expr  表达式

表达式说明：

用空格隔开每一项
用反斜杠放在shell特定的字符前面（发现表达式运行错误时，可以试试转义）
对包含空格和其他特殊字符的字符串要用引号括起来
expr会在stdout中输出结果。如果为逻辑关系表达式，则结果为真，stdout为1，否则为0。
expr的exit code：如果为逻辑关系表达式，则结果为真，exit code为0，否则为1。

字符串表达式
length STRING
返回STRING的长度

index STRING CHARSET
CHARSET中任意单个字符在STRING中最前面的字符位置，下标从1开始。如果在STRING中完全不存在CHARSET中的字符，则返回0。
substr STRING POSITION LENGTH
返回STRING字符串中从POSITION开始，长度最大为LENGTH的子串。如果POSITION或LENGTH为负数，0或非数值，则返回空字符串。

```
#! /bin/bash

str="zzd nb"
echo $(expr length "${str}") 
echo `expr index "$str" zz`
echo $(expr index "$str" zz)
echo $(expr substr "$str" 1 2)  

输出结果：
6
1
1
zz
```

加减乘除

```
#! /bin/bash

a=2
b=1

# * 和括号都要进行转义
echo `expr $a + $b`
echo `expr $a - $b`
echo `expr $a \* $b`
echo `expr $a / $b`
echo `expr \( $a + $b \) \* \( $a - $b \)`

3
1
2
2
3
```

逻辑关系表达式
|
如果第一个参数非空且非0，则返回第一个参数的值，否则返回第二个参数的值，但要求第二个参数的值也是非空或非0，否则返回0。如果第一个参数是非空或非0时，不会计算第二个参数。
&
如果两个参数都非空且非0，则返回第一个参数，否则返回0。如果第一个参为0或为空，则不会计算第二个参数。

< <= = == != >= >
比较两端的参数，如果为true，则返回1，否则返回0。”==”是”=”的同义词。”expr”首先尝试将两端参数转换为整数，并做算术比较，如果转换失败，则按字符集排序规则做字符比较。

() 可以该表优先级，但需要用反斜杠转义

```
c=1
d=0
echo `expr $d \| $c`
echo `expr $c \| $d`
echo `expr $c \& $d`
echo `expr $c \> $d`
echo `expr $c \== $d`
1
1
0
1
0

      
```

### read命令

read命令用于从标准输入中读取单行数据。当读到文件结束符时，exit code为1，否则为0。

参数说明

-p: 后面可以接提示信息
-t：后面跟秒数，定义输入字符的等待时间，超过等待时间后会自动忽略此命令

```shell
#! /bin/bash

read -p "你是谁？" -t 3 name

echo $name

```



### echo

 双引号可以输出转义字符，使用单引号不能转义。

echo用于输出字符串。命令格式：

echo STRING
显示普通字符串
echo "Hello AC Terminal"
echo Hello AC Terminal  # 引号可以省略
显示转义字符
echo "\"Hello AC Terminal\""  # 注意只能使用双引号，如果使用单引号，则不转义
echo \"Hello AC Terminal\"  # 也可以省略双引号
显示变量
name=yxc
echo "My name is $name"  # 输出 My name is yxc
显示换行
echo -e "Hi\n"  # -e 开启转义
echo "acwing"
输出结果：

Hi

acwing
显示不换行
echo -e "Hi \c"  # -e 开启转义 \c 不换行
echo "acwing"

将结果输入到文件：

echo "hello world" > a.txt

原样输出字符串：

取单引号就行

输出日期：

echo `date`

### printf

printf命令用于格式化输出，类似于C/C++中的printf函数。

默认不会在字符串末尾添加换行符。

命令格式：

printf format-string [arguments...]
用法示例
脚本内容：

printf "%10d.\n" 123  # 占10位，前面没加表示右对齐
printf "%-10.2f.\n" 123.123321  # 占10位，保留2位小数，负号表示左对齐
printf "My name is %s\n" "yxc"  # 格式化输出字符串
printf "%d * %d = %d\n"  2 3 `expr 2 \* 3` # 表达式的值作为参数
输出结果：

       123.
       123.12    .
    My name is yxc
    2 * 3 = 6
### test

expr用stdout输出，1表示真，0表示假

test用exitcode输出， 0表示真，非0表示假



**逻辑运算符&&和||**
&& 表示与，|| 表示或
二者具有短路原则：
expr1 && expr2：当expr1为假时，直接忽略expr2
expr1 || expr2：当expr1为真时，直接忽略expr2
表达式的exit code为0，表示真；为非零，表示假。（与C/C++中的定义相反）

 ```shell
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test 2 -lt 3
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
0
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test 3 -lt 2
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
1
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -e test.sh && echo "exist" || echo "no exist"
no exist
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -e testExpr.sh && echo "exist" || echo "no exist"
exist
解析:
第8行：测试testExpr.sh是否存在，&&左边执行完执行右边，然后左边整体执行完，不用去执行右边
第7行：测试test.sh是否存在，test.sh不存在所以去执行右边，输出不存在

 ```



**测试参数	代表意义**
-e	文件是否存在
-f	是否为文件
-d	是否为目录

```shell
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -f a.txt 
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
0
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# mkdir ll
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -d ll
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
0
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -d sad
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
1
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# ls
a.txt  ll  test.cpp  testEcho.sh  testExpr.sh  testPrintf.sh  testRead.sh  testTest.sh

```

**文件权限判断**
命令格式：

test -r filename  # 判断文件是否可读
测试参数	代表意义
-r	文件是否可读
-w	文件是否可写
-x	文件是否可执行
-s	是否为非空文件

```shell
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -r testEcho.sh 
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
0
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -w testEcho.sh 
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
0
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -x testEcho.sh 
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
0
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# test -s testEcho.sh 
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt# echo $?
0
```

**整数间的比较**
命令格式：

test $a -eq  $b  # a是否等于b
测试参数	代表意义
-eq	a是否等于b
-ne	a是否不等于b
-gt	a是否大于b
-lt	a是否小于b
-ge	a是否大于等于b
-le	a是否小于等于b

**字符串比较**
测试参数	代表意义
test -z STRING	判断STRING是否为空，如果为空，则返回true
test -n STRING	判断STRING是否非空，如果非空，则返回true（-n可以省略）
test str1 == str2	判断str1是否等于str2
test str1 != str2	判断str1是否不等于str2



```shell
#! /bin/bash

a=1
b=3
test $a -eq $b # equal
echo $?
test $a -ne $b ## not equal
echo $?
test $a -gt $b #greater than
echo $?
test $a -lt $b #less than
echo $?
test $a -ge $b # greater equal
echo $?
test $a -lt $b # less equal                                                                                                                                                                                       
echo $?

s1="zzdnb"
s2=""
test -z s1
echo $?
test -n s2
echo $?
test "$s1" == "$s2" && echo true || echo false
echo $?
test "$s1" != "$s2" && echo true || echo false
echo $?


test -r a.txt -a -x a.txt && echo true || echo false
test -r testEcho.sh -o -x a.txt && echo true || echo false
test -r a.txt -o -x a.txt && echo true || echo false


[ 2 -lt 3 ]
echo $?

结果输出：

1
0
1
0
1
0
1
0
false
0
true
0
false
true
true
0



```

**

多重条件判定**
命令格式：

test -r filename -a -x filename
测试参数	代表意义
-a	两条件是否同时成立
-o	两条件是否至少一个成立
!	取反。如 test ! -x file，当file不可执行时，返回true
**判断符号[]**
[]与test用法几乎一模一样，更常用于if语句中。另外[[]]是[]的加强版，支持的特性更多。

```
[ 2 -lt 3 ]  # 为真，返回值为0
echo $?  # 输出上个命令的返回值，输出0
acs@9e0ebfcd82d7:~$ ls  # 列出当前目录下的所有文件
homework  output.txt  test.sh  tmp
acs@9e0ebfcd82d7:~$ [ -e test.sh ] && echo "exist" || echo "Not exist"
exist  # test.sh 文件存在
acs@9e0ebfcd82d7:~$ [ -e test2.sh ] && echo "exist" || echo "Not exist"
Not exist  # testh2.sh 文件不存在
注意：

[]内的每一项都要用空格隔开
中括号内的变量，最好用双引号括起来
中括号内的常数，最好用单或双引号括起来
例如：

name="acwing yxc"
[ $name == "acwing yxc" ]  # 错误，等价于 [ acwing yxc == "acwing yxc" ]，参数太多
[ "$name" == "acwing yxc" ]  # 正确
```

### 判断

if…then形式
类似于C/C++中的if-else语句。

单层if
命令格式：

if condition
then
    语句1
    语句2
    ...
fi
示例：

a=3
b=4

if [ "$a" -lt "$b" ] && [ "$a" -gt 2 ]
then
    echo ${a}在范围内
fi
输出结果：

3在范围内
单层if-else
命令格式

if condition
then
    语句1
    语句2
    ...
else
    语句1
    语句2
    ...
fi
示例：

a=3
b=4

if ! [ "$a" -lt "$b" ]
then
    echo ${a}不小于${b}
else
    echo ${a}小于${b}
fi
输出结果：

3小于4
多层if-elif-elif-else
命令格式

if condition
then
    语句1
    语句2
    ...
elif condition
then
    语句1
    语句2
    ...
elif condition
then
    语句1
    语句2
else
    语句1
    语句2
    ...
fi
示例：

a=4

if [ $a -eq 1 ]
then
    echo ${a}等于1
elif [ $a -eq 2 ]
then
    echo ${a}等于2
elif [ $a -eq 3 ]
then
    echo ${a}等于3
else
    echo 其他
fi
输出结果：

其他
case…esac形式
类似于C/C++中的switch语句。

命令格式

case $变量名称 in
    值1)
        语句1
        语句2
        ...
        ;;  # 类似于C/C++中的break
    值2)
        语句1
        语句2
        ...
        ;;
    *)  # 类似于C/C++中的default
        语句1
        语句2
        ...
        ;;
esac
示例：

a=4

case $a in
    1)
        echo ${a}等于1
        ;;  
    2)
        echo ${a}等于2
        ;;  
    3)                                                
        echo ${a}等于3
        ;;  
    *)
        echo 其他
        ;;  
esac
输出结果：其他

```shell
#！ /bin/bash

a=1
b=2
if expr $a \!= $b
then 
        echo hhh
fi

a=3
b=4

if ! [ "$a" -lt "$b" ]
then
        echo ${a}不小于${b}
else
        echo ${a}小于${b}
fi

#test "acvv" -lt "sad" && echo yes || echo no

read -p "请输入一个整数:" num

if [ $num -gt 1 ] && [ $num -lt 7 ]
then
        echo $num大于1小于7
elif [ $num -eq 8 ]
then 
        echo $num等于8
else
        echo GG
fi

case $a in
    1)
        echo ${a}等于1
        ;;
    2)
        echo ${a}等于2
        ;;
    3)
        echo ${a}等于3
        ;;
    *)
        echo 其他
        ;;
esac

结果：
1
hhh
3小于4
请输入一个整数:3
3大于1小于7
3等于3

```

### 循环

**for…in…do…done**
命令格式：

for var in val1 val2 val3
do
    语句1
    语句2
    ...
done
示例1，输出a 2 cc，每个元素一行：

for i in a 2 cc
do
    echo $i
done
示例2，输出当前路径下的所有文件名，每个文件名一行：

for file in `ls`
do
    echo $file
done
示例3，输出1-10

for i in $(seq 1 10)
do
    echo $i
done
示例4，使用{1..10} 或者 {a..z}

for i in {a..z}
do
    echo $i
done

**for ((…;…;…)) do…done**
命令格式：

for ((expression; condition; expression))
do
    语句1
    语句2
done
示例，输出1-10，每个数占一行：

for ((i=1; i<=10; i++))
do
    echo $i
done

while…do…done循环
命令格式：

**while condition**
do
    语句1
    语句2
    ...
done
示例，文件结束符为Ctrl+d，输入文件结束符后read指令返回false。

while read name
do
    echo $name
done

**break命令**
跳出当前一层循环，注意与C/C++不同的是：break不能跳出case语句。

;;跳出case，break跳出for

示例

```shell
#! /bin/bash

for i in a 22 cc
do
    echo $i
done

for i in `ls`
do
    echo $i
done

for i in `seq 1 10`
do
    echo $i
done

for i in {a..z}
do
    echo $i
done

for((i=0; i<=10; i++))
do
    echo `expr $i + 1 `
done

while read name
do
    echo $name
done

until [ "${word}" == "yes" ] || [ "${word}" == "YES" ]
do
    read word
done                                                                                                                                                                                                              

while read name
do
    for i in `seq 1 10`
    do
        case $i in
            8)
                break
                ;;
            *)
                echo $i
                ;;
        esac
    done
done


```

**continue命令**

```shell
for i in `seq 1 10`
do
    if [ `expr $i % 2` -eq 0 ]
    then-
        continue
    fi
    echo $i
done   
```

### 函数

bash中的函数类似于C/C++中的函数，但return的返回值与C/C++不同，返回的是exit code，取值为0-255，0表示正常结束。

如果想获取函数的输出结果，可以通过echo输出到stdout中，然后通过$(function_name)来获取stdout中的结果。

函数的return值可以通过$?来获取。

命令格式：

[function] func_name() {  # function关键字可以省略
    语句1
    语句2
    ...
}
不获取 return值和stdout值
示例

func() {
    name=yxc
    echo "Hello $name"
}

func
输出结果：

Hello yxc
获取 return值和stdout值
不写return时，默认return 0。

示例




    func() {
        name=yxc
        echo "Hello $name"
        return 123
    }
    output=$(func)
    ret=$?
    
    echo "output = $output"
    echo "return = $ret"
    输出结果：
    
    output = Hello yxc
    return = 123



函数的输入参数
在函数内，$1表示第一个输入参数，$2表示第二个输入参数，依此类推。

注意：函数内的$0仍然是文件名，而不是函数名。

示例：



    func() {  # 递归计算 $1 + ($1 - 1) + ($1 - 2) + ... + 0
        word=""
        while [ "${word}" != 'y' ] && [ "${word}" != 'n' ]
        do
            read -p "要进入func($1)函数吗？请输入y/n：" word
        done
    if [ "$word" == 'n' ]
    then
        echo 0
        return 0
    fi  
    
    if [ $1 -le 0 ] 
    then
        echo 0
        return 0
    fi  
    
    sum=$(func $(expr $1 - 1))
    echo $(expr $sum + $1)
    }
    echo $(func 10)
    输出结果：
    
    55



函数内的局部变量
可以在函数内定义局部变量，作用范围仅在当前函数内。

可以在递归函数中定义局部变量。

命令格式：

local 变量名=变量值
例如：

#! /bin/bash

func() {
    local name=yxc
    echo $name
}
func

echo $name
输出结果：

yxc

### Exit

exit命令用来退出当前shell进程，并返回一个退出状态；使用$?可以接收这个退出状态。

exit命令可以接受一个整数值作为参数，代表退出状态。如果不指定，默认状态值是 0。

exit退出状态只能是一个介于 0~255 之间的整数，其中只有 0 表示成功，其它值都表示失败。

```shell

if [ $# -ne 1 ]
then
    echo "not"
    exit 1
else                     
    echo "yes"
    exit 1
fi

```

### 重定向

每个进程默认打开3个文件描述符：

stdin标准输入，从命令行读取数据，文件描述符为0
stdout标准输出，向命令行输出数据，文件描述符为1
stderr标准错误输出，向命令行输出数据，文件描述符为2
可以用文件重定向将这三个文件重定向到其他文件中。

```shell
重定向命令列表
命令	说明
command > file	将stdout重定向到file中
command < file	将stdin重定向到file中
command >> file	将stdout以追加方式重定向到file中
command n> file	将文件描述符n重定向到file中
command n>> file	将文件描述符n以追加方式重定向到file中
输入和输出重定向
echo -e "Hello \c" > output.txt  # 将stdout重定向到output.txt中
echo "World" >> output.txt  # 将字符串追加到output.txt中

read str < output.txt  # 从output.txt中读取字符串

echo $str  # 输出结果：Hello World
同时重定向stdin和stdout
创建bash脚本：

#! /bin/bash

read a
read b

echo $(expr "$a" + "$b")
创建input.txt，里面的内容为：

3
4
执行命令：

acs@9e0ebfcd82d7:~$ chmod +x test.sh  # 添加可执行权限
acs@9e0ebfcd82d7:~$ ./test.sh < input.txt > output.txt  # 从input.txt中读取内容，将输出写入output.txt中
同时./test.sh > out.txt < input.txt
acs@9e0ebfcd82d7:~$ cat output.txt  # 查看output.txt中的内容
7

//标准输入是0，标准输出是1
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt/acwing# ./test.sh 1 > out.txt 0 < input.txt 
root@iZ2ze34hcm5zr56umjmbfwZ:/mnt/acwing# cat out.txt 
3

```





### 引入外部搜索

类似于C/C++中的include操作，bash也可以引入其他文件中的代码。

语法格式：

. filename  # 注意点和文件名之间有一个空格

或

source filename
示例
创建test1.sh，内容为：

#! /bin/bash

name=yxc  # 定义变量name
然后创建test2.sh，内容为：

#! /bin/bash

source test1.sh # 或 . test1.sh

echo My name is: $name  # 可以使用test1.sh中的变量
执行命令：

acs@9e0ebfcd82d7:~$ chmod +x test2.sh 
acs@9e0ebfcd82d7:~$ ./test2.sh 
My name is: yxc

## ssh

### ssh登录

```shell
acwing 查看密码：homework 4 getinfo
User: acs_1249
HostName: 123.57.47.211
Password: 5483a9d6
ssh acs_1249@123.57.47.211
5483a9d6
基本用法
远程登录服务器：

ssh user@hostname
user: 用户名
hostname: IP地址或域名
第一次登录时会提示：

The authenticity of host '123.57.47.211 (123.57.47.211)' can't be established.
ECDSA key fingerprint is SHA256:iy237yysfCe013/l+kpDGfEG9xxHxm0dnxnAbJTPpG8.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
输入yes，然后回车即可。
这样会将该服务器的信息记录在~/.ssh/known_hosts文件中。

然后输入密码即可登录到远程服务器中。

默认登录端口号为22。如果想登录某一特定端口：

ssh user@hostname -p 22
配置文件
创建文件 ~/.ssh/config。

然后在文件中输入：

Host myserver1
    HostName IP地址或域名
    User 用户名

Host myserver2
    HostName IP地址或域名
    User 用户名
之后再使用服务器时，可以直接使用别名myserver1、myserver2。

密钥登录
创建密钥：

ssh-keygen
然后一直回车即可。

执行结束后，~/.ssh/目录下会多两个文件：

id_rsa：私钥
id_rsa.pub：公钥
之后想免密码登录哪个服务器，就将公钥传给哪个服务器即可。

例如，想免密登录myserver服务器。则将公钥中的内容，复制到myserver中的~/.ssh/authorized_keys文件里即可。

也可以使用如下命令一键添加公钥：

ssh-copy-id myserver
执行命令
命令格式：

ssh user@hostname command
例如：

ssh user@hostname ls -a
或者

 单引号中的$i可以求值
ssh myserver 'for ((i = 0; i < 10; i ++ )) do echo $i; done'
或者
双引号里的值先在本地转义
 双引号中的$i不可以求值
ssh myserver "for ((i = 0; i < 10; i ++ )) do echo $i; done"


```

### scp传文件

```shell
基本用法:不仅能往出传还能往回传
命令格式：

scp source destination
将source路径下的文件复制到destination中

一次复制多个文件：

scp source1 source2 destination
复制文件夹：

scp -r ~/tmp myserver:/home/acs/
将本地家目录中的tmp文件夹复制到myserver服务器中的/home/acs/目录下。

scp -r ~/tmp myserver:homework/
将本地家目录中的tmp文件夹复制到myserver服务器中的~/homework/目录下。

scp -r myserver:homework .
将myserver服务器中的~/homework/文件夹复制到本地的当前路径下。

指定服务器的端口号：

scp -P 22 source1 source2 destination
注意： scp的-r -P等参数尽量加在source和destination之前。

使用scp配置其他服务器的vim和tmux
scp ~/.vimrc ~/.tmux.conf myserver:
 

```



## git

1. git教程
代码托管平台：git.acwing.com

1.1. git基本概念
工作区：仓库的目录。工作区是独立于各个分支的。
暂存区：数据暂时存放的区域，类似于工作区写入版本库前的缓存区。暂存区是独立于各个分支的。
版本库：存放所有已经提交到本地仓库的代码版本
版本结构：树结构，树中每个节点代表一个代码版本。
1.2 git常用命令

```shell
git config --global user.name xxx：设置全局用户名，信息记录在~/.gitconfig文件中
git config --global user.email xxx@xxx.com：设置全局邮箱地址，信息记录在~/.gitconfig文件中
git init：将当前目录配置成git仓库，信息记录在隐藏的.git文件夹中
git add XX：将XX文件添加到暂存区
git add .：将所有待加入暂存区的文件加入暂存区
git rm --cached XX：将文件从仓库索引目录中删掉
git commit -m "给自己看的备注信息"：将暂存区的内容提交到当前分支
git status：查看仓库状态
git restore -- staged XX 将暂存区的文件暂时从暂存区撤出
git diff XX：查看XX文件相对于暂存区修改了哪些内容
git log：查看当前分支的所有版本   git log --pretty=online 在一行显示
git reflog：查看HEAD指针的移动历史（包括被回滚的版本）
git reset --hard HEAD^ 或 git reset --hard HEAD~：将代码库回滚到上一个版本
git reset --hard HEAD^^：往上回滚两次，以此类推
git reset --hard HEAD~100：往上回滚100个版本
git reset --hard 版本号：回滚到某一特定版本
git checkout — XX或git restore XX：将XX文件尚未加入暂存区的修改全部撤销 【还有将工作区的文件与暂存区进行同步】 
git remote remove origin 删除本地对应的远程连接
git remote add origin git@git.acwing.com:xxx/XXX.git：将本地仓库关联到远程仓库
git push -u origin branch_name( 第一次需要-u以后不需要)：将当前分支推送到远程仓库
git push origin branch_name：将本地的某个分支推送到远程仓库
git clone git@git.acwing.com:xxx/XXX.git：将远程仓库XXX下载到当前目录下
git checkout -b branch_name：创建并切换到branch_name这个分支 
git branch：查看所有分支和当前所处分支
git checkout branch_name：切换到branch_name这个分支
git merge branch_name：将分支branch_name合并到当前分支上
git branch -d branch_name：删除本地仓库的branch_name分支
git branch branch_name：创建新分支
git push --set-upstream origin branch_name：设置本地的branch_name分支对应远程仓库的branch_name分支
git push -d origin branch_name：删除远程仓库的branch_name分支
git pull：将远程仓库的当前分支与本地仓库的当前分支合并
git pull origin branch_name：将远程仓库的branch_name分支与本地仓库的当前分支合并
git branch --set-upstream-to=origin/branch_name1 branch_name2：将远程的branch_name1分支与本地的branch_name2分支对应
git checkout -t origin/branch_name 将远程的branch_name分支拉取到本地
git stash：将工作区和暂存区中尚未提交的修改存入栈中
git stash apply：将栈顶存储的修改恢复到当前分支，但不删除栈顶元素
git stash drop：删除栈顶存储的修改
git stash pop：将栈顶存储的修改恢复到当前分支，同时删除栈顶元素
git stash list：查看栈中所有元素

```









## thrift

![](C:\Users\18068\Downloads\uTools_1643251493972.png)

编译  `g++ -c main.cpp match_server/*.cpp`  所有的cpp编译生成.o文件在当前目录下

链接 g++ *.o -o main -lthrift  链接所有.o文件用 main启动

