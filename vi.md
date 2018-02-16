vi由比尔·乔伊（Bill Joy）撰写，所有UNIX like均默认安装此文本编辑器。

1. 首先复制一个文件到/tmp目录（本例中为复制根目录下install.log文件）做为示例文本。
	
	![](img/vi/fig1.png?raw=true)

2. 输入“cd /tmp”切换到/tmp目录，并输入“vi install.log”使用vi开始编辑。
	
	![](img/vi/fig2.png?raw=true)

#### 目录
1 [一般模式](#一般模式)

2	[编辑模式](#编辑模式)

3	[命令行模式](#命令行模式)

4	[替换内容](#替换内容)

## 一般模式

3. vi一般模式（Normal mode）界面如下：

	![](img/vi/fig3.png?raw=true)

4. 注意下图中光标位置。

	![](img/vi/fig4.png?raw=true)

5. 按左方向键(←)或者h(注意大小写)光标将向左移动一个字符。

	![](img/vi/fig5.png?raw=true)

6. 按右方向键（→）或者l(注意大小写)光标将向右移动一个字符。

	![](img/vi/fig6.png?raw=true)

7. 按上方向键（↑）或者k(注意大小写)光标将向上移动一个字符。

	![](img/vi/fig7.png?raw=true)

8. 按下方向键（↓）或者j(注意大小写)光标将向下移动一个字符。

	![](img/vi/fig8.png?raw=true)

9. 按“Page Down”按键或“ctrl+f”将向下移动一页。

	![](img/vi/fig9.png?raw=true)

10. 按“Page Up”按键或“ctrl+b”将向下移动一页。

	![](img/vi/fig10.png?raw=true)

11. 按0（数字）或功能键“Home”移动到光标所在行首个字符。

	![](img/vi/fig11.png?raw=true)

12. 按$或功能键“End”移动到光标所在行末尾字符。

	![](img/vi/fig12.png?raw=true)

13. 按G（注意大写）移动到文件最后一行。

	![](img/vi/fig13.png?raw=true)

14. 按gg（两个小写）移动到文件第一行。

	![](img/vi/fig14.png?raw=true)

15. 按“7回车键”向下移动7行（注意输入数字后需按回车键）。

	![](img/vi/fig15.png?raw=true)

16. 按yy（两个小写）复制光标所在行，按p（小写）复制到光标所在行下，按P（大写）复制到光标所在行上。

	![](img/vi/fig16.png?raw=true)

17. 按dd（两个小写）删除光标所在行。

	![](img/vi/fig17.png?raw=true)

18. 按u(小写)撤销上一步操作。

	![](img/vi/fig18.png?raw=true)

19. 输入5dd（数字+两个小写d）删除从光标所在行起下5行内容（包括光标所在行）。

	![](img/vi/fig19.png?raw=true)

20. 按“.（英文小数点）”重复上次操作（本例中为再删除5行）。

	![](img/vi/fig20.png?raw=true)

## 编辑模式

21. 移动光标到行中，按i（小写）即可进入插入模式（Insert mode），并从光标所在处开始插入。

	![](img/vi/fig21.png?raw=true)

22. 按“Esc”键退出编辑模式，移动光标到行中，按I（大写）即可进入插入模式（Insert mode），并从光标所在行第一个非空格字符处开始插入。

	![](img/vi/fig22.png?raw=true)

23. 按“Esc”键退出编辑模式，移动光标到“Installing”的第二个字符（n）下，按r（小写）即可进入替换模式（Replace mode）, 并会替换光标所在字符一次（本例中n被替换为i）。

	![](img/vi/fig23.png?raw=true)

24. 再次输入i，并没有替换后面字符，同时下面显示“--Insert--”，即为插入模式（Insert mode）。

	![](img/vi/fig24.png?raw=true)

25. 按“Esc”键退出编辑模式，移动光标到“Installing”的第二个字符（n）下，按R（大写）即可进入替换模式（Replace mode）,按i将一直替换，直到按Esc为止。同时下面显示“--Replace--”，即为替换模式（Replace mode）。

	![](img/vi/fig25.png?raw=true)

## 命令行模式

26. 输入“:set nu”即可显示行号。

	![](img/vi/fig26.png?raw=true)

27. 输入“:set nonu”即可取消显示行号。

	![](img/vi/fig27.png?raw=true)

28. 输入“/setup”即可查询斜杠后内容（本例中为setup）。

	![](img/vi/fig28.png?raw=true)

29. 输入n（小写）即可继续向下查找，输入N（大写）即可向上查找。

	![](img/vi/fig29.png?raw=true)

30. 如需不保存编辑并退出，可输入“:q!”并回车确定。

	![](img/vi/fig30.png?raw=true)

31. 如需保存修改并退出，可输入“:x”并回车确定，此命令仅当文件被修改时才写入，并更新文件修改时间，未修改则不更新文件修改时间。注意：不推荐使用“:wq”保存退出，因为“:wq”即使未修改文件也强制写入，并更新文件修改时间。

	![](img/vi/fig31.png?raw=true)

## 替换内容

32. 如何替换字符串，则将光标移动到欲替换行（本例中为方便说明故显示行号）。

	![](img/vi/fig32.png?raw=true)

33. 按ESC键确保为非编辑模式，输入“: s/i/x/”，即将“i”替换为“x”。

	![](img/vi/fig33.png?raw=true)

34. 按回车键确认并查看结果（本例中此行（12行）的第一个“i”被替换为“x”，即“Installing”被替换为“Installxng”）。

	![](img/vi/fig34.png?raw=true)

35. 如需将此行（12行）中所有“i”替换为“x”，则需添加参数。为方便对照，首先输入“u”撤销上一步替换。

	![](img/vi/fig35.png?raw=true)

36. 输入“: s/i/x/g”，注意比上面的命令多一个参数“g”。

	![](img/vi/fig36.png?raw=true)

37. 按回车键确定并查看结果（注意同上面的区别，本行所有的“i”已被替换为“x”）。

	![](img/vi/fig37.png?raw=true)


![](img/vi/fig38.png?raw=true)
![](img/vi/fig39.png?raw=true)
![](img/vi/fig40.png?raw=true)
![](img/vi/fig41.png?raw=true)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjk0Njc0MTY3XX0=
-->