EXAPUNKS文档汉化
====================================
STEAM上编程类游戏EXAPUNKS的文档翻译，商店链接：[EXAPUNKS](https://store.steampowered.com/app/716490/ "EXAPUNKS")  
该文档在游戏内以杂志`TRASH WORLD NEWS`的形式出现，pdf见游戏根目录下/Content/manual，作者提供了三种格式以供直接阅读或打印成小册子。

杂志分为上下册，内容按顺序分别为  
* 游戏世界观介绍
* 教程
* 代码文档
* 每关对应的背景故事和趣闻

目前已汉化完前三部分，后面的背景故事将会慢慢更新。  
本项目出于纯粹个人爱好，练练英语的同时熟悉一下markdown排版。   
一切更新随缘:kissing_closed_eyes:。
****
## 目录
* [上册](#上册)
	* [(02)TRASH WORLD MANIFESTO](#02TRASHWORLDMANIFESTO)
	* [(05)基于EXA的分布式网络程序](#05基于EXA的分布式网络程序)
	* <a href = "#title_6">(06)主机,链接,文件以及硬件寄存器</a>
		* [主机](#主机)
		* [链接](#链接)
		* [文件](#文件)
		* [硬件寄存器](#硬件寄存器)
	* [(08)GHAST教你写代码](#08GHAST教你写代码)
		* [教程1：基础](#教程1基础)
		* [教程2：文件读写](#教程2文件读写)
		* [教程3：EXA间通信](#教程3EXA间通信)
		* [教程4：条件与循环](#教程4条件与循环)
	* [(12)RUNTIME ERRORS](#12runtimeerrors)
	* [(14)EXA代码参考文档](#14EXA代码参考文档)
		* [寄存器](#寄存器)
		* [硬件寄存器](#硬件寄存器)
		* [指令](#指令)
	* [(18)"调试"噬菌体](#18调试噬菌体)
****
# 上册
## (02)TRASH&ensp;WORLD&ensp;MANIFESTO
&emsp;&emsp;欢迎阅读《TRASH WORLD NEWS》。你可能会好奇，为什么在这个数字时代我们还要发行一本纸质杂志呢？答案很简单：我们需要一块不受计算机干扰的净土，来分享有关于计算机系统和网络的重要敏感信息。  
&emsp;&emsp;你最近注意到了吗？无论何时何地，总有无数的计算机在幕后帮你做出决定。这些被当权者们设计并制造出来的电脑程序，正在背后估算着我们的价值，使我们可以为其所用，而这种行为似乎已经被大众接受并视作常态。  
&emsp;&emsp;电脑本身只是工具，应当为我们所用，这就是我们必须反抗的理由。我们要用知识和工具来武装自己，来反抗这股愈演愈烈的浪潮。下次再有计算机将我们视作棋子的时候，我们可以通过编写程序来破坏它们，让它们认识到人类才是这个世界的主宰。

**我们既是人类，也是黑客**

&emsp;&emsp;本杂志将会一步步地介绍体型微小但是功能强大的EXA，这项技术在无人察觉的情况下已经统治了世界。从游戏控制台到大公司的服务器，几乎任何东西都已经离不开它了。  
&emsp;&emsp;我们会带你了解事情的来龙去脉，并让你很快上手编程，即便你以前从没接触过代码。  
&emsp;&emsp;我们也会刊登来自全世界各个领域的黑客的研究成果，比如数据存储格式以及最新的网络研究进展等等。  
&emsp;&emsp;最后再提一句，本杂志刊登了某个生物学家最近关于“噬菌体”的研究报告，她在空闲时间里进行了该项研究并将成果分享给了我们。我敢保证这绝对是你在其他地方都找不到的绝密资料。
 
**黑客精神永存 Ghast留**


## (05)基于EXA的分布式网络程序
&emsp;&emsp;想要摆脱电脑的控制，第一步就是要学会如何去使用它们，这就需要学会用EXA编程。
### EXA是什么？  
&emsp;&emsp;EXA是可执行代理(EXecution Agent)的缩写。它可以在不打断自身工作的情况下在网络中自由穿梭，在现实世界中进行长距离移动。  
&emsp;&emsp;业内巨头Axion和TEC在几年前共同开发了EXA标准，初始版本被称作“分布式网络程序(distributed network programming)”。由于EXA可以在任何底层硬件上进行数据的传输和处理，因此EXA可以轻松地将世界上任何设备连接起来。现如今，EXA就是计算机网络的命脉。
### 代码，值和寄存器  
&emsp;&emsp;如果将EXA内部可视化，那么可以将其分成`代码区`和`寄存器区`两部分。当你使用EXODUS开发环境的时候，你可以在屏幕左侧看到你的每一个EXA实例。你可以对它们的内部代码进行编辑，并观察它们的寄存器值。  
&emsp;&emsp;**代码区**:在这里你可以用代码指示EXA进行一系列的行为，该代码语言是专门为控制EXA而设计的。我们会在之后的教程章节里详细地介绍该语言。  
&emsp;&emsp;**寄存器区**:你可以把这些寄存器看做是一个个存储值(value)的小格子。这些值可以是整型(numbers)，比如`38`或`5074`或`-203`，或字符串(keywords)，比如`SECRET`或`TRASH WORLD NEWS`或`ABC123`。你可以用代码来对寄存器内的值进行读写操作。  
&emsp;&emsp;寄存器的类型有多种。有些只能用于存储值，对这类寄存器进行读操作的时候，你可以获得上一次写入寄存器的值(X和T寄存器就属于这类)。其他寄存器可以看做是高级功能的接口，比如读写文件(F寄存器)，与其他EXA进行数据传输(M寄存器)。现在理解起来可能有些困难，没关系，教程里面会有详细说明。

(译者注：关于number和keywords的翻译，我觉得直接翻译成整型与字符串更舒服一些，因为在游戏里确实就是这样)


## <a name = "title_6">(06)主机,链接,文件以及硬件寄存器</a>
&emsp;&emsp;当你在网络中使用EXA的时候，下面这些信息你必须了解：
### 主机
&emsp;&emsp;一个主机(host)代表了网络中的一台电脑。EXA只能存在于主机之中。当你创建一个新的EXA实例时，它就会出现在你的主机中，你可以操控他们进入其他主机并执行特定行为。  
&emsp;&emsp;由于内存和系统性能的限制，每个主机所能容纳的EXA数量是有限的。在EXODUS开发环境中，这个容量就表现为主机所拥有的空余格子数量，每个EXA占一格。
### 链接
&emsp;&emsp;链接(link)将不同的主机连接了起来，EXA可以通过链接在主机之间进行移动。每个链接都有一个数字ID作为标识，以便你在代码中指向它们。大多数链接是双向的，不过某些特定的链接是单向的，少数链接甚至无法通行。
### 文件
&emsp;&emsp;文件(file)存储了值的序列，包括整型与字符串。文件类似于EXA，因为它们也存在于主机之中，也会占用格子，但它们不包含可执行代码，他们唯一的目的就是存储数据。  
&emsp;&emsp;想要操作文件，你需要使用EXA。EXA可以对文件进行创造、删除、读、写，并可以在不同主机之间移动文件。如同链接一样，每个文件都有一个数字ID，以方便你在代码中操作它们。
### 硬件寄存器
&emsp;&emsp;有些主机拥有特殊的硬件寄存器(hardware registers)。每个硬件寄存器代表了一个连接到当前主机的外部设备。不同的外设，硬件寄存器不同，它们的读写限制也不同。这些硬件寄存器也使用整型或字符串。它们的名字标识规则如下：一个井号后面跟着4个字母，比如`#POWR`或`#ENAB`。你可以在你的代码里直接使用这些标识。

&emsp;&emsp;以上信息有点多，所以如果你一时间无法消化也不用担心，在接下来的教程中，你可以开始用EXODUS开发环境来真正地编写一些代码了。


## (08)GHAST教你写代码
&emsp;&emsp;我相信每个人都可以轻松学会EXA编程，这就是为什么我写下了这些教程。即便你不是程序员，你也不用担心，试一下吧，很好学的。
### 教程1：基础
&emsp;&emsp;在这个教程中，你的目标是将ID为200的文件从名为"inbox"的主机中移动到名为"outbox"的主机中。你需要通过ID为800的链接来达到此目的。  
&emsp;&emsp;启动EXODUS开发环境并连接到网络，系统将会自动为你创建一个空白工程("工程"就是你当前用于完成任务的EXA的集合，当你按下run时就会执行它)  
&emsp;&emsp;现在，你会在屏幕左边看到一个拥有空白代码区的EXA。将下面五行代码敲进去。

	LINK 800  \\通过链接800进入网络
	GRAB 200  \\拿起文件200
	LINK 800  \\通过链接800进入"outbox"
	DROP      \\放下文件
	HALT      \\终止当前EXA
	
&emsp;&emsp;按下step按钮，以行为单位来调试你的代码。当你感觉差不多了以后，按下run按钮来执行全部代码。当你确认自己的代码没问题以后，按下forward来运行所有的case，直到结束。恭喜，你完成了你的首次EXA编程。
### 教程2：文件读写
&emsp;&emsp;第二个任务和第一个任务很像，但是除了移动文件，还需要你对文件进行读写。在继续阅读之前，先去EXODUS里看一下任务要求吧。  
&emsp;&emsp;如果需要使用EXA进行文件读写，我们需要用到F寄存器，同时需要用到X寄存器来存放中间值。将下面的代码输入你的EXA。

	LINK 800    \\通过链接800进入网络
	GRAB 200    \\拿起文件200
	COPY F X    \\从F中读取数据并写入X
	ADDI X F X  \\计算X+F并将结果写入X
	MULI X F X  \\计算X×F并将结果写入X
	SUBI X F X  \\计算X-F并将结果写入X
	COPY X F    \\从X中读取数据并写入F
	LINK 800    \\通过链接800进入"outbox"
	DROP        \\放下文件
	HALT        \\终止当前EXA

&emsp;&emsp;使用step来调试代码，当运行到GRAB的时候，注意观察在当前EXA窗口下面出现的代表文件200的窗口，同时注意该窗口中的文件指针，它高亮了文件的第一个值。当EXA尝试从F寄存器中读取值的时候，它就会读入当前高亮的值。同理，如果此时向F寄存器写入值，那么该值就会覆盖掉当前文件指针所指向的值。如果文件指针指向了文件末尾，那么此时写入操作会将新值添加到文件末尾。  
&emsp;&emsp;还有一点。当读操作或者写操作完成以后，文件指针将会自动后移一个位置。这个特性有时是很方便的，但有时却并不。
### 教程3：EXA间通信
&emsp;&emsp;在本教程中，有一个文件被放在只能进不能出的主机中，进去抓取文件的EXA将会被关在里面。因此，你需要创建两个EXA实例并进行EXA间的通信来完成该任务。这次，我希望你能独立完成代码编写，下面给你一些提示：
* 你可以使用MAKE来创建一个新文件。被创建的新文件默认为空，并且直接出现在创建它的EXA手里。
* 一个EXA实例可以使用WIPE来删除它手中的文件。
* EXA实例之间可以使用M寄存器来进行EXA间通信。一个EXA将值写入它的M寄存器，另一个EXA就可以将该值从它的M寄存器中读出，这样便完成了读者和写者之间的一次通信。
* 如果某个EXA实例尝试读取空的M寄存器，它将会被阻塞；反之，当某个EXA实例向M寄存器写入值以后，它将会被阻塞，直到另一个EXA实例将值从它那端的M寄存器中读出。因此，你不需要掐准时机去进行EXA间通信。
* 在EXODUS用户界面中，每个EXA实例都有一个开关，可以让你将该EXA的M寄存器设置为全局(global)或本地(local)。在全局模式下，两个EXA之间可以进行通信，无论他们在网络中的什么位置，只要他们之间的链接是通的(处于同一个强连通分量之中)。在本地模式下，两个EXA只有在同一个主机之中才可以通信。最后一点，如果两个EXA分别开了全局模式和本地模式，即便这两个EXA处于同一个主机中，它们也不能够通信。
### 教程4：条件与循环
&emsp;&emsp;你的最后一个任务，是创建一个文件并输入特定的内容。做到这点你需要使用LOOP指令，它可以让你循环执行代码，直到达到某特定条件并退出循环。给你一些建议：
* 你可以通过TEST指令来比较一个寄存器和另一个寄存器(或一个整型)是否相等，比如比较X是否等于38(TEST X = 38)，如果结果为True，那么**T寄存器**会被置1，否则，**T寄存器**会被置0。
* 单独使用TEST指令并没有什么用，但如果你结合条件跳转指令来使用(TJMP和FJMP)，你可以使程序跳转到其他位置。TJMP(jump if true)，当T的值为1时使程序跳转到指定位置；FJMP(jump if false)，当T的值为0时使程序跳转到指定位置。你可以使用MARK指令来标记跳转位置。
* 当指令TJMP和指令FJMP去检查T寄存器的值时，它们并不会关心此时T的值是TEST指令赋予的，还是你自己手动去修改的。实际上你可以向T寄存器存入任何值，只不过你要小心，不要让TEST指令把你的值给覆盖了。
  
&emsp;&emsp;下面给出一个循环的例子。假设你想向某个文件中写入9999，一共写10次，你可以用寄存器X来记录当前已写入次数。  

	COPY 0 X    \\将X寄存器的值置为0
	MARK LOOP   \\定义一个跳转标记，名为LOOP
	COPY 9999 F \\向手中的文件写入值9999
	ADDI X 1 X  \\X自增
	TEST X = 10 \\检查X的值是否等于10，并将结果写入T(0或1)
	FJMP LOOP   \\若T的值为0，则程序跳回LOOP处继续执行

&emsp;&emsp;好了，祝贺你，现在你已完成了所有教程。你现在是一个真正的EXA程序员了。需要学的东西还很多，但至少你已经入门了。


## (12)RUNTIME&ensp;ERRORS
&emsp;&emsp;当EXA尝试执行一些非法操作时，该EXA实例就会被主机自动终止，等同于运行了HALT指令。大部分非法操作都毫无用处，但还是有少数几个errors是可以被利用的。  
&emsp;&emsp;先让我们看看那些没用的errors：
* **除以0** 你不能执行除以0操作，基本的数学常识。别问，记住就行了。
* **对字符串进行运算** 你不能对字符串进行加减乘除，数学运算只能用于数字。
* **非法访问F寄存器** 如果一个手中没有文件的EXA尝试进行读写操作，则它会发生错误并终止。不要忘了先把文件拿起来。
* **非法访问硬件寄存器** 和上一条有点类似，当你准备对硬件进行读写时，确保你的EXA和硬件寄存器处于同一主机中。  

&emsp;&emsp;上述errors也许你已经在教程中遇到过了，现在让我们来看看一些更有意思的errors。  
&emsp;&emsp;主机的链接可以改变，里面文件也可以删除，所以有时你也许并不了解当前主机的全部信息。你当前操作环境的某些信息，只有通过故意执行某些会引起报错的代码才能够得到。这听起来好像挺危险的，不过不用担心，我们只要能达到目的即可，又不是在给大公司开发核心项目。  
&emsp;&emsp;下面就是你可以利用的errors：

* **非法文件访问** 当你想寻找某个特定文件时，如果发生了该错误，则说明该文件不存在。  
* **非法穿越链接** 当某个EXA希望通过不存在的链接时，该EXA会被终止，但至少你知道了该链接不存在。  

&emsp;&emsp;不要担心你的EXA会发生错误，虽然可能看上去它们很可爱，但它们存在的目的就是不停地交换、计算、生成并死亡，你要学会利用这一点。


## (14)EXA代码参考文档
&emsp;&emsp;EXA虚拟机(EXA-VM)允许用户在主机共享网络之中运行多个EXA实例。在该网络中，EXA可以动态地生成、销毁，也可以在主机之间移动。EXA虚拟机允许所有的EXA独立并同时运行，即便多个EXA处于同一台主机中。  
&emsp;&emsp;一道EXA程序由一系列指令构成。有的指令不需要操作数(operand)，而有的指令需要指定1个或多个操作数。在接下来的讲解中，将使用以下缩写来代替操作数：
* **`R`** 寄存器
* **`R/N`** 寄存器，或者一个介于-9999和9999之间的数
* **`L`** 使用MARK伪代码定义的标签
### 寄存器
* **`X`** X寄存器是一个标准存储寄存器，可用于存储整型与字符串。
* **`T`** T寄存器是一个标准存储寄存器，可用于存储整型与字符串。它同时也会存储TEST指令的测试结果，并作为条件跳转指令(TJMP AND FJMP)的执行条件。
* **`F`** F寄存器允许EXA对它手里的文件进行读写。当EXA拿起文件时，文件指针会自动指向该文件的第一个值。读取F寄存器便会拿到该值；写入F寄存器便会覆盖该值。对F寄存器的读写结束后，文件指针会自动后移一个单位。当指针指向文件末尾时，写入操作会将新值添加到文件末尾。
* **`M`** M寄存器提供了EXA间通信的功能。当某EXA将值写入M寄存器时，该值就会留在通信管道中，直到另一个EXA从它那端的M寄存器中将该值读出。该方法可以传输整型和字符串。  
&emsp;&emsp;当某个EXA实例向M寄存器写入值以后，它将会被阻塞，直到另一个EXA实例将值从它那端的M寄存器中读出。如果某个EXA实例尝试读取空的M寄存器，它将会被阻塞，直到有值可读。若多个EXA同时对M寄存器进行读取，则只有一个会成功，但结果是不可预测的。  
&emsp;&emsp;在默认情况下，EXA间通信可以横跨整个网络，若想将该通信范围限制在一个主机之中，可以点击全局/本地开关，或者直接执行`MODE`指令。处于全局模式的EXA是不能同处于本地模式的EXA通信的，即便它们在同一个主机内。
### 硬件寄存器
&emsp;&emsp;一些运行EXA虚拟机的主机，会使用硬件寄存器来提供访问外设的接口。硬件寄存器的合法命名规则为#号后面跟着4个字母，比如`#POWR`或`#ENAB`。根据主机配置的不同，它的硬件寄存器分为只读、只写或可读可写。
### 指令
#### 与值相关的操作
* **`COPY R/N R`** 将第一个操作数的值复制到第二个操作数中。
* **`ADDI R/N R/N R`** 将第一个操作数的值与第二个操作数的值相加并存入第三个操作数中。该语法同样适用于以下指令：`SUBI(减法)`，`MULI(乘法)`，`DIVI(除法)`，`MODI(取模)`。
* **`SWIZ R/N R/N R`** 暂略。
#### 跳转指令
* **`MARK L`** 用L来标记该行。`MARK`是伪代码，不会运行。
* **`JUMP L`** 跳转到指定的标记位置。
* **`TJMP L`** 如果T寄存器的值为1(或其他任何不为0的值)，则跳转到指定的标记位置。对应`TEST`结果为true的情况。
* **`FJMP L`** 如果T寄存器的值为0，则跳转到指定的标记位置。对应`TEST`结果为false的情况。
#### 测试值
* **`TEST R/N = R/N`** 对第一个操作数和第二个操作数进行比较。如果相等，将T寄存器的值置1，否则置0。该语法同样适用于`<`和`>`。注：对字符串比较的依据是字典序；整型与字符串的比较永远返回false。
#### 生命周期
* **`REPL L`** 创造当前EXA的一份拷贝，并跳转到新EXA的指定标记位置。如果某EXA运行`REPL`指令的时候手里有文件，则文件将会留在原EXA手中，并不会被复制。
* **`HALT`** 终止当前EXA。若该EXA手里有文件，则掉落(drop)。
* **`KILL`** 终止当前EXA所在的主机内的另一个EXA，优先终止当前用户所创建的EXA。如果有多个目标，则结果不可预测。
#### 移动
* **`LINK R/N`** 穿过指定链接。
* **`HOST R`** 将当前主机的名字复制到指定寄存器中。
#### 交流
* **`MODE`** 调整M寄存器的模式。
* **`VOID M`** 清空M寄存器。
* **`TEST MRD`** 如果当前M寄存器中有值可读，则置T寄存器的值为1，否则为0。
#### 文件操作
* **`MAKE`** 创建新文件。
* **`GRAB R/N`** 拿起指定文件。
* **`FILE R`** 将手中文件的ID复制到指定寄存器。
* **`SEEK R/N`** 根据值来移动手中文件的文件指针，正数则向文件末尾移动，负数则向文件头部移动。`SEEK`操作并不会使得文件指针越界，因此你可以将操作数设置为-9999或9999来使文件指针直接移动到末尾或头部。
* **`VOID F`** 将当前高亮的值从文件中删除。
* **`DROP`** 放下当前文件。
* **`WIPE`** 删除当前文件。
* **`TEST EOF`** 检查当前文件指针是否已经到达文件末尾。若是，则置T寄存器的值为1，反之为0。
#### 杂项
* **`NOTE`** 跟在NOTE后面的任何文本在编译代码的过程中会被丢弃，因此你可以在后面写注释。
* **`NOOP`** 空过一个循环。
* **`RAND R/N R/N R`** 在[R/N_1，R/N_2]的范围内随机创建一个数并存储到第三个操作数中。


## (18)"调试"噬菌体
&emsp;&emsp;近些天，一种被称作“噬菌体”的神秘疾病正在悄然爆发。该病毒会将人体慢慢地转变成计算机部件。虽然这听起来像是科幻小说里才会发生的故事，但可惜，这都是真的。“噬菌体”在医学界的学名是“进行性神经胶质功能障碍”(该叫法已过时，且完全不准确)，或被称作Wurzner综合征。  
&emsp;&emsp;乍一看，将身体转变为计算机好像挺酷的，像终结者一样。不幸的是，噬菌体并不会将你的身体变成你想象中的那种可运行的计算机。如果不经控制，噬菌体只会将人体转变成一个无生命且毫无意义的电路集合。  
&emsp;&emsp;我们已经确认，该疾病最容易发生在经常使用电脑的人群之中，目前感染该疾病的全部都是每天使用电脑时长超过8小时的人。该病毒会从人的四肢开始蔓延(通常是手，有时是脚)，在6到18个月内就会遍布全身，慢慢地将人体细胞转变成含有半导体亚结构的类塑料实体。  
&emsp;&emsp;目前，治疗该疾病的最好方式，就是尽快将已感染的组织切除，不过这明显不是一个理想的解决方案。其他的治疗方法正在研究当中，其中一种口服药剂似乎可以有效地减缓病毒扩散的速度，不过昂贵的价格导致该方案的普及无望。  
&emsp;&emsp;除此之外，目前我们对噬菌体的了解还是过于缺乏，因此坊间流传出了许多猜测。其中一种猜测称，噬菌体是从某秘密政府实验室泄露出来的用于研究人机交互(真·人机交互)的试验品。更有传闻说这是某邪教组织想将碳基生命和硅基生命融合起来以创造出更高级的生命意识体。  
&emsp;&emsp;根据经验，有一件事是我们目前可以确定的：噬菌体被设计出来的原始目的，确实是为了促进人机交互的发展。作为从某知名医科大学毕业的学生，我可以在实验室做一些“非学术”的医学实验，实验对象是我的一位感染噬菌体的朋友，在该实验中我们两人将匿名。
### 把噬菌体节点看作EXA主机接口
&emsp;&emsp;关于被噬菌体所感染的人体组织，有一点非常有趣，就是它确实可以提供一个接口，用市面上现成的硬件调试器就可以与其进行连接。在该实验中，我使用的是Mitsuzen HDI-10，它一般用作调试基于EXA的嵌入式系统。  
&emsp;&emsp;我用可导电的高精度镊子替换了HDI-10原装的探测器，使我可以连接到下面显微图像所示的噬菌体节点簇之中。每个噬菌体节点都可看做一个小主机，主机之间有链接互通，HDI-10的固件可以自动识别并枚举出合适的链接ID。  
&emsp;&emsp;众所周知，噬菌体节点对神经(或类神经)细胞具有亲和力，可以破坏神经行为并且引起退行性症状。那些与神经细胞相连的噬菌体节点(也就是主机)，可以在内部提供能够测量神经电位的硬件寄存器，并判断该神经是处于兴奋态还是抑制态，这进一步证明了“噬菌体的设计初衷是研究人机交互”这一猜测。神经电位的单位貌似是毫伏，正常情况下神经电位处于-70mV左右，在兴奋态下会升至50mV左右，在抑制态下降至-120mV左右。  
### 将EXA注入噬菌体节点？
&emsp;&emsp;根据这些初期工作所得到的结果来看，我感觉可以将EXA注入人体内的噬菌体节点，并通过编程来修复那些由于噬菌体的扩散而遭到破坏的神经程序。我本想亲自进行该实验的，可这种事情若是传到我的医学界同僚那里就麻烦了(这肯定要保密的)，而且这种一次性的定制疗法肯定是得不到监管部门批准的，所以我打算有机会再做进一步的尝试。
