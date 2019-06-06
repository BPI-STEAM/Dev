了解拓展积木模板
==================================================================

认识 Blockly 积木设计器
---------------------------------

前面我们已经介绍了什么是 Blockly ，现在就来说说，怎么开发它们。

- 谷歌源 `GOOGLE Blockly Developer Tools <https://blockly-demo.appspot.com/static/demos/blockfactory/index.html>`_

- 国内源 `Blockly Developer Tools <http://walkline.wang/blockly/blockfactory/>`_

- 可选 `备用源 <https://blockly.yelvlab.cn/google/blockly/demos/blockfactory/index.html?tdsourcetag=s_pctim_aiomsg>`_

.. image:: images/blockly_developer.png

设计器使用方法参见以下两篇介绍文档，两篇参考资料可选。

- `Blockly 创建自定义块-概述 <https://itbilu.com/other/relate/H1huYbEWQ.html>`_
- `Blockly 创建自定义块-Blockly 开发者工具 <https://itbilu.com/other/relate/r1IhFZV-X.html>`_

可选参考资料。

- `Blockly - 来自Google的可视化编程工具 <https://itbilu.com/other/relate/4JL8NjUP7.html>`_
- `Blockly 的配置 <https://itbilu.com/other/relate/Ek5ePdjdX.html>`_

拓展积木的基本构成
---------------------------------

假设学会使用上述设计器，那就从一个通用的模板开始吧。

请看这个 `webduino-blockly-template <https://bpi.org.cn/webduino-blockly-template/blockly.json>`_ 示例项目。

认识模板目录文件，如下一系列表格，稍后会详细介绍。

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
webduino-blockly-template
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

====================  ===================================================
 文件路径                             介绍与用途
====================  ===================================================
blockly                 积木资源文件夹，内容下述
demes                   积木示例、设计文件夹，内容下述
blockly.json            积木类型、依赖、实现的定义
itpk-blockly.js         积木的代码生成函数实现
itpk.html               测试原始积木功能 API 页面
itpk.js                 经典 JavaScript 接口实现
README.md               积木的使用说明文档
_config.yml             由 Github Page 创建，并提供外链。
====================  ===================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
webduino-blockly-template\\blockly
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

====================  ===================================================
 文件路径                             介绍与用途
====================  ===================================================
msg                    积木多语言资源文件夹，内容下述
blocks.js              由 积木设计器 自动生成的样式实现
javascript.js          由 积木设计器 自动生成的积木代码生成函数实现
toolbox.xml            由你提供左侧工具列积木样式设计
====================  ===================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
webduino-blockly-template\\blockly\\msg
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

====================  ===================================================
 文件路径                             介绍与用途
====================  ===================================================
blocks                  积木内部的相关的语言文件，内容下述
en.js                   定义工具列的 英文 文字变量
zh-hans.js              定义工具列的 简体中文 文字变量
zh-hant.js              定义工具列的 繁体中文 文字变量
====================  ===================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
webduino-blockly-template\\blockly\\msg\\blocks
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

====================  ===================================================
 文件路径                             介绍与用途
====================  ===================================================
en.js                  定义积木内部的 英文 文字变量
zh-hans.js             定义积木内部的 简体中文 文字变量
zh-hant.js             定义积木内部的 繁体中文 文字变量
====================  ===================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
webduino-blockly-template\\demos
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

====================  ===================================================
 文件路径                             介绍与用途
====================  ===================================================
blockly.xml             积木的使用范例，可导入 webduino blockly 
library.xml             积木的设计库，可导回设计器中重新设计
====================  ===================================================

这些基本的定义是便于修改模板积木过程中查阅其确切定义。

拓展积木的外链说明
---------------------------------

根据 `拓展积木的使用说明 <http://doc.bpi.org.cn/zh_CN/latest/bpi-web/modules/basic.html>`_ 可知插件地址外链类似这样：`https://bpi.org.cn/webduino-blockly-template/blockly.json` 的地址，又或者是这样 `https://junhuanchen.github.io/webduino-module-itpk-robot/blockly.json` ，请确保在访问的时候，使用 https 访问且内容类似下图的 JSON 效果。

.. image:: images/blockly_json.png

拓展积木的托管说明
---------------------------------

如果发现 fork 该模板项目后无法直接外链使用，请设置 Github Pages 的 Source，如下描述，这是因为它需要转换为该链接，以个人的 Github 为例，如下图是没有设置的情况。

.. image:: images/pages_source.png

选择了 Source 的 master branch 分支。

.. image:: images/pages_select.png

此时将会产生 Github 的外链，这就是在 Github 上提供积木的地址，积木地址务必提供 https 访问，防止被跳转回 http 。

.. image:: images/pages_result.png

使用这个刚生成的地址 `https://junhuanchen.github.io/webduino-blockly-template/blockly.json` ，在积木载入中确认一遍。

.. image:: images/pages_commit.png

注意 fork 的 readme 的内容并没有改变，所以发布的时候，别忘了修改积木地址。
