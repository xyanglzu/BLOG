---
title: Python-matplotlib导入问题
toc: true
date: 2018-12-05 14:54:41
tags:
categories: Python
---

Mac系统导入matplotlib包时，报错：

```
ImportError: Python is not installed as a framework. The Mac OS X backend will not be able to function correctly if Python is not installed as a framework. See the Python documentation for more information on installing Python as a framework on Mac OS X. Please either reinstall Python as a framework, or try one of the other backends. If you are using (Ana)Conda please install python.app and replace the use of 'python' with 'pythonw'. See 'Working with Matplotlib on OSX' in the Matplotlib FAQ for more information.
```



**解决方法：**

通过pip更新matplotlib:

```bash
pip --upgrade matplotlib
```

- 找到目录`~/.matplotlib`
- 新建文件`~/.matplotlib/matplotlibrc`
- 文件中添加`backend: TKAgg`