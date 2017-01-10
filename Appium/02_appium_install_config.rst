
Appium安装配置 
=============================

下载
------------------------------

https://bitbucket.org/appium/appium.app/downloads/

Windows Download: 下载exe可执行文件进行安装

Mac Download: 下载dmg进行安装

Mac安装
----------------------------

.. code-block:: python

    > brew install node      # get node.js
    > npm install -g appium  # get appium
    > npm install wd         # get appium client
    > appium &               # start appium
    > node your-appium-test.js

Appium Andorid环境
------------------------------

* Android ADK API >= 17
* Java


Appium ios 环境
-----------------------------

* Mac OS X 10.10以上版本
* Xcode 6.0以上版本
* Apple Developer Tools

Appium Python Client
------------------------------

Appium Python Client封装了标准的selenium客户端类库, 为用户提供常见的selenium命令以及额外移动设备控制相关的命令.

使用pip命令进行安装Appium Python Client

.. code-block:: python:

    pip install Appium-Python-Client

Python Api具体见第三章节

用法
------------------------------

.. code-block:: python

    from appium import webdriver
    from selenium import webdriver

**例子**

.. code-block:: python

    from appium import webdriver
    
    #脚本运行需要增加下列环境参数    
    config = {
                'platformName' = 'Android',
                'platformVersion' = '6.0',
                'devicesName' = 'Android Emulator',
                'app' = '$PATH',
                'automationName' = 'Appium'
            }

    driver = webdriver.Remote('http://localhost:4723/wd/hub',config)

使用Android sdk 自带的adb命令获取devicesName

.. code-block:: java

    adb devices -l
