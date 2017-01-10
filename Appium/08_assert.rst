
Appium使用断言
====================

在编写Appium脚本中，可借用Python unittest断言。

比如判断activity：

.. code-block:: python

  assertEqual(".activity.MainActivity",driver.current_activity)


