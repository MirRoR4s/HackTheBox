---
description: https://academy.hackthebox.com/module/35/section/219
---

# HyperText Transfer Protocol (HTTP)

Today, the majority of the applications we use constantly interact with the internet, both web and mobile applications. Most internet communications are made with web requests through the HTTP protocol. [HTTP](https://tools.ietf.org/html/rfc2616) is an application-level protocol used to access the World Wide Web resources. The term `hypertext` stands for text containing links to other resources and text that the readers can easily interpret.

如今，我们经常使用的大部分应用程序都需要和互联网交互，例如web应用程序和移动端应用程序皆是如此。大部分互联网通信是通过HTTP协议发起web请求进行的。HTTP是一个用于访问万维网WWW的应用层协议，中文名译为超文本传输协议。超文本是一种特殊的文本，该文本包含了到其他资源和易被读者理解的文本的链接。

HTTP communication consists of a client and a server, where the client requests the server for a resource. The server processes the requests and returns the requested resource. The default port for HTTP communication is port `80`, though this can be changed to any other port, depending on the web server configuration. The same requests are utilized when we use the internet to visit different websites. We enter a `Fully Qualified Domain Name` (`FQDN`) as a `Uniform Resource Locator` (`URL`) to reach the desired website, like [www.hackthebox.com](http://www.hackthebox.com/).

HTTP通信由客户端和服务器端组成，客户端会请求服务器端上的资源。服务器端会处理请求并返回所请求的资源。HTTP默认的通信端口是80端口，但可基于web服务器的配置将通信端口改为其他的端口。当我们使用互联网访问不同的网站时，会使用到相同的请求。我们输入一个全限定域名（FQDN）作为统一资源定位符以到达期望的网站，比如www.hackthebox.com。

***

### URL

Resources over HTTP are accessed via a `URL`, which offers many more specifications than simply specifying a website we want to visit. Let's look at the structure of a URL:&#x20;

我们通过URL访问HTTP上的资源。比起简单的指明我们欲访问的网站，URL提供了更多的规范。以下是一个URL的具体结构：

![url\_structure](https://academy.hackthebox.com/storage/modules/35/url\_structure.png)

Here is what each component stands for:

<table data-header-hidden><thead><tr><th width="112"></th><th width="207"></th><th></th></tr></thead><tbody><tr><td><strong>Component</strong></td><td><strong>Example</strong></td><td><strong>Description</strong></td></tr><tr><td><code>Scheme</code></td><td><code>http://</code> <code>https://</code></td><td>This is used to identify the protocol being accessed by the client, and ends with a colon and a double slash (<code>://</code>) 指明客户端所用的协议，以冒号加两个斜杠结尾。</td></tr><tr><td><code>User Info</code></td><td><code>admin:password@</code></td><td>This is an optional component that contains the credentials (separated by a colon <code>:</code>) used to authenticate to the host, and is separated from the host with an at sign (<code>@</code>) 这是一个可选的部分，包含了用于对主机进行身份验证的凭据。凭据由账号密码构成并由冒号分隔。同时User InfoHost之间用@分隔。</td></tr><tr><td><code>Host</code></td><td><code>inlanefreight.com</code></td><td>The host signifies the resource location. This can be a hostname or an IP address</td></tr><tr><td></td><td></td><td>host意味着资源的位置，host可以是主机名或IP地址。</td></tr><tr><td><code>Port</code></td><td><code>:80</code></td><td><p>The <code>Port</code> is separated from the <code>Host</code> by a colon (<code>:</code>). If no port is specified, <code>http</code> schemes default to port <code>80</code> and <code>https</code> default to port <code>443</code> </p><p><code>端口和主机之间由冒号分隔。如果未指定端口，http协议默认使用80端口，https协议默认使用443端口。</code></p></td></tr><tr><td><code>Path</code></td><td><code>/dashboard.php</code></td><td>This points to the resource being accessed, which can be a file or a folder. If there is no path specified, the server returns the default index (e.g. <code>index.html</code>). Path指出要访问的资源，可以是一个文件或文件夹。若没有指定path，服务端会返回默认的index，比如index.html等。</td></tr><tr><td><code>Query String</code></td><td><code>?login=true</code></td><td>The query string starts with a question mark (<code>?</code>), and consists of a parameter (e.g. <code>login</code>) and a value (e.g. <code>true</code>). Multiple parameters can be separated by an ampersand (<code>&#x26;</code>). 查询字符串以一个问号开始，包含一个参数以及参数值。多个参数之间用&#x26;分隔</td></tr><tr><td><code>Fragments</code></td><td><code>#status</code></td><td><p>Fragments are processed by the browsers on the client-side to locate sections within the primary resource (e.g. a header or section on the page). </p><p>Fragements由客户端的浏览器进行处理，主要是用于定位首要资源内的小节。比如页面上的header或是section</p></td></tr></tbody></table>

Not all components are required to access a resource. The main mandatory fields are the scheme and the host, without which the request would have no resource to request.

当通过URL访问资源时，并不要求用到URL的全部组成部分。主要的必填字段是协议scheme和主机host，没有它们，请求就没有资源可请求

### HTTP Flow

![HTTP\_Flow](https://academy.hackthebox.com/storage/modules/35/HTTP\_Flow.png)

The diagram above presents the anatomy of an HTTP request at a very high level. The first time a user enters the URL (`inlanefreight.com`) into the browser, it sends a request to a DNS (Domain Name Resolution) server to resolve the domain and get its IP. The DNS server looks up the IP address for `inlanefreight.com` and returns it. All domain names need to be resolved this way, as a server can't communicate without an IP address.

上图在一个非常高的层次给出了HTTP请求的流程。首先用户在浏览器输入URL（`inlanefreight.com`），之后浏览器会向DNS服务器发起一个请求以解析域名并得到其ip地址。DNS服务器会查询inlanefreight.com的IP地址并返回。所有的域名都需要通过这种方式来解析，因为服务器端在没有IP地址的情况下无法进行通信。

Note: Our browsers usually first look up records in the local '`/etc/hosts`' file, and if the requested domain does not exist within it, then they would contact other DNS servers. We can use the '`/etc/hosts`' to manually add records to for DNS resolution, by adding the IP followed by the domain name.

注意：我们的浏览器通常会首先查询本地的 /etc/hosts 文件的域名记录，如果所请求的域名在该文件内不存在，那么浏览器才会联系DNS服务器。 我们可以手工地向/etc/hosts文件添加域名解析记录，只需要在IP后面跟上域名即可。

Once the browser gets the IP address linked to the requested domain, it sends a GET request to the default HTTP port (e.g. `80`), asking for the root `/` path. Then, the web server receives the request and processes it. By default, servers are configured to return an index file when a request for `/` is received.

一旦浏览器获得了和请求域名相关联的IP地址，那么浏览器就会向默认的HTTP端口发起一个GET请求，要求获得根目录的资源/。然后，web服务器会接收到这个请求并进行相应处理。默认情况下，当接收到一个访问 / 的请求时，服务器被配置为返回一个默认文件。

In this case, the contents of `index.html` are read and returned by the web server as an HTTP response. The response also contains the status code (e.g. `200 OK`), which indicates that the request was successfully processed. The web browser then renders the `index.html` contents and presents it to the user.

在这种情况下，服务器会读取 index.html 的内容并将其作为 HTTP 响应返回。响应包含了状态码（比如200 OK）。状态码表明了请求已被成功处理。随后 web 浏览器会渲染 index.html的内容并将其展示给用户。

Note: This module is mainly focused on HTTP web requests. For more on HTML and web applications, you may refer to the [Introduction to Web Applications](https://academy.hackthebox.com/module/details/75) module.

***

### cURL

In this module, we will be sending web requests through two of the most important tools for any web penetration tester, a Web Browser, like Chrome or Firefox, and the `cURL` command line tool.

在本模块中，我们将会通过两个重要的工具来发起 web 请求。这两个工具分别是 Web 浏览器，比如谷歌或火狐，另一个则是 cURL 命令行工具。

[cURL](https://curl.haxx.se/) (client URL) is a command-line tool and library that primarily supports HTTP along with many other protocols. This makes it a good candidate for scripts as well as automation, making it essential for sending various types of web requests from the command line, which is necessary for many types of web penetration tests.

cURL（client URL）是一个命令行工具和库，主要支持HTTP及许多其他协议。这使得它成为脚本和自动化的一个很好的候选。\
这个工具可以从命令行发送不同类型的 web 请求，这对于许多类型的 web 测试来说是很必要的。&#x20;

We can send a basic HTTP request to any URL by using it as an argument for cURL, as follows:

我们可以发起一个到任意 URL 的 HTTP 请求，只需将该 URL 作为 cURL 的参数即可，具体示例如下：

```bash
MirRoR4s@htb[/htb]$ curl inlanefreight.com

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
...SNIP...
```

We see that cURL does not render the HTML/JavaScript/CSS code, unlike a web browser, but prints it in its raw format. However, as penetration testers, we are mainly interested in the request and response context, which usually becomes much faster and more convenient than a web browser.

我们可以看到不像 web 浏览器，cURL 并不会渲染 HTML/JavaScript/CSS 代码，而是打印出其原始格式。然而，作为渗透测试者，我们主要对请求及响应的上下文感兴趣，所以是否渲染HTML等代码并不重要，所以 cURL 比起 web 浏览器来说，是一个更加快速和方便的工具。

We may also use cURL to download a page or a file and output the content into a file using the `-O` flag. If we want to specify the output file name, we can use the `-o` flag and specify the name. Otherwise, we can use `-O` and cURL will use the remote file name, as follows:

&#x20; 我们也可以使用 cURL 下载一个网页或文件并使用 `-O` 标志将其内容输出到一个文件中。若我们想要指定输出的文件名，我们可以使用 `-o` 标志后跟文件名，否则输出的文件名默认为远程的文件名，具体示例如下：

```bash
MirRoR4s@htb[/htb]$ curl -O inlanefreight.com/index.html
MirRoR4s@htb[/htb]$ ls
index.html
```

As we can see, the output was not printed this time but rather saved into `index.html`. We noticed that cURL still printed some status while processing the request. We can silent the status with the `-s` flag, as follows:

&#x20; 如我们所见，这一次响应的内容没有被打印出来，而是被保存到了一个名为 index.html 的文件中。我们注意到 cURL 在处理请求时仍然会打印出一些状态信息。我们可以使用 `-s` 标志隐藏这些状态信息，具体示例如下：

```bash
MirRoR4s@htb[/htb]$ curl -s -O inlanefreight.com/index.html
```

This time, cURL did not print anything, as the output was saved into the `index.html` file. Finally, we may use the `-h` flag to see what other options we may use with cURL:

&#x20; 这一次cURL将不会打印任何信息，因为输出被保存到index.html文件中去了。最后，我们可以使用 -h 标志查看 cURL 支持的选项。

```bash
MirRoR4s@htb[/htb]$ curl -h
Usage: curl [options...] <url>
 -d, --data <data>   HTTP POST data
 -h, --help <category> Get help for commands
 -i, --include       Include protocol response headers in the output
 -o, --output <file> Write to file instead of stdout
 -O, --remote-name   Write output to a file named as the remote file
 -s, --silent        Silent mode
 -u, --user <user:password> Server user and password
 -A, --user-agent <name> Send User-Agent <name> to server
 -v, --verbose       Make the operation more talkative

This is not the full help, this menu is stripped into categories.
Use "--help category" to get an overview of all categories.
Use the user manual `man curl` or the "--help all" flag for all options.
```

As the above message mentions, we may use `--help all` to print a more detailed help menu, or `--help category` (e.g. `-h http`) to print the detailed help of a specific flag. If we ever need to read more detailed documentation, we can use `man curl` to view the full cURL manual page.

如上所示，我们也可以使用 `--help all` 来打印出更加具体的帮助菜单，或是使用 `--help category`（比如 -h http）来打印一个指定标志的具体帮助信息。若我们想要阅读更加具体的文档，我们可以使用 `man curl` 命令查看完整的 cURL 手册页。

In the upcoming sections, we will cover most of the above flags and see where we should use each of them.

在接下来的章节中，我们会涵盖上述大部分标志，并查看我们应在何种情况下使用他们。

**Questions**

Answer the question(s) below to complete this Section and earn cubes!

Target: Click here to spawn the target system!\


Cheat Sheet+ 1  To get the flag, start the above exercise, then use cURL to download the file returned by '/download.php' in the server shown above.\


> 开启靶机，用-O选项下载download.php即可
