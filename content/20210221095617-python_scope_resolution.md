+++
title = "Python Scope Resolution"
author = ["Fangyuan Wang"]
tags = ["py"]
draft = false
+++

作用域是 Python 程序可以直接访问[命名空间]({{< relref "20210221095523-python_namespaces.md" >}})的正文区域。

在一个 Python 程序中，直接访问一个变量，会从内到外依次访问所有的作用域，
直到找到那个变量，否则就会报未定义的错误。
