---
title: MarkdownPad2 Github在线报错
tags: 
- MarkdownPad2在线报错
categories:
- hexo
abbrlink: 3fd15368
date: 2019-01-05 04:16:54
---
# 解决方案：

## 在您的注册表中进行以下更改，它应该工作：
## 1.）[.NET Framework强大的加密](https://docs.microsoft.com/en-us/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server#enable-strong-cryptography-in-net-framework-45-or-higher)注册表项

``` bash
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SchUseStrongCrypto"=dword:00000001
```

## 2.）[安全通道（Schannel）TLS 1.2](https://docs.microsoft.com/en-us/windows-server/security/tls/tls-registry-settings#tls-12)注册表项

``` bash
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2]

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client]
"DisabledByDefault"=dword:00000000
"Enabled"=dword:00000001

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server]
"DisabledByDefault"=dword:00000000
"Enabled"=dword:00000001
```

# 参考：
## 1. [GFM在线模式SSL / TLS安全通道中止](http://forums.apricitysoftware.com/t/gfm-online-mode-ssl-tls-secure-channel-aborts/1313/7)
## 2. [MarkdownPad2不能用Github在线样式渲染](https://segmentfault.com/q/1010000014637647)
## 3. [asp.net - .NET Framework 4.0中的TLS 1.2 - Stack Overflow](https://stackoverflow.com/a/44153734/4473405)
## 4. [在Office Online Server中启用TLS 1.1和TLS 1.2支持 Microsoft Docs](https://docs.microsoft.com/en-us/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server#enable-strong-cryptography-in-net-framework-45-or-higher)
## 5. [传输层安全性（TLS）注册表设置| Microsoft Docs](https://docs.microsoft.com/en-us/windows-server/security/tls/tls-registry-settings#tls-12)
