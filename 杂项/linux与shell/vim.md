# vim

- esc**正常模式**：在文件中四处移动光标进行修改
- i**插入模式**：插入文本
- r**替换模式**：替换文本
- **可视化模式**（v一般，V行，C-v块）：选中文本块
- :**命令模式**：用于执行命令

## 基本操作

### 普通模式(esc退出其他模式)

- h j k l 控制光标 左 下 上 右 移动

- 光标快速移动motion

  | 0    | 至行首                 |
  | ---- | ---------------------- |
  | $    | 至行尾                 |
  | b    | 至光标所在单词的起始处 |
  | e    | 至光标所在单词的结尾处 |
  | w    | 至下一个单词的起始处   |
  | gg   | 至文件开头             |
  | G    | 至文件末尾             |

- x 删除单个字符（vim删除的同时会复制，相当于剪切）

  | d0   | 删除至行首           |
  | ---- | -------------------- |
  | d$   | 删除至行尾           |
  | db   | 删除至当前单词首     |
  | de   | 删除至当前单词尾     |
  | dw   | 删除至下个单词起始处 |
  | dd   | 删除所在行           |
  | dgg  | 删除至起始点         |
  | dG   | 删除至末尾           |
  | dh   | 删除光标前面一个字符 |
  | dj   | 删除光标后面一个字符 |
  | dk   | 删除所在行及上一行   |
  | dl   | 删除所在行及下一行   |

- 拷贝 y[数字]motion

- 数字

  - 数字+motion=重复多个 motion
  - d+数字+motion=删除多个motion范围

- 修饰语

  - `ci(` 改变当前括号内的内容

  - `ci[` 改变当前方括号内的内容
  - `da'` 删除一个单引号字符串， 包括周围的单引号

- 撤销

  - u撤销最后一次修改
  - U撤销整行的修改
  - ctrl+r 恢复撤销的内容

- 粘贴

  - p将内容粘贴到光标之后，P是光标之前
  - 如果是整行内容则会粘贴到上一行/下一行

- 替换 

  - r替换一个
  - 数字+r替换多个
  - R替换模式
    - 可连续替换
    - 输入退格会变回替换前的字符

- 修改

  - c[数字]motion
  - 相当于先删除然后进入修改模式
  - 组合键与删除类似
    - cc删除当前行并进入插入
    - 其它类似

- [数字]+>>(<<)缩进一或多行

  - 或按v进入可视模式，选中范围后<或>

- 命令行:

  - nohl 取消高亮
  - !+linux命令行
  - w+文件名 另存为（可以先在可视模式中选中一部分进行保存）
    - w仅保存（加！表示强制操作）

  - 退出
    
    - q! 退出不保存
    - ZZ(直接输入) 或 保存退出wq
    
  - r+文件名 合并文件（将指定文件插入进来）

  - set nu 显示行号

  - set paste 设置粘贴模式（esc退出）
    - 防止粘贴进来后格式混乱（如缩进错误）

- 搜索

  - / +xx 向后搜索 n下一个 N上一个
  - ？+xx 向前搜索 n上一个 N下一个

- 替换

  -   :s/被替换/替换后

  - 只会替换第一个

  - 再加上/g可以替换一行
  - 加/gc 会逐个询问是否需要替换
    - y替换
    - n不替换
    - a替换所有
    - q放弃替换
  - 前面再加上%可以对整个文件替换
  - 前面加m,n会替换m,n范围内的

- 其他操作
  - ctrl+g查看文件信息
  - 行号+G 跳转(或者用:+行号)
  - %定位括号
  - 打开文件时 vim -o 垂直并排打开多个文件
    - -O  水平打开
    - ctrl w w 光标切换至下一文件
    - ctrl w 方向键切换文件
    - 在退出命令后加上a时可以全部退出


### 插入模式

- 进入

  | i    |        在光标前面进入        |
  | ---- | :--------------------------: |
  | I    |    在光标所在行的行首进入    |
  | a    |        在光标后面进入        |
  | A    |    在光标所在行的行尾进入    |
  | o    | 在所在行的下方插入空行并进入 |
  | O    | 在所在行的上方插入空行并进入 |
  | s    |   删除光标指定的字符并进入   |
  | S    |    删除光标所在的行并进入    |


### 控制模式

- `:q` 退出（关闭窗口）
  - `:qa`全部退出
  - `:sp`打开多个窗口（同一文件）
- `:w` 保存（写）
- `:wq` 保存然后退出
- `:e {文件名}` 打开要编辑的文件
- `:ls` 显示打开的缓存
- :help {标题}打开帮助文档
  - `:help :w` 打开 `:w` 命令的帮助文档
  - `:help w` 打开 `w` 移动的帮助文档

### 宏

- `q{字符}` 来开始在寄存器`{字符}`中录制宏
- `q`停止录制
- `@{字符}` 重放宏
- `q{字符}q`清除宏
- 宏的执行遇错误会停止
- `{计数}@{字符}`执行一个宏{计数}次
- 宏可以递归
  - 首先用`q{字符}q`清除宏
  - 录制该宏，用 `@{字符}` 来递归调用该宏 （在录制完成之前不会有任何操作）

## 常用插件及配置