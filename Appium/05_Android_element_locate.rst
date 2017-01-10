
Android元素定位
============================================

uiautomatiorviewer
---------------------------------------------

uiautomatorviewer是Android SDK自带的工具，在$ANDROID_HOME/tools目录下。

使用的测试App为：旧爱，在各大应用市场都可以搜索到。

点击uiautomatorviewer.bat后,将鼠标置于元素之上，如下：

.. image :: ../_static/image/UI_Automator_Viewer.png

使用resource_id定位
-------------------------------------

.. code-block:: python

    driver.find_element_by_id("com.jiuai:id/rbPersonal").click()
