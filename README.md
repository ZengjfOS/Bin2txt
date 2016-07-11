# Bin2txt
参考NXP论坛中bin2txt.pyw源代码，修改其中的两处错误，功能是将二进制文件转成C头文件，主要为了处理U-boot Logo文件。

## 参考源码
[bin2txt.pyw](https://community.nxp.com/docs/DOC-93833)

## 如下两处错误修改

```Python
    if 2 == argc:
    if argv_list[1].startswith('-'):
        # fetch the option
        # option = argv_list[0][1:]     # <-- error 1
        # 源代码中这一部分错了，需要将argv_list[0][1:]改成argv_list[1][1:]
        option = argv_list[1][1:]
        if 'version' == option:
            Print_Version()
        elif 'help' == option:
            Print_Help()
        else:
            print 'Unknown', option, 'option!'
        # 添加这条语句，这里结束了后续没必要运行了。
        return                          # <-- error 2
```
