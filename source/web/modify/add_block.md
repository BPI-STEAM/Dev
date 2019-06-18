
## 添加新的积木

先前我们制作了一个积木块，我们需要将它添加到我们自己的积木里，先看一下我们想要添加的积木的效果。

![](images/blockly_itpk_ask_ip.png)

进入 Block Exporter 可以批量选取积木并导出对应代码。

![](images/blockly_exporter.png)

获取这两段定义内容，然后将它添加到创建的模板积木中，注意结合前一章的目录下的文件描述。

进入 blockly/blocks.js ，在后面添加 Block Definitions 的代码。

```javascript
Blockly.Blocks['itpk_ask_ip'] = {
  init: function() {
    this.appendDummyInput()
        .appendField("问 茉莉 查本机网络 IP ");
    this.appendStatementInput("callback")
        .setCheck(null);
    this.setPreviousStatement(true, null);
    this.setNextStatement(true, null);
    this.setColour(160);
 this.setTooltip("");
 this.setHelpUrl("");
  }
};
```

进入 blockly/javascript.js 也同样添加 Generator Stubs 的代码。

```javascript
Blockly.JavaScript['itpk_ask_ip'] = function(block) {
  var statements_callback = Blockly.JavaScript.statementToCode(block, 'callback');
  // TODO: Assemble JavaScript into code variable.
  var code = '...;\n';
  return code;
};
```

如果不清楚如何操作的可以看这个提交 [添加积木的定义](https://github.com/junhuanchen/webduino-blockly-template/commit/8f556c70a033d4e8186439dbf348d10aa29fece0) 。

![](images/add_blockly.png)

当你添加完了积木的定义，不代表积木可以使用，还需要在 blockly/toolbox.xml 中添加你积木的工具栏位置，否则将无法显示到左侧来，例如下图的效果。

![](images/blockly_left_tool.png)

那么我们应该如何做呢？先是进入 Workspace Factory 可以模拟设计的积木大致的使用方法，与其他积木进行对接的尝试，还可以导出（Export）积木工具列 toolbox.xml 文件供你参考。

![](images/blockly_factory.png)

然后拿我们设计的积木出来。

![](images/view_toolbox.png)

此时通过下图的方式得到 toolbox.xml 文件，然后添加到我们原本的 blockly/toolbox.xml 文件当中。

![](images/export_toolbox.png)

下载打开它得到 xml 文件代码。

![](images/open_toolbox.png)

```xml
<xml xmlns="http://www.w3.org/1999/xhtml" id="toolbox" style="display: none;">
  <block type="itpk_ask_ip">
    <statement name="callback">
      <block type="text_print">
        <value name="TEXT">
          <block type="itpk_answer"></block>
        </value>
      </block>
    </statement>
  </block>
</xml>
```

实际上就可以看出积木的对应效果，例如 `<block>` 标签对应的就是积木块， `<statement>` 标签对应的就是结合的积木块，所以我们可以在工具栏看到如下效果。

![](images/toolbox_result.png)

现在将其添加到我们的原本的模板积木当中，与其他存在的积木块作出对比。

以下是原内容：

```xml
<category id="catItpk">
  <block type="itpk_ask">
    <value name="question">
      <block type="text">
        <field name="TEXT">今天东莞天气如何？</field>
      </block>
    </value>
  </block>
  <block type="console">
    <value name="console">
      <block type="itpk_answer"></block>
    </value>
  </block>
  <block type="itpk_clear">
  </block>
  <block type="itpk_ask">
  <value name="question">
    <block type="text">
      <field name="TEXT">查 IP </field>
    </block>
  </value>
	<statement name="callback">
	<block type="console">
	<value name="console">
		<block type="itpk_answer"></block>
	</value>
	</block>
	</statement>
  </block>
</category>
```

在后面添加新内容，变成如下代码。

```xml
<category id="catItpk">
  <block type="itpk_ask">
    <value name="question">
      <block type="text">
        <field name="TEXT">今天东莞天气如何？</field>
      </block>
    </value>
  </block>
  <block type="console">
    <value name="console">
      <block type="itpk_answer"></block>
    </value>
  </block>
  <block type="itpk_clear">
  </block>
  <block type="itpk_ask">
  <value name="question">
    <block type="text">
      <field name="TEXT">查 IP </field>
    </block>
  </value>
	<statement name="callback">
	<block type="console">
	<value name="console">
		<block type="itpk_answer"></block>
	</value>
	</block>
	</statement>
  </block>
  <block type="itpk_ask_ip">
    <statement name="callback">
      <block type="console">
        <value name="console">
          <block type="itpk_answer"></block>
        </value>
      </block>
    </statement>
  </block>
</category>
```

现在，你已经将自己设计的积木添加进去了，此时你还需要最后一步，就可以载入积木看到效果。

在 blockly.json 中添加你的积木类型（types），因为它是一个全新的积木所以需要添加进去，否则不会被载入到动态积木中。

查看 blockly.json 的内容，然后在 types 列中添加 `"itpk_ask_ip",`

```json
{
  "types": [
    "itpk_ask_ip",
    "itpk_ask",
    "itpk_answer",
    "itpk_clear"
  ],
  "category": "itpk",
  "scripts": [
    "https://cdn.jsdelivr.net/gh/yarrem/stringFormat.js/format.js",
    "itpk-blockly.js",
    "blockly/blocks.js",
    "blockly/javascript.js"
  ],
  "dependencies": [
    "itpk.js"
  ],
  "msg": "blockly/msg",
  "blocksMsg": "blockly/msg/blocks",
  "toolbox": "blockly/toolbox.xml"
}
```

> 以下的操作均在浏览器无痕模式下进行。（等你足够了解后，可以先移除积木后刷新再重新载入积木）。

现在你可以提交它，然后等一会提交成功后，可以载入 `https://junhuanchen.github.io/webduino-blockly-template/blockly.json` 积木查看效果了。

![](images/new_toolbox.png)
