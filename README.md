###  这些年 从 tp5 走过的那些坑

#### 起步

> 下载一个thinkphp5 压缩包

#### 配置

1. phpstudy 2017(目前最新版本)
2. 配置php环境变量(可从phpstudy选个5.6或者其他较高版本的php配置，配置方法：百度)
3. 编辑器(sublime，phpstorm， 记事本， etc..)

#### 步骤

1. 解压thinkphp5压缩包 重新命名为 tp5 并将 thinkphp5 放入 phpstudy的www文件目录下
2. 打开浏览器 输入网址 localhost/tp5/public/index.php (默认端口80)
3. 弹出欢迎界面，表示成功；否则请重试，或参考[官方文档](https://www.kancloud.cn/manual/thinkphp5/)

----
### 以下为可能遇到的问题

###### 隐藏index.php

	// www/tp5 --目录
	// Apache: .htaccess
	<IfModule mod_rewrite.c>
		Options +FollowSymlinks
		RewriteEngine On
		RewriteCond %{REQUEST_FILENAME} !-d
		RewriteCond %{REQUEST_FILENAME} !-f
		RewriteRule ^(.*)$ index.php?s=$1 [QSA,PT,L]
	</IfModule>

	// IIS: web.config
	<?xml version="1.0" encoding="UTF-8"?>
	<configuration>
	<system.webServer>
	<rewrite>
	<rules>
	<rule name="Imported Rule 1" stopProcessing="true">
	<match url="^(.*)$" ignoreCase="false" />
	<conditions logicalGrouping="MatchAll">
	<add input="{REQUEST_FILENAME}" matchType="IsDirectory" ignoreCase="false" negate="true" />
	<add input="{REQUEST_FILENAME}" matchType="IsFile" ignoreCase="false" negate="true" />
	</conditions>
	<action type="Rewrite" url="index.php/{R:1}" appendQueryString="true" />
	</rule>
	</rules>
	</rewrite>
	</system.webServer>
	</configuration>

###### 
	 


----
######### PS：以上内容不做详细分析，仅仅提供解决方案，也只是方便本人查询
