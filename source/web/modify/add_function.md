
## 添加对应功能

现在积木已经生成，但是我们要如何为如下代码添加对应的功能呢？

```javascript
scope.itpk_answer = function () {
  return "webduino.module.RobotItpk.answer()";
}
```

我们继续看它的生成代码，这个实际上就是生成（返回）一段调用 blockly/itpk-blockly.js 函数的 `webduino.module.RobotItpk.answer()` 代码，所以我们需要在 blockly/itpk-blockly.js 中提供这个函数的实现，也就是如下代码。

```javascript
RobotItpk.answer = function () {
    return answer.replace("[cqname]", "moli");
}
```

我们可以在单元测试（unit_test）中得知它的用法。

```javascript
function unit_test() {
  webduino.module.RobotItpk.ask('东莞天气如何？');
  setTimeout(function(){
    console.log(webduino.module.RobotItpk.answer());
    webduino.module.RobotItpk.ask('高雄天气如何？');
    setTimeout("console.log(webduino.module.RobotItpk.answer())", 1000);
  }, 1000);
}
```

但是为什么可以链接起来？这需要看 blockly.json 的定义。

```javascript
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

关于依赖的 javascript 代码的使用情况，我们需要将 Blockly 分成两个场景，第一是积木生成代码阶段的，第二是生成代码的时候运行依赖，也就是 `scripts` 和 `dependencies` 两列，如你所见的是 `scripts` 包含的是 Blockly 积木相关联的实现代码，而 `dependencies` 则是代码运行的时候依赖的 javascript 代码，例如 `itpk.js` 代码可以在运行代码的时候实现。
