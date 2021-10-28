![bc5c7a34fee614e08839b511a5840873.jpg](https://i.loli.net/2020/01/30/fOFvI2o9KXqEkJr.jpg)
# Magisk Module 模板

`这是Magisk模块最基础的结构及说明`
```
Magisk-Modules-Template(20.4+).zip
│
├── META-INF
│   └── com
│       └── google
│           └── android
│               ├── update-binary      <--- 这个文件你可以通过下载 module_installer.sh 得到
│               └── updater-script      <--- 这个文件应仅包含字符串 "#MAGISK"
│
├── customize.sh         <--- 这个文件包含 "SKIPUNZIP=0" 如需很多自定义操作 请把0改为1 
│                                                  customize.sh 由 update-binary 执行(sourced)
├── module.prop          <--- 这个文件是填写模块信息
│
├── post-fs-data.sh        <--- 这个文件可以填写系统启动前想要执行的命令
│
├── service.sh             <--- 这个文件可以填写系统启动后想要执行的命令
│
├── system.prop            <--- 这个文件将被resetprop读取 挂载改变系统build.prop对应值
│
├── ...  /* 模块文件的其余部分 */
│
```
**SKIPUNZIP=0意味着除了重要的文件,其他的文件如果您不需要的话可以删除.**

**这是 [Magisk 官方新模块模板](https://github.com/HANA-CI-Build-Project/magisk-module-template) 您也可以去看看**

**有关模块和存储库的更多信息 请查看 [Magisk 官方文档](https://topjohnwu.github.io/Magisk/guides.html)**

感谢 [Pinkdoge](https://github.com/Pinkdoge) 提供相关内容
