---
title: vue 在系统上禁止运行脚本
date: 2022-11-22 12:02:07
tags: [Vue,Error]
categories: 软件&硬件问题汇总 #分类
---
1. 首先需要在编译器终端中执行命令：**get-ExecutionPolicy**，
终端返回 ：**Restricted**   //表示脚本被禁止，无法使用
2. 在命令行打入命令  **set-ExecutionPolicy RemoteSigned：**//设置执行策略为RemoteSigned。
**如果显示没有权限修改 注意用管理员身份运行编辑器（vscode或hbuilder等）**
3. 然后我们再执行 **get-ExecutionPolicy**
显示**RemoteSigned**，即表示可以正常执行脚本命令了。
