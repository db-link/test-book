
解决中文输入问题
=====================

问题
----------------------

使用Appium进行Android测试时，使用send_keys()发送中文，输入框没有输入任何文本


解决办法
----------------------

使用Appium键盘,appium执行时,会在Android手机安装一个特殊键盘（即Appium Android lnput Manager for Unicode)

在Appum config中增加下列代码:

.. code-block:: python

   'unicodeKeyboard':True,
   'resetKeyboard':True

解释：

1. 使用unicode的编码方式发送字符
2. Unicode键盘并非虚拟键盘，在界面上不会显示出来


说明
-----------------------

::

    Android tests allow for Unicode input by installing and using a specialized keyboard 
    that allows the text to be passed as ASCII text between Appium and the application
    being tested.

    In order to utilize this functionality, set the unicodeKeyboard desired capability is 
    set to true. If the keyboard should be returned to its original state, the resetKeyboard 
    desired capability should also be set to true. Otherwise Appium’s Unicode keyboard will
    remain enabled on the device after the tests are completed.

    Then tests can pass Unicode text to editable fields using send_keys
