IoT 平台规划
=====================================================

项目文件已经托管到 Github，不过尚未完成，目前计划是写一部分文档，再写一部分代码去完成文档中的功能，一步一步慢慢来

项目地址
-------------------

https://github.com/Walkline80/IoT-Platform-Web


受到 `帅大叔`_ 之前玩的使用贝壳物联接入天猫精灵，再通过天猫精灵语音控制设备的启发，准备自己实现一下这个过程，不过不是通过第三方的物联网平台。

.. _帅大叔: https://github.com/youxinweizhi

这里的规划先不包括接入天猫精灵，因为只要平台建立起来，要接入是很简单的事情，其次，要自己实现物联网平台，理论上也并不困难(自我催眠中)

接入流程
------------------------------

1. 首先用户登录平台，注册账号并登录
2. 用户在平台上创建虚拟设备
3. 在设备开发中，使用虚拟设备提供的参数，使硬件设备和虚拟设备两者之间建立联系
4. 两者使用 http 轮训的方式交换信息，是交换信息，因为这里并不存在消息推送或者事件触发
5. 平台下发指令，包括控制设备动作以及获取设备状态
6. 是否需要设备主动上报数据呢？

.. Hint::
    所谓下发指令并不是从平台直接下达指令到设备让设备去执行，而是给虚拟设备标记一个期望值，比如期望设备做出 power on 的动作，或者期望得到设备当前的 power state，当硬件设备在轮训期间得到期望值会主动执行动作或者上报状态等。

.. toctree::
    :maxdepth: 2
    :hidden:
    
    sign_up
    operations
    create_device

更新日志
----------------------

.. toctree::
    :maxdepth: 2
        
    change_log
