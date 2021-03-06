# 文本编辑器

## vi编辑器
**vi** 是Linux上的文本编辑器，你可以使用鼠标和键盘完成大多数的文本工作。

> **vim** 的全名是 _**Vi IMproved**_. 他们是一样的东西，比较类似。

### 进入VI文本编辑器
你可以像下面的方式一样进入vi：

`$vi filename`

如果文件不存在，vi将会创建一个文件。

```bash
$vi testfile
|
~
~
~
~
~
~
~
"testfile" [New File]
```

### Vi的模式
vi有两个模式

* 命令模式<font size=2 color=#90EE90>（command mode）</font>
* 输入模式<font size=2 color=#90EE90>（insert mode）</font>

在命令模式下，键盘上的字母会执行一些编辑程序（像移动光标，删除文本等等），要选择输入模式，请输入`<i>`。

在输入模式下，你输入的字母组合成单词和句子，不像许多文字处理软件，vi启动时就在命令模式，如果你在输入模式想要返回命令模式，就输入`<Esc>`。

### vi退出方式
你可以在命令模式下退出vi，首先，保证你的vi在命令模式下，然后你可以使用`:q`推出vi，如果你遇到了问题，那么`:q!`会帮助你强制退出，并且不会保存任何你输入的文本，输入`:wq`会保存后退出文本。

### 这里有一系列vi的命令

| 指令  |英文           | 描述   |
| :---  |:---          | :---     |
| :w    | Write        | 写入文件  |
| :q    | Quit         | 退出vi    |
| :wq   | Write & Quit | 保存并退出 |
| ZZ    |              | 等效于 `:wq`，你需要小心`Z`是大写字母。 |

## NANO
Nano是另一个Linux上的文本编辑器，它没有在任何Linux发行版上预安装，但它使用起来非常方便。

和vi一样，你可以使用`nano filename`去创建一个文件或者编辑它，当你在nano中输入文字，你将发现一些和vi的不同处，在屏幕底部，你可以看见一条，`^`意味着你需要使用`Ctrl` + `<key>`，举个例子，你可以使用`Ctrl` + `X`推出nano，如果你想要一些nano上面的信息，你可以使用`Ctrl` + `G`获取帮助。