---
description: https://academy.hackthebox.com/module/18/section/71
---

# User Management

User management is an essential part of Linux administration. Sometimes we need to create new users or add other users to specific groups. Another possibility is to execute commands as a different user. After all, it is not too rare that users of only one specific group have the permissions to view or edit specific files or directories. This, in turn, allows us to collect more information locally on the machine, which can be very important. Let us take a look at the following example of how to execute code as a different user.

**Execution as a user**

```bash
MirRoR4s@htb[/htb]$ cat /etc/shadow

cat: /etc/shadow: Permission denied
```

**Execution as root**

```bash
MirRoR4s@htb[/htb]$ sudo cat /etc/shadow

root:<SNIP>:18395:0:99999:7:::
daemon:*:17737:0:99999:7:::
bin:*:17737:0:99999:7:::
<SNIP>
```

Here is a list that will help us to better understand and deal with user management.

<table data-header-hidden><thead><tr><th width="178"></th><th></th></tr></thead><tbody><tr><td><strong>Command</strong></td><td><strong>Description</strong></td></tr><tr><td><code>sudo</code></td><td>Execute command as a different user.</td></tr><tr><td><code>su</code></td><td>The <code>su</code> utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed.</td></tr><tr><td><code>useradd</code></td><td>Creates a new user or update default new user information.</td></tr><tr><td><code>userdel</code></td><td>Deletes a user account and related files.</td></tr><tr><td><code>usermod</code></td><td>Modifies a user account.</td></tr><tr><td><code>addgroup</code></td><td>Adds a group to the system.</td></tr><tr><td><code>delgroup</code></td><td>Removes a group from the system.</td></tr><tr><td><code>passwd</code></td><td>Changes user password.</td></tr></tbody></table>

User management is essential in any operating system, and the best way to become familiar with it is to try out the individual commands in conjunction with their various options.

**Questions**

Answer the question(s) below to complete this Section and earn cubes!

\+ 0  Which option needs to be set to create a home directory for a new user using "useradd" command?&#x20;

{% embed url="https://linux.die.net/man/8/useradd" %}

\+ 0  Which option needs to be set to lock a user account using the "usermod" command? (long version of the option)&#x20;

```
--lock # 这玩意真的对吗？我看文档似乎说的是禁用掉用户的密码，难道这不应该理解成允许空密码登录吗？
```

{% embed url="https://linux.die.net/man/8/usermod" %}

\+ 0  Which option needs to be set to execute a command as a different user using the "su" command? (long version of the option)

{% embed url="https://linux.die.net/man/1/su" %}
