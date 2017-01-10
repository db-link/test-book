
android adb 命令使用记录
===============================

adb debugging
------------------------------

打印当前连接设备

.. code-block:: java

    adb devices

包管理
-------------------------------

a. adb shell pm 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

列出手机中所有的第三方包

.. code-block:: java

    adb shell pm list package -3 | sort

列出手机中的系统package

.. code-block:: java

    adb shell pm list package -s | sort

清除app缓存数据

.. code-block:: java

    adb shell pm clear PackageName

b. adb shell am
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

监控activity

.. code-block:: java

    adb shell am monitor

文件管理
--------------------------------
