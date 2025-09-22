---
layout: hexo教程
title: 添加woff2切片
date: 2024-06-23 07:41:38
tags: 教程
cover: https://www.10wallpaper.com/wallpaper/1366x768/2406/Dusk_Coast_Beach_Summer_Moon_Vik_Iceland_5K_1366x768.jpg # 必选
poster: # 海报（可选，全图封面卡片）
  topic: 教程 # 可选
  headline: 为你的blog添加字体 # 必选
  caption: 整合于网络，非盈利性 # 可选
  color: 标题颜色
---

# hexo添加woff2切片

1. Stellar主题当中，作者写的教程关于woff2切片加载比较模糊，我这里做一个补充说明，首先如果你导入的ttf文档比较大的时候，需要使用fonttools进行切割，这不得不使用PyCharm了，所以我们第一个步骤就是安装他

2. PyCharm：[点我下载](https://www.jetbrains.com/zh-cn/pycharm/download/?section=windows) 安装方式不做过多赘述

3. 破解工具：[点我下载](https://96110.pages.dev/ChinaUnicom/CU) 进入到文件夹 `/jetbra`——将上面图示的补丁的所属文件夹 `/jetbra` 复制电脑某个位置**，补丁所属文件夹需单独存放，且放置的路径不要有中文与空格`，`以免 Pycharm 读取补丁错误**。——点击进入 `/jetbra` 补丁目录，再点击进入 `/scripts` 文件夹，双击执行 `install-current-user.vbs` 破解——重新打开 Pycharm 后，复制下面的激活码：
   
   <div>
   EUWT4EE9X2-eyJsaWNlbnNlSWQiOiJFVVdUNEVFOVgyIiwibGljZW5zZWVOYW1lIjoic2lnbnVwIHNjb290ZXIiLCJhc3NpZ25lZU5hbWUiOiIiLCJhc3NpZ25lZUVtYWlsIjoiIiwibGljZW5zZVJlc3RyaWN0aW9uIjoiIiwiY2hlY2tDb25jdXJyZW50VXNlIjpmYWxzZSwicHJvZHVjdHMiOlt7ImNvZGUiOiJQU0kiLCJmYWxsYmFja0RhdGUiOiIyMDI1LTA4LTAxIiwicGFpZFVwVG8iOiIyMDI1LTA4LTAxIiwiZXh0ZW5kZWQiOnRydWV9LHsiY29kZSI6IlBDIiwiZmFsbGJhY2tEYXRlIjoiMjAyNS0wOC0wMSIsInBhaWRVcFRvIjoiMjAyNS0wOC0wMSIsImV4dGVuZGVkIjpmYWxzZX0seyJjb2RlIjoiUFBDIiwiZmFsbGJhY2tEYXRlIjoiMjAyNS0wOC0wMSIsInBhaWRVcFRvIjoiMjAyNS0wOC0wMSIsImV4dGVuZGVkIjp0cnVlfSx7ImNvZGUiOiJQV1MiLCJmYWxsYmFja0RhdGUiOiIyMDI1LTA4LTAxIiwicGFpZFVwVG8iOiIyMDI1LTA4LTAxIiwiZXh0ZW5kZWQiOnRydWV9LHsiY29kZSI6IlBDV01QIiwiZmFsbGJhY2tEYXRlIjoiMjAyNS0wOC0wMSIsInBhaWRVcFRvIjoiMjAyNS0wOC0wMSIsImV4dGVuZGVkIjp0cnVlfV0sIm1ldGFkYXRhIjoiMDEyMDIyMDkwMlBTQU4wMDAwMDUiLCJoYXNoIjoiVFJJQUw6MzUzOTQ0NTE3IiwiZ3JhY2VQZXJpb2REYXlzIjo3LCJhdXRvUHJvbG9uZ2F0ZWQiOmZhbHNlLCJpc0F1dG9Qcm9sb25nYXRlZCI6ZmFsc2V9-FT9l1nyyF9EyNmlelrLP9rGtugZ6sEs3CkYIKqGgSi608LIamge623nLLjI8f6O4EdbCfjJcPXLxklUe1O/5ASO3JnbPFUBYUEebCWZPgPfIdjw7hfA1PsGUdw1SBvh4BEWCMVVJWVtc9ktE+gQ8ldugYjXs0s34xaWjjfolJn2V4f4lnnCv0pikF7Ig/Bsyd/8bsySBJ54Uy9dkEsBUFJzqYSfR7Z/xsrACGFgq96ZsifnAnnOvfGbRX8Q8IIu0zDbNh7smxOwrz2odmL72UaU51A5YaOcPSXRM9uyqCnSp/ENLzkQa/B9RNO+VA7kCsj3MlJWJp5Sotn5spyV+gA==-MIIETDCCAjSgAwIBAgIBDTANBgkqhkiG9w0BAQsFADAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBMB4XDTIwMTAxOTA5MDU1M1oXDTIyMTAyMTA5MDU1M1owHzEdMBsGA1UEAwwUcHJvZDJ5LWZyb20tMjAyMDEwMTkwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCUlaUFc1wf+CfY9wzFWEL2euKQ5nswqb57V8QZG7d7RoR6rwYUIXseTOAFq210oMEe++LCjzKDuqwDfsyhgDNTgZBPAaC4vUU2oy+XR+Fq8nBixWIsH668HeOnRK6RRhsr0rJzRB95aZ3EAPzBuQ2qPaNGm17pAX0Rd6MPRgjp75IWwI9eA6aMEdPQEVN7uyOtM5zSsjoj79Lbu1fjShOnQZuJcsV8tqnayeFkNzv2LTOlofU/Tbx502Ro073gGjoeRzNvrynAP03pL486P3KCAyiNPhDs2z8/COMrxRlZW5mfzo0xsK0dQGNH3UoG/9RVwHG4eS8LFpMTR9oetHZBAgMBAAGjgZkwgZYwCQYDVR0TBAIwADAdBgNVHQ4EFgQUJNoRIpb1hUHAk0foMSNM9MCEAv8wSAYDVR0jBEEwP4AUo562SGdCEjZBvW3gubSgUouX8bOhHKQaMBgxFjAUBgNVBAMMDUpldFByb2ZpbGUgQ0GCCQDSbLGDsoN54TATBgNVHSUEDDAKBggrBgEFBQcDATALBgNVHQ8EBAMCBaAwDQYJKoZIhvcNAQELBQADggIBABqRoNGxAQct9dQUFK8xqhiZaYPd30TlmCmSAaGJ0eBpvkVeqA2jGYhAQRqFiAlFC63JKvWvRZO1iRuWCEfUMkdqQ9VQPXziE/BlsOIgrL6RlJfuFcEZ8TK3syIfIGQZNCxYhLLUuet2HE6LJYPQ5c0jH4kDooRpcVZ4rBxNwddpctUO2te9UU5/FjhioZQsPvd92qOTsV+8Cyl2fvNhNKD1Uu9ff5AkVIQn4JU23ozdB/R5oUlebwaTE6WZNBs+TA/qPj+5/we9NH71WRB0hqUoLI2AKKyiPw++FtN4Su1vsdDlrAzDj9ILjpjJKA1ImuVcG329/WTYIKysZ1CWK3zATg9BeCUPAV1pQy8ToXOq+RSYen6winZ2OO93eyHv2Iw5kbn1dqfBw1BuTE29V2FJKicJSu8iEOpfoafwJISXmz1wnnWL3V/0NxTulfWsXugOoLfv0ZIBP1xH9kmf22jjQ2JiHhQZP7ZDsreRrOeIQ/c4yR8IQvMLfC0WKQqrHu5ZzXTH4NO3CwGWSlTY74kE91zXB5mwWAx1jig+UXYc2w4RkVhy0//lOmVya/PEepuuTTI4+UJwC7qbVlh5zfhj8oTNUXgN0AOc+Q0/WFPl1aw5VV/VrO8FCoB15lFVlpKaQ1Yh+DVU8ke+rt9Th0BCHXe0uZOEmH0nOnH/0onD
   </div>
   
   粘贴到输入框内，点击 `Activate` 按钮，就激活成功了。

4. 然后下载常用文字 [点我下载](https://96110.pages.dev/ChinaUnicom/CU) 把3500.txt 导入PyCharm的ProJect ，**新建项目工程**，在此文件夹下打开terminal  输入`pip install fontTools`之后可能会出现因为目录没有放入系统变量而导致的错误，会提示程序不存在，这里需要进入电脑高级设置，将path环境变量引入，如果**没有报错请跳过**，最后便是`pyftsubset.exe 你字体名字.ttf --text-file=3500.txt`***注意 这里需要把你的字体文件放在和TXT同级目录之下***

5. 之后会输出ttf简化版的文件，他内存更小，但仅仅包含常用字3500个，因为是网站，太大的字体会导致加载太卡，使用10mb以上的字体属于一种避讳，有时可能因为加载不出来导致字体全白

6. 之后便是ttf切片 这里推荐使用([在线字体分包器 ](https://chinese-font.netlify.app/online-split/))当转换出来之后，便是wooff2切片，**把css文件复制出来**，**删除除woff2以外所有文件**，导入到`\博客目录\source\font\`

7. 把分包器**css**中的@font-face下面的内容复制出来，导入到**blog主题css**下的_custom.styl当中，注意这里路径`./`是进入上级目录 ，是相对路径，这里的路径在source下级，例如可以把`./`替换成`/font/你的切片.wofff2` ***注意，这里的切片有多个***

8. 查看你复制的内容中的`font-family: "FZSJ-TIANSDQSYZ"` <u>FZSJ-TIANSDQSYZ</u>便是你字体的家族名，之后进入主题文件
   
   <div>
   font-family:
       logo: 'system-ui, "Microsoft Yahei", "Segoe UI", -apple-system, Roboto, Ubuntu, "Helvetica Neue", Arial, "WenQuanYi Micro Hei", sans-serif'
       body: 'FZSJ-TIANSDQSYZ'//字体名字
       code: 'Menlo, Monaco, Consolas, system-ui, "Courier New", monospace, sans-serif'
       codeblock: 'Menlo, Monaco, Consolas, system-ui, "Courier New", monospace, sans-serif'
   </div>

9. 例外补充一点，代码块换行要ctrl加ent 差点就要另起一段了 悲

10. 如果无效果可尝试pubilc当中的main.css，重复上述7的步骤

11. 之后就是cl+g+s+d了，刷新便可以看到你的hexo字体得到更改了
