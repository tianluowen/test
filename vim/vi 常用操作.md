`vi / vim` 是一款文本编辑器，为了方便编写代码，主要需要掌握 移动、选择、删除、复制等常用的操作。主要使用的模式有普通模式、插入模式、选择模式、命令行模式。

## vim 常用模式

### 1、**Normal Mode** 普通模式

功能：在这种模式下可以移动光标等。
进入：默认进入 `vim` 之后，处于这种模式。在其他模式下按ESC后进入此模式。

> 注意：
>
> 在一般的编辑器下，当你需要copy一段文字的时候，你需要使用 `Ctrl` 键，比如：`Ctrl-C`。也就是说，Ctrl键就好像功能键一样，当你按下了功能键Ctrl后，C就不在是C了，而且就是一个命令或是一个快键键。
>
> **在VIM的Normal模式下，所有的键就是功能键了**



### 2、**Visual Mode** 可视模式

功能：在这种模式下可以选定一些字符、行、多列。
进入：在普通模式下，按 v 进入可视模式，按 V 进入可视行模式，按 `ctrl + v` 进入可视块模式。



### 3、**Insert Mode** 插入模式

功能：在这种模式下可以编辑输入等。
进入：普通模式下，可以按 `i、a、o、s` 等进入。



### 4、**Command-Line** 命令行模式

功能：可以输入各种命令。
进入：普通模式下按冒号 `:` 进入。



### 5、**Ex Mode** `Ex` 模式

功能：多行的 `Command-Line` 模式。
进入：普通模式下按 `Q` 进入 `Ex` 模式。



### 6、**Select Mode** 选择模式

功能：在 `vim`下常用的模式，用鼠标拖选区域的时候，就进入了选择模式。
和可视模式不同的是，在这个模式下，选择完了高亮区域后，敲任何按键就直接输入并替换选择的文本了。
进入：普通模式下，可以按 `gh` 进入。



> 注意：
>
> 



**参考教程：https://coolshell.cn/articles/5426.html**

**vim 配置教程：http://www.wklken.me/posts/2013/06/11/linux-my-vim.html**

**vim 插件管理：https://www.cnblogs.com/zzqcn/p/4660615.html#_label2**

**vim 插件查找：https://vimawesome.com/**

**vim 从入门到精通：https://github.com/wsdjeg/vim-galore-zh_cn/blob/master/README.md**



## vim 基本操作

### 打开/保存/退出/改变文件

```
vi -t main 			存在 ctags 文件时，可以直接打开 main 函数所在文件中定义的位置
vi filename +78		直接打开时，光标跳转到 78 行行首
vi filename +		打开时光标处于最后一行
vi -r filename		在上次正用 vi 编辑时发生意外退出，恢复

命令行模式下
:q		退出
ZZ		不需要输入冒号回车，直接退出 （注意：是大写的 ZZ）
:w		保存
:x		保存退出
:wq		保存退出
:!		强制执行,可以暂时退出，按回车键又进入文件编辑状态
:q!		
:n filename  	新建文件 new
:w filename  	另存为，但是仍然编辑当前文件，并不会切换文件
:e filename 	切换文件，但是当前文件必须保存
:e. 			打开 vi 内置文件浏览，切换别的文件
:sp filename 	横向增加分屏 split
:vsp filename  	纵向增加分屏 vertical split
ctrl + w		切换各个编辑中的窗口，窗口的切换先按 ctrl + w
:saveas <path/to/file> 		另存为 <path/to/file>

:bn 
:bp 			你可以同时打开很多文件，使用这两个命令来切换下一个或上一个文件
```



#### 普通模式：

```
ctrl + g 	显示当前文件名，和光标所在的百分比位置
=			格式化代码
gg=G		格式化所有代码
```



### 移动和选择：

```
space 		将光标向后移动一个字符
enter		将光标移到下一行的第一个字符处
-			光标跳转到上一行的第一个字符处
+			光标跳转到下一行的第一个自付处
gg 			光标跳转到文件开始处
G			光标跳转到文件结束处
number+gg	光标跳转到 number 行
number+G	同上，光标跳转到 number 行
:number		同上，光标跳转到 number 行
gD			跳转到局部变量的定义处

``			跳转到光标上次所在的位置
''			跳转到光标上次所在的行首
m+(a-Z)		给某个位置做标记
`+(a-Z)		跳转到标记的位置
'+(a-Z)		跳转到标记的行首

h			左
j			下
k			上
l			右 

H               移动光标到屏幕的首行	head
M              	移动光标到屏幕的中间一行  	middle
L               移动光标到屏幕的尾行 	low

ctrl + f        向下翻页 同 page down   	forword
ctrl + b        向上翻页 同 page up		back
ctrl + d        向下翻半页 此比较有用 	 down
ctrl + u        向上翻半页 此比较有用		 up
ctrl + e        向下翻一行	
ctrl + y        向上一行

%	 	跳转到匹配的括号处 大括号和小括号都可以（(, {, [）
{      	转到上一个空行
}   	转到下一个空行
[   	转到上一个位于第一列的“{”
]   	转到下一个位于第一列的“}”
```



### 行内移动

```
w   移动光标到下一个单词开头 word
e   如果光标不在当前所在的单词的末尾，将光标移动到当前单词的末尾，如果光标在当前单词的末尾，
	将光标移动到下一个单词的末尾
W	将光标移动到下一个开头	以 空白符为分隔
E	将光标移动到下一个末尾	以 空白符为分隔

b   移动光标到上一个单词开头 back
B	移动光标到上一个开头 以空白符为分隔		

0               移动光标到本行开头
home 			移动光标到本行开头
^(shift + 6)	移动光标到本行第一个不是blank字符的位置
				(所谓blank字符就是空格，tab，换行，回车等)
$(shift + 4)   	移动光标到本行结尾处
end 			移动光标到本行结尾处
-				移动光标到上一行的第一个不是blank字符的位置
——（shift + -)  移动光标到本行的第一个不是blank字符的位置 
g——（g+shift + -) 	到本行最后一个不是blank字符的位置
fa  			到下一个为a的字符处，你也可以fs到下一个为s的字符。
t, 				到逗号前的第一个字符。逗号可以变成其它字符
3fa 			在当前行查找第三个出现的a。
F T				和 f 和 t 一样，只不过是相反方向
dt"  			删除所有的内容，直到遇到双引号 —— " 双引号可以是别的字符
df"				删除到 " 的所有字符，包括 " 字符
```



### 插入

```
i		在光标所在的字符前开始插入 insert
I		在光标所在的行首开始插入，如果行首有空格则在空格之后插入 insert
a		在光标所在的字符后开始插入 add
A		在光标所在的行尾开始插入 add	
o		在光标所在的行的下面另起一行插入 online
O		在光标所在的行的上面另起一行插入 online
s		删除光标所在的字符并开始插入 
S		删除光标所在的行并开始插入
```



### 编辑操作：复制删除和粘贴，删除本质上就是剪贴

```
u				撤销，可以一直撤销到打开文件时的状态 undo
ctrl + r		恢复撤销的命令 redo <C-r>

x				删除光标所在的字符，或者选中的文字 cut
d + 移动命令	 删除当前光标至移动命令之间对应的内容 delete
		eg：
			dw 		删除光标当前位置到词尾
			d0 		删除光标到一行的起始位置
			d} 		删除光标到段结尾
			d代码行G 从光标所在的位置删除到指定代码行之间的所有字符，包括那一行
			d'a 	删除光标至标记 a 之间的所有字符 
dd		删除一行，就是剪切
D		删除至行尾
nx		执行 n 次 x 命令，删除当前光标后面的 n 个字符
ndd		执行 n 次 dd 命令，删除光标所在行至后面的 n 行
dnd     执行 n 次 dd 命令，删除光标所在行至后面的 n 行

y + 移动命令	 复制当前光标至移动命令之间的所有内容
yy				复制当前光标所在的行	
nyy				执行 n 次 yy 命令，复制光标所在行至后面的 n 行
yny				执行 n 次 yy 命令，复制光标所在行至后面的 n 行

p		粘贴，将粘贴板中的内容粘贴到光标所再的位置

r		替换当前字符，只能替换一个字符然后就会自己退出替换模式 replace
R		替换当前行光标后的字符，进入替换模式，可以一次替换光标后面的字符 replace
```



### 普通模式下 缩进：

```
>> 		向右缩进 可视行模式下只需要一个 >
<<		向左缩进 可视行模式下只需要一个 <
.		重复上次修改的命令
```



### 查找 替换命令：

```
查找
:/str	查找字符串的位置，查到后按 n 查找字符串下一个出现的位置，N查找字符串所在的上一个位置 从文件
		结尾处开始搜索
:?str	查找字符串的位置，查到后按 n 查找字符串下一个出现的位置，N查找字符串所在的上一个位置 从文件
		开头处开始搜索
		使用 vim 搜索字符串时会导致所查找的字符串高亮，可以在命令行下 :noh :nohlsearch :set
        nohlsearch :set noh 都可以，意思为（no highlight search 缩写）
#		向上查找当前光标所在的单词
*		向下查找当前光标所在的单词
n		跳转到查找的下一个结果 注意：使用 # 查找时，按下 n 会向文件前面跳转
N		跳转到查找的上一个结果


替换
:%s/str1/str2/g		全局替换 将 str1 全部替换为 str2 
:%s/str1/str2/g		先远中要替换文字的范围，将选中范围内的 str1 全部替换为 str2
:%s/str1/str2/gc	替换字符的时候，会有提示，推荐使用
	y	替换 yes
	n	不替换 no
	a	替换全部 all
 	l	最后一个，并把光标移动到行首 last 
	^E	向下滚屏
	^Y	向上滚屏
	q	退出替换 quit
```



### 出现 `.filename.swp` 解决方法

```
vi -r filename	# 第一种
vi filename 	# 第二种
	r 还原上次退出时的文件编辑状态
	d 删除对应的 .filename.swp
```



## vim 一些操作实例

### 编辑命令和数字连用 输入 N 个相同的字符

1. 输入 `10`，表示要重复 `10` 次
2. 输入 `i` 进入编辑模式
3. 输入 `*` 也就是要重复的文字
4. 按下 `ESC` 也就是返回到普通模式，返回后 `vi` 就会把 `2`，`3` 步骤在执行 `9` 次，算上第一次，总共是 `10` 次




### 利用可视块给多行代码增加注释

1. 移动到要添加注释的第一行代码，按 `^` 来到行首
2. 按 `CTRL + v` 进入可是款 模式
3. 使用 `j` 向下连续远中要添加的代码
4. 输入 `I` 进入编辑模式，注意：一定要使用 `I`
5. 在行首插入注释符号 `//`
6. 按下 `ESC` 也就是返回到普通模式，返回之后 `vi` 会在之前远中的每一行代码前插入 `//`



### 删除多行注释

1. 移动到要添加注释的第一行代码，按 `^` 来到行首
2. 按 `CTRL + v` 进入可视块模式
3. 使用 `j` 向下连续远中，使用 `l` 向右选中要删除的地方
4. 按下 `x` 或者 `d` 删除

> 注意： 必须在可视块模块下才生效



## vim 键位图

![vim 键位图](https://gitee.com/tian_luowen/picture-bed/raw/master/编程工具的使用/vim/vi 常用操作/vim键盘操作图.png)



## vim 配置

### vim 配置文件位置

```
.vimrc    	vim 基本配置信息
.vim		vim 各种插件信息
	colors	vim 各种主题存放的位置
	bundle	vim 各种插件存放的位置
```



### vimrc 文件的设置

```
定义变量位置描述
                (nothing) In a function: local to a function; otherwise: global 
buffer-variable    b:     Local to the current buffer.                          
window-variable    w:     Local to the current window.                          
tabpage-variable   t:     Local to the current tab page.                        
global-variable    g:     Global.                                               
local-variable     l:     Local to a function.                                  
script-variable    s:     Local to a :source'ed Vim script.                     
function-argument  a:     Function argument (only inside a function).           
vim-variable       v:     Global, predefined by Vim.

map 键位映射
```





### vim 插件教程

介绍两个东西

- 插件：配合 vim 实现更强大的功能 
- 管理插件的软件：为了方便管理，有一个专门的插件软件，来实现对其他插件的快速安装，卸载等功能



### Vundle：vim 插件管理器













