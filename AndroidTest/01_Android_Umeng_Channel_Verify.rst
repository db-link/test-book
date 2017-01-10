

验证Android渠道版本渠道号
==============================

国内市场上有许许多多的应用市场，常见的有：百度、360、腾讯应用宝、豌豆荚等。
其他手机厂家如小米、华为、魅族、三星等都有自己的应用市场，总共有上百家！

----

问题
--------
发版前，Android工程师打包了上百个渠道版本，如何检验渠道号与apk名称是否一致？

希望自动去获取apk的友盟渠道号，并自动进行校验。


怎么做
--------
Android Apk的渠道号一般存放在AndroidManifest.xml文件中。

#. 批量反编译Android Apk
#. 遍历反编译后的apk文件夹，从AndroidManifest.xml取出渠道号
#. 比较渠道号与apk名称
#. 将测试结果写入csv文件

a. 反编译Android Apk
^^^^^^^^^^^^^^^^^^^^^^
----

反编译Apk,得到源文件和资源文件.

渠道号存放在 **AndroidManifest.xml** 文件中。

反编译工具apktool.jar: https://bitbucket.org/iBotPeaches/apktool/downloads

.. code-block:: java
	
    java -jar apktool.jar d -f package.apk	

输出结果如下：

.. code-block:: java

    I: Using Apktool 2.1.0 on test.apk
    I: Loading resource table...
    I: Decoding AndroidManifest.xml with resources...
    I: Loading resource table from file: C:\Users\Administrator\apktool\framework\1.apk
    I: Regular manifest package...
    I: Decoding file-resources...
    I: Decoding values */* XMLs...
    I: Baksmaling classes.dex...
    I: Copying assets and libs...
    I: Copying unknown files...
    I: Copying original files...


**备注:** 
Android apk整体反编译所需时间较长，如只获取AndroidManifest.xml文件，那么只需反编译
资源文件即可，不对源代码进行反编译，使用参数 **-s** ,只需花费很少时间.

b. 获取渠道号
^^^^^^^^^^^^^^^^^^^^^
----

遍历AndroidManifest.xml文件，取出渠道号所在行.

python实现如下：

.. code-block:: python

    with open(manifest,'r+') as m:
        umeng_line = [ line.strip() for line in m.readlines() if 'UMENG_CHANNEL' in line ]
    #取出渠道号所在行后，进行分割、去除.


或者直接输入编译后的apk文件夹，具体如下：

.. code-block:: python

    def get_apk_umeng_value(reverse_folder):
        umeng_channel = []  
        for rfn in reverse_folder:
            manifest = os.path.join(version_catalogue,rfn,'AndroidManifest.xml')
            with open(manifest,'r+') as m:
                umeng_line = [ line.strip() for line in m.readlines() if 'UMENG_CHANNEL' in line ]
                    for ul in umeng_line:
                        ucv = ul.split('=')[2]
                        #使用strip过滤"/>//--等特殊字符
                        umeng_channel.append(ucv.strip('"/>// --'))
        return umeng_channel


**完整代码地址：**

    https://github.com/midada/Android-Test/blob/master/channelverify.py
