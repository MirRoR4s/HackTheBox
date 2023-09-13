## 总结

1. nmap扫描发现web服务
2. burp suite发现web登录页面
3. 结合信息泄露篡改cookie以管理员权限上传php反弹shell
4. suid提权获得root的flag

- 如何查找具有suid权限的文件？一般是sudo -l，但是本靶机不行，后面是通过查找属于 bugtracker组的文件发现了一个。
- 
