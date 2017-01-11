# Win10系统右键添加Sublime Text 3的打开方式

1.打开注册表编辑器，开始->运行->regedit。

2.在HKEY_CLASSSES_ROOT→ * → Shell 下，在Shell下，新建项命名为Open With Sublime Text，在该新建项的右边窗口新建字符串值（右键--新建--字符串值）。名称：Icon；值：D:\Program Files\Sublime Text 3\sublime_text.exe,0 【注：使用您自己的安装文件目录】。

3.在新建的项Open With Sublime Text下面新建项Command（必须这个名称）。修改Command项右侧窗口的默认值，修改为："D:\Program Files\Sublime Text 3\sublime_text.exe" "%1"【注：使用您自己的安装文件目录】，双引号一定要加，否则无法打开路径带空格的文件，这样就大功告成了。
