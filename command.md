# Linux Shell 命令

## 使用一些有用的命令
几乎所有的 Shell 命令都有形如 "$ [命令] [操作] [文件名]" 的格式，如

`` ～$ ls -l /etc ``

下面展示的是一些常用的命令：

**ls**: **英文**为 *'List'*，**作用**是列出某个目录下面的文件

    -l: 使用长列表格式，可以列出更多更详细的信息
    -a: 列出所有文件，包括隐藏的文件
<font size=2> *所以你可以使用 <font color=#DEB887>ls -al</font> 来显示某一个目录下所有文件的详细信息*</font>

| 命令   | 英文              | 描述 |
| :---  | :---              | :---      |
| cd    | change directory  | 改变当前 *shell* 的工作目录 |
| mkdir | make directory    | 新建一个目录文件 |
| pushd | push directories  | 选择一个目录文件切换为当前**工作目录**，并将先前的目录压入目录栈。如果操作后缺少参数，则自动**切换** <font size=2 color=#90EE90>*(rotates)*</font> 目录栈顶端的两个目录 |
| popd  | pop directories   | 推出目录栈中顶端的目录作为工作目录，原来栈中的该目录将删除 |
| cat   | concatenate       | 连接一个文件，并将其标打印至**标准输出** <font size=2 color=#90EE90>*(stdout)*</font> |
| mv    | move              | 移动一个文件 |
| rm    | remove            | 删除一个文件 |
| ls    | list              | 列出某个目录下面的文件 |


## 如何登录远程的Linux？<font size=2 color=#90EE90>*(SSH远程登录)*</font>

这个部分，我们将介绍一些基础的SSH命令，并且展示如何使用SSH登录到远程*Linux*电脑。

### SSH简介
> SSH命令提供了一种在不稳定网络上两台主机安全的连接方式，这样的方式同样适用于终端登录，文件传输以及在一些应用程序之间建立信息的传输隧道。

对我们而言，SSH只是一个登录*Linux*的工具，使我们可以使用*windows*登录*Linux*。

### 如何使用SSH登录Linux?

首先，运行下面的命令以确保SSH服务器已经被安装在Linux中 *('$'不用打)* 。

`$sudo apt-get install openssh-server`

如果我们想要通过 _**ssh**_登录一个服务器，我们就需要知道一个**用户账户**，一个**用户密码**以及一个服务器的**IP地址**或**域名**。

`$ssh [username]@hostname [command]`

如果没有设置用户名，那么默认用户名就是你私人Linux电脑的账户名。

如果这是你第一次使用 _ssh_ 去连接远程机器，你将会看见下面的信息。

```bash
The authenticity of host '[SERVER NAME]' cannot be established.DSA key fingerprint is 04:48:84:31:b0:z0:5a:9b:01:9d:b3:a7:47:e2:b1:0c.Are you sure you want to continue connecting (yes/no)?
```
输入 ``yes`` 继续，这将让这个服务器加入你已知的主机列表中 _(被储存在`~/.ssh/known_hosts`中)_ 。如下面所呈现的信息<font color=#A00E0E><缺少呈现信息></font>所示，我们将不能再次输入`yes`在我们下次登录Linux的时候。

至于为什么我们得到的信息和最开始的会不一样，你可以从[这篇博客](https://www.ssh.com/attack/man-in-the-middle)中找到精简的回答，这是因为中间人攻击。

在你第一次得到了密钥时，使用如下命令进入`~/.ssh/`文件夹：

`$mv /path/to/key ~/.ssh`

然后使用下面的命令改变这个密钥的权限至600,_至于更多关于权限控制的知识，可以参看这篇[博客](https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-permissions)_：

`$chmod 600 ~/.ssh/key`

当我们将先前做的一切都安排妥当了，我们就可以使用这个钥匙登录我们的服务器了：

`$ssh -i ~/.ssh/key [USERNAME]@[SERVER ADRESS]`

事实上，我们通常并不使用这样的方式登录Linux，需要用密钥登录的电脑是为了确保电脑的安全。

除了SSH中最基础的知识外， _scp_ 的用法：一种基于SSH上的文件传输工具，它对我们一样的重要。下一个章节将谈一谈这个命令。

### 使用SSH在其他Linux上显示出GUI

`$ssh -X [USERNAME]@[SERVER ADDRESS]`

然后你就可以在终端上运行类似于`gedit`这样有用户交互界面的程序了。用户界面会呈现在你的屏幕上。

### 使用SSH在Windows上登录Linux

> 也许你并不知道如何将SSH安装至最新的Windows 10系统，你可以在 `powershell` 或者 `cmd`中使用它,并且如果你使用其他Windows系统，你可以安装[Xshell](https://www.netsarang.com/products/xsh_overview.html)，或者其他SSH客户端在你的系统上。

当你想要在你自己的电脑上登录时，终端仿真器<font size=2 color=#90EE90>(Terminal Emulator)</font>可以帮助你，接下来，我们将使用 _**Xshell**_作为一个例子。

#### 如何使用Xshell

Xshell的操作和Linux系统上的Shell几乎是一样的，唯一的不同是Xshell将新推出一个窗口，那个窗口将需要输入账户密码。

如果你希望你的Xshell能记住你的用户名，或者不想要输入密码去登录你的Linux，只需要在Xshell中跟着下面的步骤：

**步骤 1** 

点击按钮新建一个配置文件。

**步骤 2**

设置配置以对应上你的Linux。

如果你不知道你电脑的IP，请使用`ifconfig`命令在你的Linux上显示出IP地址。

**步骤 3**

如果你有一个私钥去登录你的Linux，只需要变更模式即可。

**步骤 4**

点击 OK 按钮去保存你的配置文件，然后继续。

Xshell将会再次检查你的密码，然后将反馈一些信息。

然后，你将可以使用SSH登录你的Linux了。

### 使用SSH在Windows上显示GUI

你可以使用Xmanager在你的Windows上显示GUI。下载[Xmanager](https://www.netsarang.com/products/xmg_overview.html)

**拓展**

如果你想要，你还可以在你的Windows10上安装**WSL**<font size=2 color=#90EE90>(Linux Windows子系统，Windows Subsystem for Linux)</font>，WSL将提供一个在Windows上的Linux虚拟环境。

这里是一片关于它的[官方文档](https://docs.microsoft.com/en-us/windows/wsl/install-win10)。

## 如何使用Linux命令翻译文件

### SCP简介

_**scp**_ 是一个在服务器和本地电脑之间通过SSH协议传输文件的工具，它是一个Linux上非常有用的工具，当然，对于Windows用户来说，你可以使用 [Xshell](https://www.netsarang.com/products/xsh_overview.html) 或者 [Xftp](https://www.netsarang.com/products/xfp_overview.html) 来替代。
