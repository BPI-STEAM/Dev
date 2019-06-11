.. Introduction to BPI-STEAM documentation master file, created by
   sphinx-quickstart on Sun May 26 22:43:43 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to BPI-STEAM documentation!
=====================================================

.. Hint::

    欢迎来到 BPI-STEAM 的开发指导，本项目托管于 `Github BPI-STEAM <https://github.com/BPI-STEAM>`_ 开源组织。

.. Attention::

    此处文档并不会照顾到一般用户的理解，请先具备隔壁 `用户文档 <https://bpi-steam-docs.readthedocs.io>`_ 的基础。
    
以下是我们所用的 BPI-BIT 教育开发板。

.. image:: _static/facade.gif

BPI-BIT 是一款基于 ESP32 高性能芯片且兼容 micro:bit 设计的开源 STEAM 教育产品。

.. toctree::
   :maxdepth: 2
   :caption: BPI-BIT
   
   bpi-steam/readme
   bpi-steam/driver

开发 MicroPython 模块
---------------------------

在这里将会教会你如何优雅地设计与开发一个 MicroPython 的 import 模块。

.. toctree::
   :maxdepth: 2
   :caption: MicroPython

   mpy/index.rst

开发 Webduino 积木 
---------------------------

在这里将会教会你如何优雅地设计与开发一个 Webduino 的 Blockly 积木。

.. toctree::
   :maxdepth: 2
   :caption: Webduino
   
   web/index.rst


金手指拓展板设计
---------------------------

稍后补充，不好意思，此处是备选目录。

.. toctree::
   :maxdepth: 2
   :caption: 金手指拓展板

.. image:: _static/footer.png

接入 IOT 平台
---------------------------

.. toctree::
   :maxdepth: 2
   :caption: IoT
   
   iot/index.rst

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
