 # sublime Text 3 个人配置


 * ## 绿化  

    在软件第一次启动前于sublime_text Text根目录下新建Data文件夹即可，如果不是第一次启动，则需到 %appdata% 文件夹下删除sublime text对应目录 （windows环境）

    以下是sublime text 在各个操作系统下配置文件夹路径
    OS X: ~/Library/Application Support/Sublime Text 2/Packages/
    Windows: %APPDATA%/Roaming/Sublime Text 2/Packages/
    Linux: ~/.config/sublime-text-2/Packages/


 * ## 安装Package Control （必须装）

    快捷键 ``` Ctrl+` ```  调出命令控制台  
    输入命令
    ```
    import urllib.request,os,hashlib; h = '2deb499853c4371624f5a07e27c334aa' + 'bf8c4e67d14fb0525ba4f89698a6d7e1'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
    ```
    此命令为sublime text3的安装命令，其他版本的安装命令可查看官网 [Package Control官网](https://packagecontrol.io/installation)  
    重启后Package Control安装完毕

 * ## 插件安装

    - ### 用Package Control安装插件的方法：

    按下`Ctrl+Shift+P`调出命令面板  
    输入 `Package Control install` 调出 Install Package 选项并回车，然后在列表中选中要安装的插件。

    - ### 主题列表  
      * thmee-soda  
      * theme-spacegray

    - ### 插件列表

    * ##### snippets  
      使用说明： sublime Text3 自带，可根据自己的需要进行添加对应开发语言的snippets，加快编码速度  

    * ##### insert callback
      使用说明
    ```
    About
    Inserts a node-style JavaScript callback function, and ensures that the call's trailing semicolon is inserted.

    Example
    Type a function call. When you type (, Sublime will autofill the closing ), and your cursor will be between the parens.

    someAsyncFn()
    Press Alt+C. If the function call's trailing semicolon is missing, it will be filled in. A callback function snippet will then be inserted.

    someAsyncFn(function(err, d) {

    });
    d will be selected for changing. Tab takes you to the function body.

    You can also select existing code and press Alt+C; the selected text will be inserted inside the new function body.
    ```

    * ##### advanceNewfile  [项目地址](https://github.com/skuroda/Sublime-AdvancedNewFile)
    使用说明:快速创建文件，快捷键 Ctrl+Alt+N ,支持输入路径，并会自动新建文件夹  

    * ##### httprequest [项目地址](https://github.com/braindamageinc/SublimeHttpRequester)
    使用说明：
    快速测试网站后端程序，[演示地址](http://www.imooc.com/video/5469)

    * ##### nettus fetch
    --使用说明：

    用以能够非常方便的管理一些开源框架
    按下Ctrl+Shift+P调出命令面板输入fetch:manage修改配置文件,添加平常开发需要的类库或包地址
    使用:新建一个文件，在命令面板输入fetch:file后选择需要添加的类库或包，回车后插件自动下载文件并将内容添加到
    新建的文件内

    * ##### sidebarenhancements （只支持sublime text3）
    --使用说明

    sublime Text3 默认siderbar（侧边栏）增强插件

    * ##### docblockr
    --使用说明
    快速添加注释，[演示视频](http://www.imooc.com/video/5472/0)   
    eg: 在函数上面输入/** ,然后按tab 就会自动生成注释。

    * ##### SublimeLinter
    --使用说明  
      使用linter进行语法及风格校验，这是一个基础包，需要根据开发进行进一步配置  
    eg：开发php时可安装 sublimelinter-php 插件  
     接下来，打开preferences-package>>settings-sublimeLinter-settings--user  
    配置文件：
    ```
    {
        "user": {
            "linters": {
                "php": {
                    "@disable": false,
                    "args": [],
                    "excludes": []
                }
            },
            "paths": {
                "linux": [],
                "osx": [],
                "windows": [
                    "D:\\Program Files (x86)\\wamp\bin\\php\\php5.3.3"   // 指定本地php目录。
                ]
            }
        }
    }
    ```
    有错误的地方在行号上会有红点提示在代码上会有红色方框，鼠标放红色方框上，错误信息在编辑器底部状态栏显示。

    * ##### Emmet(原名zencoding)
    --使用说明  

    快速写html代码，具体请参考：http://docs.emmet.io/abbreviations/syntax/

    * ##### Alignment   
    --使用说明

    代码对齐，如写几个变量，选中后，Ctrl+Alt+A，对代码有洁癖的人会喜欢的

    * ##### Bracket Highlighter
    --使用说明

    高亮代码匹配，可以匹配括号，引号，标签等各种

    * ##### JS Format
    --使用说明

    一个JS代码格式化插件，ctrl+alt+f格式化代码，让代码分分钟变漂亮

    * ##### Gist
    --使用说明

    超级方便的代码管理，首先你需要有github的用户名和密码，另外，你的终端要能运行curl
    安装Gist，然后Preferences->Browser Packages中找到Gist中的Gist.sublime-settings文件，输入github的用户名密码，根据文件注释中的地址生成GitHub API token，这就可以用了。

    * ##### liveReload+divvy，soda主题+phix配色方案（可选）
    ST2如果实现实时预览很头疼。我找到了一个很完美的玩法。
    1、ST2中安装liveReload。安装后找到这个包的配置文件，可以进行一些配置。
    2、浏览器中安装liveReload的扩展，现代浏览器都有对应版本。扩展安装成功后，用的时候点击一下就可以了。
    3、安装divvy(windows/mac都有版本，也都有破解方法)
    东西非常好用，你可以去官方FQ看下那个几分钟的小片子，几分钟可能改变一生喔 ；-)
    4、这样，在ST2中写完后，用sidebarEnhance一键呼出浏览器（我配置成F12），然后用divvy调整两个窗口的位置大小，就可以慢用liveReload带给我们实时修改实时预览的快感了。

    * ##### 格式化代码插件
    --使用说明

    使用TAG插件可格式化html代码  快捷键为 ctrl+alt+f

    也可以使用sublime text3 自带插件，快捷键设置代码为 {"keys": ["ctrl+shift+r"], "command": "reindent" , "args": {"single_line": false}} ，添加到Preferences → Key Bindings – User下
