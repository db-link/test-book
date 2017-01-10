
Apk签名校验
=================

对Apk签名进行校验，是发版前必不可少的工作。


.. code-block:: java

   keytool.exe -printcert -v -file CERT.RSA


输出结果如下：

::

    Owner: CN=wang, OU=xinhuan, O=xinhuan, L=beijing, ST=beijing, C=cn
    Issuer: CN=wang, OU=xinhuan, O=xinhuan, L=beijing, ST=beijing, C=cn
    Serial number: 469d1fe7
    Valid from: Tue Oct 27 19:38:09 CST 2015 until: Sat Oct 20 19:38:09 CST 2040
    Certificate fingerprints:
         MD5:  D9:0B:82:E7:D6:22:81:84:AE:A0:52:44:25:E0:61:B3
         SHA1: 16:D1:C5:4A:EE:04:DA:13:5C:67:F1:2E:42:7C:B5:BB:10:7D:D6:B4
         SHA256: 94:2B:75:83:57:DC:3C:BB:38:FE:B4:66:98:B2:12:CE:D9:31:92:BB:EA:B2:19:9D:58:74:FD:34:CC:D5:3D:7A
         Signature algorithm name: SHA256withRSA
         Version: 3

    Extensions:

    #1: ObjectId: 2.5.29.14 Criticality=false
    SubjectKeyIdentifier [
    KeyIdentifier [
    0000: 92 74 E2 63 9A BA 38 9C   7F A1 44 8C E5 D3 CA BC  .t.c..8...D.....
    0010: 79 FB 03 AF                                        y...
    ]
    ]
