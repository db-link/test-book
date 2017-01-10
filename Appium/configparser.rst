
扩展:提高脚本复用、可配置性
======================================

问题
-------------------

在编写Appium脚本过程中，某个元素的resource_id或class可能在多个文件被使用，
当界面发生变化的时候，脚本将变得难以维护


解决办法
--------------------
使用configparser提高Appium脚本的复用性、可配置性
将element全部写到一个配置文件中，比如config.ini或config.cfg


比如config.ini配置文件如下:

.. code-block:: python

    ;登录
    [login]

    user = com.jiuai:id/et_phoneNumber
    pwd = com.jiuai:id/et_password
    loginbtn = com.jiuai:id/btn_common_login
    forgetpwd = com.jiuai:id/tv_forget_pwd
    userment = com.jiuai:id/tv_user_agreement
    tvregister = com.jiuai:id/tv_register


使用Python configparser读取配置文件
----------------------------------------

.. code-block:: python

    from configparser import ConfigParser

    # read config.ini
    cfg = configParser()
    cfg.read('config.ini')


读取其中值：

.. code-block:: python

    cfg.get('login','user')


实际操作：

.. code-block:: python

    driver.find_element_by_id(cfg.get('login','user')).click()

 
