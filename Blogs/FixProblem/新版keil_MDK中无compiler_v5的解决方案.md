# 前言

>笔者近期学习STM32时，在STM官网上下载了最新版的keil_MDK软件，新版keil_MDK默认编译器为compiler_v6且不提供compiler_v5。由于v5环境下的代码在v6中无法直接编译（直接编译会存在数十个error），因此考虑下载旧版compiler_v5。

下面给出完整解决方案，并解答部分可能遇到的问题。

---

# Compiler_v5的下载与添加
V5下载链接（提取码1234）：[https://pan.baidu.com/s/1Tjj02vgeguDWmugbPHFh2w](https://pan.baidu.com/s/1Tjj02vgeguDWmugbPHFh2w?pwd=1234) 
下载后解压，并按下列步骤进行：

::: center  
| 步骤 | 图片 |
| ------ | ------ |
| 1. 将解压后的文件夹复制到keil安装目录下的ARM文件夹中（非常不建议复制到其它文件夹，否则可能出错） | ![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/005545092-1.png) |
| 2. 打开keil5，点击 "File Extensions" | ![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/005846263-1.png) |
| 3. 依次点击 "Folders/Extensions" --> 省略号    |![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/010037939-1.png) |
| 4. 点击 "Add anotherARM" | ![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/010051557-1.png) |
| 5. 选择刚刚复制过来的文件夹AMRCC | ![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/010146542-1.png) |
| 6. 看到新增了一条信息，点击下方close|![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/010231276-1.png)|
|7. 点击OK退出此界面（注意：这里不能直接关闭，否则添加无效）|![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/010432463-1.png)|
|8. 点击魔术棒"options for target"|![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/010547434-1.png)|
|9. 点击 "target" --> "下三角"|![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/010642958-1.png)|
|10. 选择 "V5.06 update 6 (build 750)"|![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/012048244-1.png)|
|11. 点击下方"OK"退出界面|![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/010853639-1.png)|
:::


即可完成compiler_v5的相关配置，在可执行project中点击编译，可以看到 "0 error, 0 warning"。
![image#500px #390px](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/095021199-1.png)
project的创建与初始化可以参考视频（3分16秒~11分22秒）：[https://www.bilibili.com/video/BV1th411z7sn](https://www.bilibili.com/video/BV1th411z7sn?p=4&vd_source=cc1a55267bfd4977e53958893f16a4a9) 

---
# 常见问题1：编译报错 "Error: CreateProcess failed"
>编译后报错 "Error: CreateProcess failed ......"

![image#303px #203px](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/012726033-1.png)

一个可能的原因是在上面的步骤10不小心选择错误，错选为了"use defult compiler version 5"，另一个可能的原因是keil版本不同fromelf.exe的位置不一样导致路径冲突。
对于第一种原因：在上面步骤10中重新选择 "V5.06 update 6 (build 750)"
对于第二种原因：参考文章 [https://blog.csdn.net/weixin_38748999/article/details/116012799](https://blog.csdn.net/weixin_38748999/article/details/116012799) 

# 常见问题2：Target栏界面空白
>魔术棒"options for target"中，Target栏绝大部分选项消失，无法选择编译器版本等。

::: center  
| Target栏界面空白 | 正常的Target |
| ------ | ------ |
| ![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/013025299-1.png) | ![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/095510200-1.png) |
:::

可能是因为AMRCC文件夹路径错误。
解决方法：检查ARMCC文件夹路径是否正确，上上级文件夹是否的确为keil软件根目录，且上级文件夹为ARM

---

# 参考文章

>本文参考的资料，提及的文章内容附在此处以供查阅

[KeilMDK V5编译器的安装：https://blog.csdn.net/weixin_42727214/article/details/132378555](https://blog.csdn.net/weixin_42727214/article/details/132378555) 