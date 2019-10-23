### 此篇为sublime中插件的安装配置记录(update:2019年06月12日)
__2018年7月19日__	
　　感觉什么都很乱，但又懒得去整理，过了一段时间，也就看顺眼，感觉好像也不是那么乱。o(╯□╰)o  sublime又像是有那么一点调皮，干脆卸载重新装一次。  	
__tips__：sublime迁移到新环境，默认安装下将`%appdata%(C:\Users\Administrator\AppData\Roaming\Sublime Text 3)`整个替换到新环境中的文件夹,之后修改一些配置中的环境变量(未尝试)	
　　我觉得有些东西看原文的要好得多，很多网上的文章都是东拼西凑，甚至是断章取义的，看的人头皮发麻。＞﹏＜  
　　参考文章： [链接1][1] [链接2][2]	
　　官方网站下载页面：https://www.sublimetext.com/3		
　　官方插件网站：https://packagecontrol.io/	

#### 插件安装

* __Emmet__：代码快速编写。需要安装PyV8，默认是自动安装，如出现问题请[手动安装][3]，按照readme.md操作。
``` 
    工欲善其事，必先利其器之选一个主题。→_→。有时候很纠结，找一个东西，不得门路，
    七搞八搞的，把热情消磨了。殊不知，其实有时候够用就行，非要追求最新，最好或者其他，钻牛角尖也不好。
    我选择的是Material Theme 的默认主题，具体操作在官方插件网站中搜索该主题，并按照提示操作。
```
* __Bracket Highlighter__:高亮显示匹配的括号、标签等。
***  

__2018年8月4日__   第N天后的更新，放纵如山倒，自律如抽丝。  

*  __SideBarEnhancements__：增强侧边栏，增加边栏中右键菜单，可自定义快捷键，具体参照[readme][4]。
* __HTML-CSS-JS Prettify__: 整理代码格式。需要安装Node.js，在`Preferences->Package-setting->HTML-css-js Prettify->set node path`中设置好node.exe的路径。
* __SublimeLiter__: 代码检查工具需要下载<b>对应的linter</b>，设置每次保存时提示错误窗口`"show_panel_on_save"`。[详细设置参考][5]
    + __SublimeLinter-jshint__： 依赖 jshint，是否有jshint系统命令行中查找`where jshint`；没有的话使用`npm -g install jshint`进行全局安装。下同。
    + __sublimelinter-contrib-htmllint__： html语法检查，依赖htmlhint,这个好像用处不大
    + __SublimeLinter-php__： 此插件需要安装php，关于安装php环境，有phpstudy，WAMP，XAMPP,之后将路径加入到`paths`中,路径只需定位到`php.exe`目录中，，同下文
    + __SublimeLinter-csslint__：
    我想将node包局部安装在sulime的文件中，方便迁移，  
    尝试:
        - 在`\Users\Administrator\AppData\Roaming\Sublime Text 3`目录下安装node包  
        - 结果报错，例如'cannot locate jshint'，因为没有找到可执行文件。[常见错误解决][故障排查]  
        - 对照例子解决办法：在`SublimeLinter->setting`中，加入额外路径。 如果不是全局安装的话有两种使用局部node包的方法
            ```
                1. 在package.json 中使用script命令定义
                2.将node包的命令的路径引进，即node_modules下的.bin目录
            ```
            (这里有点疑问，那他原先全局安装的情况下，node包js引入的路径是在哪里配置的呢 ??[一个详细介绍npm的链接不知道有没有关系][6])
            ```
                // Provide extra paths to be searched when locating system executables.
                    "paths": {
                        "linux": [],
                        "osx": [],
                        "windows": ["C:\\Users\\**\\AppData\\Roaming\\Sublime Text 3\\node_modules\\.bin\\"]
                    }
            ```
*  __All Autocomplete__： 在当前所有打开的窗口中查找提示可能的名称，名词
* __AutoFileName__： 自动补全文件路径和文件名
* __sublimeCodeIntel__： 全功能的代码智能和智能自动完成引擎，依赖于__CodeIntel__，且在安装CodeIntel前需要安装Python、pip和php（WAMP自带）。然后设置解释器目录，[详细解释][7]
    ```
        //pip升级和安装包可能都需要管理员权限，在系统在以管理员方式运行命令行
        pip install pip -U 
        //更换pip镜像为国内清华镜像
        pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple 
    ```
    + 安装<b>codeIntel</b>可能报错提示` Microsoft Visual C++ 14.0 is required`,出错的原因大意上应该是缺少一个c++的环境来执行python，所以需要安装对应的环境，
    ```
        Downloaded Microsoft Visual C++ Build Tools from this link: https://visualstudio.microsoft.com/downloads/

        Run the installer

        Select: Workloads → Visual C++ build tools.

        Install options: select only the “Windows 10 SDK” (assuming the computer is Windows 10)
    ```
* __MarkdownPreview__：  markdown导出HTML格式文件预览。[帮助文档][9]https://facelessuser.github.io/MarkdownPreview/usage/#to-preview，越发觉得英语好的重要性，看文档不费劲，直接理解不需要再用中文意思理解一遍。
要想实时预览需要在sublime中安装<b>LiveReload</b>。
* __Markdown Editing__：  markdown编辑语法插件；安装此插件不要打开markdown格式文件；sublime 自带一个原生的markdown包，但跟此插件冲突，默认禁止掉原生的，当禁用掉原生的包时，此时恰好打开了md文件，就会提示错误,仅需要关闭后重新打开即可。[当未关闭markdown文件安装插件时的错误详细解释][8]
* __LiveReload__： 一个浏览器实时刷新插件配合MarkdownPreview 可在浏览器中实时刷新页面，[详细操作][10]
***  
#### 2019/05/19
* __LESS__： less文件语法高亮
* __sublime wxapp__： 微信小程序语法高亮，提示插件
* __ConvertToUTF8__： 文档支持中文格式
* __sublime merge__: 目前sublime 3.2.1 中支持了git的相关操作。只需要下载[Sublime Merge][11]就行，可以很方便的使用git的相关操作，之前没有的安装的话是使用gittortoise进行git操作的辅助
* __AdvancedNewFile__： 快速新建文件和文件夹
* __FileDiffs__: 比较两个文件的异同之处
* __Vue Syntax Highlight__: vue 语法高亮 在sublime 右下角选择选择语法的时候选择 vue component
* __Vuejs Snippets__： 使用时应注意与使用的vue版本保持一致，vue在更新，一些标签，属性也有了变化。

[故障排查]: http://www.sublimelinter.com/en/stable/troubleshooting.html
[详细介绍npm]: https://juejin.im/post/5ab3f77df265da2392364341中文
[1]: https://blog.csdn.net/mazegong/article/details/78859502链接2
[2]: https://www.shopify.com/partners/blog/sublime-text-plugins-2018
[3]: https://github.com/emmetio/pyv8-binaries
[4]: https://github.com/titoBouzout/SideBarEnhancements/blob/st3/readme.md
[5]: https://segmentfault.com/a/1190000004401704
[6]: https://juejin.im/post/5ab3f77df265da2392364341
[7]: https://github.com/SublimeCodeIntel/SublimeCodeIntel/blob/master/README.md
[8]: https://github.com/SublimeText-Markdown/MarkdownEditing#error-loading-syntax-file
[9]: https://facelessuser.github.io/MarkdownPreview/usage/#to-preview
[10]: https://facelessuser.github.io/MarkdownPreview/usage/#livereload
[11]: https://www.sublimemerge.com/
