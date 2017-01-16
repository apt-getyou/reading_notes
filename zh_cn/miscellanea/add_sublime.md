# Win10系统右键添加Sublime Text 3的打开方式

1. 打开注册表编辑器，开始->运行->`regedit`。

2. 在`HKEY_CLASSSES_ROOT→ * → Shell` 下，在Shell下，新建项命名为`Open With Sublime Text`，在该新建项的右边窗口新建字符串值（右键--新建--字符串值）。名称：Icon；值：`D:\Program Files\Sublime Text 3\sublime_text.exe,0` 【注：使用您自己的安装文件目录】。

3. 在新建的项`Open With Sublime Text`下面新建项Command（必须这个名称）。修改Command项右侧窗口的默认值，修改为：`"D:\Program Files\Sublime Text 3\sublime_text.exe" "%1"`【注：使用您自己的安装文件目录】，双引号一定要加，否则无法打开路径带空格的文件，这样就大功告成了。


# Win10系统右键添加Atom的打开方式
1. 打开注册表编辑器，开始->运行->`regedit`。

2. 在`HKEY_CLASSSES_ROOT→ * → Shell` 下，在Shell下，新建项命名为`Open With Atom`，在该新建项的右边窗口新建字符串值（右键--新建--字符串值）。名称：Icon；值：`"C:\Users\banhu\AppData\Local\atom\app-1.12.9\atom.exe"` 【注：使用您自己的安装文件目录】。

3. 在新建的项`Open With Atom`面新建项`Command`（必须这个名称）。修改`Command`项右侧窗口的默认值，修改为：`"C:\Users\banhu\AppData\Local\atom\app-1.12.9\atom.exe" "%1"` 【注：使用您自己的安装文件目录】，双引号一定要加，否则无法打开路径带空格的文件，这样就大功告成了。



添加右键方法应该大致相同
