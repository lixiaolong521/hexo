---
title: 关于电脑显示“没有被指定在windows上运行，或者它包含错误”怎么解决？
date: 2022-11-21 21:56:45
tags: [windows系统,方法]
categories: 软件&硬件问题汇总 #分类
---

1. 首先需要找到并右击名称为“菜单”按钮，接着需要在接下来弹出来的下拉菜单中的下方，找到并点击名称为”运行“按钮：

2. 接着需要在接下来弹出来的页面框中输入“CMD”命令符，点击“确定”按钮：
<!-- more -->

3. 接着只需要输入“for %1 in (%windir%\system32\\*.dll) do regsvr32.exe /s %1”命令按下回车键：

4. 最后重启电脑桌面上就不会显示“没有被指定在windows上运行，或者它包含错误”即可解决问题了
