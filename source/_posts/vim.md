---
title: vim文档
date: 2024-07-24 10:56:42
cover: https://img.hehonglei.cn/img/0005.jpg
tags: 
  - 文档
categories: 
  - documents
---
{% span  logo red h1 left, 本文记录了常用VIM相关操作 %}

<table>
    <tr style="background-color: #8d8d8d;">
        <td>移动光标的方法 </td>
        <td></td>
    </tr>
    <tr>
        <td>h 或 向左箭头键(←)</td>
        <td>光标向左移动一个字符 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>j 或 向下箭头键(↓)</td>
        <td>光标向下移动一个字符 </td>
    </tr>
    <tr>
        <td>k 或 向上箭头键(↑)</td>
        <td>光标向上移动一个字符 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>l 或 向右箭头键(→)</td>
        <td>光标向右移动一个字符 </td>
    </tr>
    <tr>
        <td>如果你将右手放在键盘上的话，你会发现 hjkl 是排列在一起的，因此可以使用这四个按钮来移动光标。 如果想要进行多次移动的话，例如向下移动 30 行，可以使用 &quot;30j&quot; 或 &quot;30↓&quot; 的组合按键， 亦即加上想要进行的次数(数字)后，按下动作即可！ </td>
        <td></td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>[Ctrl] + [f]</td>
        <td>屏幕『向下』移动一页，相当于 [Page Down]按键 (常用) </td>
    </tr>
    <tr>
        <td>[Ctrl] + [b]</td>
        <td>屏幕『向上』移动一页，相当于 [Page Up] 按键 (常用) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>[Ctrl] + [d]</td>
        <td>屏幕『向下』移动半页 </td>
    </tr>
    <tr>
        <td>[Ctrl] + [u]</td>
        <td>屏幕『向上』移动半页 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>+</td>
        <td>光标移动到非空格符的下一行 </td>
    </tr>
    <tr>
        <td>-</td>
        <td>光标移动到非空格符的上一行 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>n&lt;space&gt;</td>
        <td>那个 n 表示『数字』，例如 20 。按下数字后再按空格键，光标会向右移动这一行的 n 个字符。例如 20&lt;space&gt; 则光标会向后面移动 20 个字符距离。 </td>
    </tr>
    <tr>
        <td>0 或功能键[Home]</td>
        <td>这是数字『 0 』：移动到这一行的最前面字符处 (常用) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>$ 或功能键[End]</td>
        <td>移动到这一行的最后面字符处(常用) </td>
    </tr>
    <tr>
        <td>H</td>
        <td>光标移动到这个屏幕的最上方那一行的第一个字符 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>M</td>
        <td>光标移动到这个屏幕的中央那一行的第一个字符 </td>
    </tr>
    <tr>
        <td>L</td>
        <td>光标移动到这个屏幕的最下方那一行的第一个字符 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>G</td>
        <td>移动到这个档案的最后一行(常用) </td>
    </tr>
    <tr>
        <td>nG</td>
        <td>n 为数字。移动到这个档案的第 n 行。例如 20G 则会移动到这个档案的第 20 行(可配合 :set nu) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>gg</td>
        <td>移动到这个档案的第一行，相当于 1G 啊！ (常用) </td>
    </tr>
    <tr>
        <td>n&lt;Enter&gt;</td>
        <td>n 为数字。光标向下移动 n 行(常用)</td>
    </tr>
</table>
<table>
    <tr style="background-color: #8d8d8d;">
        <td>搜索替换 </td>
        <td></td>
    </tr>
    <tr>
        <td>/word</td>
        <td>向光标之下寻找一个名称为 word 的字符串。例如要在档案内搜寻 vbird 这个字符串，就输入 /vbird 即可！ (常用) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>?word</td>
        <td>向光标之上寻找一个字符串名称为 word 的字符串。 </td>
    </tr>
    <tr>
        <td>n</td>
        <td>这个 n 是英文按键。代表重复前一个搜寻的动作。举例来说， 如果刚刚我们执行 /vbird 去向下搜寻 vbird 这个字符串，则按下 n 后，会向下继续搜寻下一个名称为 vbird 的字符串。如果是执行 ?vbird 的话，那么按下 n 则会向上继续搜寻名称为 vbird 的字符串！ </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>N</td>
        <td>这个 N 是英文按键。与 n 刚好相反，为『反向』进行前一个搜寻动作。 例如 /vbird 后，按下 N 则表示『向上』搜寻 vbird 。 </td>
    </tr>
    <tr>
        <td>使用 /word 配合 n 及 N 是非常有帮助的！可以让你重复的找到一些你搜寻的关键词！ </td>
        <td></td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>:n1,n2s/word1/word2/g</td>
        <td>n1 与 n2 为数字。在第 n1 与 n2 行之间寻找 word1 这个字符串，并将该字符串取代为 word2 ！举例来说，在 100 到 200 行之间搜寻 vbird 并取代为 VBIRD 则： </td>
    </tr>
    <tr>
        <td>『:100,200s/vbird/VBIRD/g』。(常用) </td>
        <td></td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>:1,$s/word1/word2/g 或 :%s/word1/word2/g</td>
        <td>从第一行到最后一行寻找 word1 字符串，并将该字符串取代为 word2 ！(常用) </td>
    </tr>
    <tr>
        <td>:1,$s/word1/word2/gc 或 :%s/word1/word2/gc</td>
        <td>从第一行到最后一行寻找 word1 字符串，并将该字符串取代为 word2 ！且在取代前显示提示字符给用户确认 (confirm) 是否需要取代！(常用)</td>
    </tr>
</table>
<table>
    <tr style="background-color: #8d8d8d;">
        <td>删除、复制与贴上 </td>
        <td></td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>x, X</td>
        <td>在一行字当中，x 为向后删除一个字符 (相当于 [del] 按键)， X 为向前删除一个字符(相当于 [backspace] 亦即是退格键) (常用) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>nx</td>
        <td>n 为数字，连续向后删除 n 个字符。举例来说，我要连续删除 10 个字符， 『10x』。 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>dd</td>
        <td>剪切游标所在的那一整行(常用)，用 p/P 可以粘贴。 </td>
    </tr>
    <tr>
        <td>ndd</td>
        <td>n 为数字。剪切光标所在的向下 n 行，例如 20dd 则是剪切 20 行(常用)，用 p/P 可以粘贴。 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>d1G</td>
        <td>删除光标所在到第一行的所有数据 </td>
    </tr>
    <tr>
        <td>dG</td>
        <td>删除光标所在到最后一行的所有数据 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>d$</td>
        <td>删除游标所在处，到该行的最后一个字符 </td>
    </tr>
    <tr>
        <td>d0</td>
        <td>那个是数字的 0 ，删除游标所在处，到该行的最前面一个字符 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>yy</td>
        <td>复制游标所在的那一行(常用) </td>
    </tr>
    <tr>
        <td>nyy</td>
        <td>n 为数字。复制光标所在的向下 n 行，例如 20yy 则是复制 20 行(常用) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>y1G</td>
        <td>复制游标所在行到第一行的所有数据 </td>
    </tr>
    <tr>
        <td>yG</td>
        <td>复制游标所在行到最后一行的所有数据 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>y0</td>
        <td>复制光标所在的那个字符到该行行首的所有数据 </td>
    </tr>
    <tr>
        <td>y$</td>
        <td>复制光标所在的那个字符到该行行尾的所有数据 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>p, P</td>
        <td>p 为将已复制的数据在光标下一行贴上，P 则为贴在游标上一行！ 举例来说，我目前光标在第 20 行，且已经复制了 10 行数据。则按下 p 后， 那 10 行数据会贴在原本的 20 行之后，亦即由 21 行开始贴。但如果是按下 P 呢？ 那么原本的第 20 行会被推到变成 30 行。 (常用) </td>
    </tr>
    <tr>
        <td>J</td>
        <td>将光标所在行与下一行的数据结合成同一行 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>c</td>
        <td>重复删除多个数据，例如向下删除 10 行，[ 10cj ] </td>
    </tr>
    <tr>
        <td>u</td>
        <td>复原前一个动作。(常用) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>[Ctrl]+r</td>
        <td>重做上一个动作。(常用) </td>
    </tr>
    <tr>
        <td>这个 u 与 [Ctrl]+r 是很常用的指令！一个是复原，另一个则是重做一次～ 利用这两个功能按键，你的编辑，嘿嘿！很快乐的啦！ </td>
        <td></td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>.</td>
        <td>不要怀疑！这就是小数点！意思是重复前一个动作的意思。 如果你想要重复删除、重复贴上等等动作，按下小数点『.』就好了！ (常用)</td>
    </tr>
</table>
<table>
    <tr style="background-color: #8d8d8d;">
        <td>进入输入或取代的编辑模式 </td>
        <td></td>
    </tr>
    <tr>
        <td>i, I</td>
        <td>进入输入模式(Insert mode)： </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>i 为『从目前光标所在处输入』， I 为『在目前所在行的第一个非空格符处开始输入』。 (常用) </td>
        <td></td>
    </tr>
    <tr>
        <td>a, A</td>
        <td>进入输入模式(Insert mode)： </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>a 为『从目前光标所在的下一个字符处开始输入』， A 为『从光标所在行的最后一个字符处开始输入』。(常用) </td>
        <td></td>
    </tr>
    <tr>
        <td>o, O</td>
        <td>进入输入模式(Insert mode)： </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>这是英文字母 o 的大小写。o 为在目前光标所在的下一行处输入新的一行； O 为在目前光标所在的上一行处输入新的一行！(常用) </td>
        <td></td>
    </tr>
    <tr>
        <td>r, R</td>
        <td>进入取代模式(Replace mode)： </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>r 只会取代光标所在的那一个字符一次；R会一直取代光标所在的文字，直到按下 ESC 为止；(常用) </td>
        <td></td>
    </tr>
    <tr>
        <td>上面这些按键中，在 vi 画面的左下角处会出现『--INSERT--』或『--REPLACE--』的字样。 由名称就知道该动作了吧！！特别注意的是，我们上面也提过了，你想要在档案里面输入字符时， 一定要在左下角处看到 INSERT 或 REPLACE 才能输入喔！ </td>
        <td></td>
    </tr>
    <tr style="background-color: #8d8d8d;"> 
        <td>[Esc]</td>
        <td>退出编辑模式，回到一般模式中(常用)</td>
    </tr>
</table>
<table>
    <tr style="background-color: #8d8d8d;">
        <td>指令行的储存、离开等指令 </td>
        <td></td>
    </tr>
    <tr>
        <td>:w</td>
        <td>将编辑的数据写入硬盘档案中(常用) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>:w!</td>
        <td>若文件属性为『只读』时，强制写入该档案。不过，到底能不能写入， 还是跟你对该档案的档案权限有关啊！ </td>
    </tr>
    <tr>
        <td>:q</td>
        <td>离开 vi (常用) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>:q!</td>
        <td>若曾修改过档案，又不想储存，使用 ! 为强制离开不储存档案。 </td>
    </tr>
    <tr>
        <td>注意一下啊，那个惊叹号 (!) 在 vi 当中，常常具有『强制』的意思～ </td>
        <td></td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>:wq</td>
        <td>储存后离开，若为 :wq! 则为强制储存后离开 (常用) </td>
    </tr>
    <tr>
        <td>ZZ</td>
        <td>这是大写的 Z 喔！如果修改过，保存当前文件，然后退出！效果等同于(保存并退出) </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>ZQ</td>
        <td>不保存，强制退出。效果等同于 :q!。 </td>
    </tr>
    <tr>
        <td>:w [filename]</td>
        <td>将编辑的数据储存成另一个档案（类似另存新档） </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>:r [filename]</td>
        <td>在编辑的数据中，读入另一个档案的数据。亦即将 『filename』 这个档案内容加到游标所在行后面 </td>
    </tr>
    <tr>
        <td>:n1,n2 w [filename]</td>
        <td>将 n1 到 n2 的内容储存成 filename 这个档案。 </td>
    </tr>
    <tr style="background-color: #8d8d8d;">
        <td>:! command</td>
        <td>暂时离开 vi 到指令行模式下执行 command 的显示结果！例如 </td>
    </tr>
    <tr>
        <td>『:! ls /home』即可在 vi 当中察看 /home 底下以 ls 输出的档案信息！</td>
        <td></td>
    </tr>
</table>



