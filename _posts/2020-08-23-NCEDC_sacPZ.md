---
layout:     post
title:      从NCEDC下载的L4短周期仪器的sacpz格式的仪器响应文件的问题
subtitle:   
date:       2020-08-23
author:     yunnd
header-img: img/Walle.jpg
catalog: true
tags:
    - seismic, data, response, sacpz
---
最近从北加州数据中心下载sacpz格式的仪器响应文件遇到了一些问题。有一个短周期仪器L4的[仪器响应文件](https://github.com/yunndlalala/yunndlalala.github.io/raw/master/file/NC.PHP.--.EHZ.sacpz.txt)很奇怪[](https://raw.githubusercontent.com/yunndlalala/yunndlalala.github.io/master/img/2020-08-23-NCEDC_sacPZ/PHP.jpg)  
包含两组A0, Sensitivity还有零极点。测试一通，再加上对比RESP文件之后发现，应该是这个文件写的有问题，把仪器其中一部的滤波单独列出来了。直接用这个文件，调用sac命令去除仪器响应虽然不会报错，但是结果是不对的。正确的文件应该是
* 把所有零极点写在一起
* 两个Sensitivity是重复的，用一个就好
* 另个A0相乘作为新的A0
* constant是新的sensitivity和A0的乘积
[](https://raw.githubusercontent.com/yunndlalala/yunndlalala.github.io/master/img/2020-08-23-NCEDC_sacPZ/PHP_right.jpg)



