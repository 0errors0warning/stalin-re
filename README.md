# stalin-re
斯大林正则表达式解释器
## 正则表达式是甚么
正则表达式只是一个没有长度限制的字符串。这些字符串实际上都是微型计算机程序。正则表达式的语法，实际上是一种轻量级、简洁、适用于特定领域的编程语言。
- 正则表达式可以分解为一个指令序列，比如“先找到这样的字符，再找到那样的字符，再从中找到一个字符。。。”
- 每一个正则表达式都有输入（文本）和输出（匹配规则的输出，有时是修改后的文本）
- 正则表达式有可能出现语法错误——不是所有的字符串都是正则表达式
## 正则表达式的基础语法
### 字符
 只能匹配自身
- 可以在元字符前加“\”，这时元字符就会被当作普通字符处理。
### 元字符
 代表了一些特殊的匹配规则
#### `.`
 代表这个位置可以是任何字符
- .talin     可以匹配 atalin,btalin,.......stalin.
- ......talin      可以匹配114514talin 191981talin
#### `[]`
 可以匹配[]中的任何一个字符
- []中的元素会自动去重
-- [as]talin  stalin or atalin
- []中使用短横线表示范围如[a-z]
#### `^`
[]内部前面加字符表示反义,不匹配
- [^s]talin 不匹配stalin
[]外部表示匹配行的开始
#### `\d`
- 匹配任何一个数字
#### `\w`
- 匹配一个数字或字母字符
#### `\s`
- 匹配一个空字符，（空格，制表符，回车，换行）
#### `\D`
- 匹配任何一个非数字
#### `\W`
- 匹配一个非数字非字母字符
#### `\S`
- 匹配一个非空字符
#### `{}`
匹配重复字符
- sta{3}lin         匹配staaalin
- [sta][sta][sta]lin          等价于[sta]{3}lin
- sta{1,2}lin           匹配stalin,staalin(指定范围）
- sta{1，}lin          匹配中间有最多a的stalin（范围可以是开区间）
#### `？`
等价于{0,1}
- x？：x这个字符有没有都行
见好就收，后面加问号表示最短匹配
#### `*`
等价于{0,}
- a* 匹配最长的a串，没a也行
#### `+`
等价于{1,}
- a+ 匹配最长的a串，要有a

#### `｜`
选择匹配
- stalin｜Bukharin           斯大林或布哈林（值得庆幸的是，本位面不是布哈林）
#### `\b`
匹配一个单词分隔符           匹配一个六字母单词，比如stalin
- \b\w{5}\b         
#### `$`
匹配行的结束
#### `（）`
划定捕获组
#### `\1`
第一个捕获组返回值，其余以此类推
