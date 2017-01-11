
android adb 命令使用记录
===============================

adb debugging
------------------------------

打印当前连接设备

.. code-block:: java

    adb devices

获取信息
-----------------------------

获取手机系统系的信息，包括硬件和软件

.. code-block:: java

	adb shell getprop

> 使用adb shell getprop可以获取cpu、mem、网络信息。如：
	adb shell getprop ro.build.version.release	#获取手机android系统版本
	adb shell getprop ro.build.fingerprint		#获取手机品牌型号
	adb shell getprop ro.serialno				#获取手机设备ID
	adb shell getprop dhcp.wlan0.ipaddress		#获取当前连接的无线的ip地址
	adb shell getprop ro.product.cpu.abilist	#获取cpu

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
