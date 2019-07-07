# &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; BPI-STEAM/Dev 开发指导

[![Open Source Love](https://badges.frapsoft.com/os/v3/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badge/)

[![Documentation Status](https://readthedocs.org/projects/bpi-steam-dev/badge/?version=latest)](https://bpi-steam-dev.readthedocs.io/zh_CN/latest/?badge=latest)

## how to edit

The document content is in [source](https://github.com/BPI-STEAM/Dev/tree/master/source).

文档结构如下：（如果你需要操作，请扫一遍关键目录，可以用 markdown 也可以用 rst，看自己喜欢）

- conf.py 自动化部署脚本，不需要修改
- contents.rst 和 index.rst 为 根目录（进入网站左边一排），需保持一致。

如果想提交内容，直接提交即可，提交后，项目会自动编译部署到网站，而你只需要在本地 build 核对一下即可，如果出现问题请提交 issue 或直接反馈到群里。

## python

```unix
pip install sphinx, sphinx_rtd_theme, recommonmark
```

## powershell

```bat
.\make.bat html
```
