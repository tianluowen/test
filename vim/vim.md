vim 设置

> ***Edit Text at the Speed of Thought  以思维的速度来编辑文本***
>
> ***无论是 插件，自定义快捷键，还是比较少见的操作 都应该以提高编码生产力为准则***
>
> ***其中 自带操作 > 自定义快捷键 > 插件*** 



问题：

- <u>设置下行不自动注释，缩进就没了了</u>
- <u>进入一次插入模式后，当前行就不突出显示了</u>
- <u>SirVer/ultisnips 使用方式  自定义插入代码</u>



- <u>上下行 各留 7 个位置 set scrolloff</u>
- <u>设置 term 256 色 同主题</u> 
- <u>当前行背景色  每行 80 个字符，自动标注</u> 
- <u>最下面的文件属性设置 code utf-8 位置</u>
- <u>相对行号 相对行号 同 绝对行号的转换</u>
- <u>当前文件函数名 变量名的显示</u> 
- <u>文件列表的显示 taglist</u>
- <u>设置换行 不自动添加注释  set paste</u>
- <u>管理插件的教程 同 手动安装插件</u>
- <u>todo 等词高亮</u>
- <u>c，cpp 文件自动插入头文件   新建文件 自动添加信息</u>
- <u>左边文件列表和函数名和变量名</u>
- <u>取消查询高亮</u>
- <u>文件跳转</u>
- <u>ctrl + hjkl 当前位置切换</u>
- <u>扩展 f 和 t 在多行之间跳转</u>
- <u>标签页显示 路径</u>
- <u>mark.vim  标记高亮显示</u>  需要支持ruby特性
- <u>tab切换标签 标准模式下  插入模式下  跳出括号</u>
- 每行显示固定的字符长度
- 自动补全 智能语法提示 自动补全，提示结构体



- 部分插件 
  - <u>vim-wakatime 记录操作日志 了解自己</u>   api-key `a7bfa4b7-e2eb-4b11-93fa-c6993cbab71f`  https://wakatime.com/
  - <u>vim-colorschemes 配色主题</u> 
  - <u>vim-easy-aligh '=' 对齐</u>
  - <u>nerdtree，用来浏览文档树</u>
  - <u>tabular</u>
  - <u>tagbar</u>
  - <u>taglist</u>
  - <u>语法错误提示</u>  
  - <u>vim-autoformat 比如c++，会自动调用诸如astyle, clang-format来对代码进行美化</u>
  - <u>textobj-entire 增加 ie 同 ae 全局作用</u> 
  - <u>Plugin 'luochen1990/rainbow  " 彩虹色括号增强版</u>
  - <u>字体 微软雅黑 consol 字体</u>   https://github.com/yakumioto/YaHei-Consolas-Hybrid-1.12
  - ale 
  - F11 全屏
  - 一键编译
  - 自定义代码头文件



插件管理 plugin 使用设置

```shell
"*************************************************************************************
"*
"*                            Vundle Settings
"*
"*************************************************************************************
":PluginInstall 
":PluginClean
":PluginList
" 侦测文件类型，该Vundle使用新版本

set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

" 要安装某一个插件的时候 在 github 上找到该插件的位置，然后按照如下所示放到这里即可
" 使Vundle管理插件版本，必须
Plugin 'VundleVim/Vundle.vim'

" 所有添加插件放置在上面
call vundle#end()
```



文件类型插件和智能缩进

```shell
filetype off		  " 打开文件类型检测功能

" 智能插件
filetype plugin on    " 载入文件类型插件 添加该文件类型可以使用的所有插件
filetype indent on    " 为特定文件类型载入相关缩进文件 缩进设置
```



基本功能设置

```shell
" 上下行 各留 7 个位置
set scrolloff=7
" 回车后不自动添加注释
set paste
 


"---------------------------------------------
" 状态栏增强显示
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'

" 插件设置
set laststatus=2   " 设置下方的 bar 总是显示
let g:airline_theme='papercolor' "设置下方 bar 的显示主题 可以在文件中存放主题，然后设置
"---------------------------------------------

" 设置上下左右键位失效，强迫自己使用 hjkl
map <left> <nop>
map <up> <nop>
map <down> <nop>
map <right> <nop>
map <F1> <nop>
```



设置基本显示

```shell
set guifont="Courier 10 pitch:h10:cANSI"
let &titlestring = expand("%:p")
set notitle
set mouse=n
" t_Co terminal Color setting 256 色
set t_Co=256
syntax enable

" 设置配色主题
colorscheme mono
```





设置行号

```shell
"--------------------------------------------------------------------
" 设置相对行号，并制定快捷键 来回转换
set relativenmuber number
" au Focuslost * :set norelativenumber number
" au FocusGained * :set relativenumber
function! NumberToggle()
	if(&relativenumber == 1)
		set norelativenumber number
	else
		set relativenumber
	endif
endfunc

nnoremap <C-n>:call NumberToggle()<cr>
"-------------------------------------------------------------------- 
```



系统级别的键位映射

```shell
# 如何将 左 ctrl 键位 与 大小写键位 更换
# 打开 下面文件 里面是所有键位映射 
sudo vi /usr/share/X11/xkb/symbols/pc
```



终端同 vim 256 的设置

查看终端显示

```shell
tput colors  # 查看当前终端的显示方式
echo $TERM   # 
```

.bashrc 文件 设置 TERM 终端显示 256

```shell
#**************************************************************************************
#*
#*                           设置终端 256 色 
#*
#**************************************************************************************
if [ "$TERM" == "xterm" ]; then
export TERM=xterm-256color
fi
```



.vimrc 文件设置支持 256 

```SHELL
" t_Co即terminal Color之意
set t_Co=256 
```



vim 智能注释切换

```shell
"v"vim-commentary

" 为python和shell等添加注释
autocmd FileType python,shell,coffee set commentstring=#\ %s
" 修改注释风格
autocmd FileType java,c,cpp set commentstring=//\ %sim-commentary
" 为python和shell等添加注释
autocmd FileType python,shell,coffee set commentstring=#\ %s
" 修改注释风格
autocmd FileType java,c,cpp set commentstring=//\ %s
```

