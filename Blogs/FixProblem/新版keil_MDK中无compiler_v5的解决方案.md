## 前言

>笔者近期学习STM32时，在STM官网上下载了最新版的keil_MDK软件，新版keil_MDK默认编译器为compiler_v6且不提供compiler_v5。由于v5环境下的代码在v6中无法直接编译（直接编译会存在数十个error），因此考虑下载旧版compiler_v5。

下面给出完整解决方案，并解答部分可能遇到的问题。

---

## 导入Compiler_V5
V5下载链接（提取码1234）：[https://pan.baidu.com/s/1Tjj02vgeguDWmugbPHFh2w](https://pan.baidu.com/s/1Tjj02vgeguDWmugbPHFh2w?pwd=1234) 
下载后解压，并按下列步骤进行：

<div class='center'>

| 步骤 | 图片 |
| ------ | ------ |
| 1. 将解压后的文件夹复制到keil安装目录下的ARM文件夹中（不建议复制到其它文件夹，否则可能出错） | ![ff509f7a822d7c10cf871dc2938c3aba.png](https://i3.mjj.rip/2024/06/16/ff509f7a822d7c10cf871dc2938c3aba.png) |
| 2. 打开keil5，点击 "File Extensions" | ![2bbb535f9bd3537633a734286bdf6b62.png](https://i3.mjj.rip/2024/06/16/2bbb535f9bd3537633a734286bdf6b62.png) |
| 3. 依次点击 "Folders/Extensions" --> 省略号    |![c5e8b6134d0b6838664ead5676b64cb6.png](https://i3.mjj.rip/2024/06/16/c5e8b6134d0b6838664ead5676b64cb6.png) |
| 4. 点击 "Add anotherARM" | ![3e903fe7d82fba28fe3d1a87059be417.png](https://i3.mjj.rip/2024/06/16/3e903fe7d82fba28fe3d1a87059be417.png) |
| 5. 选择刚刚复制过来的文件夹AMRCC | ![11778bd28373779dd9bee89cde905fd4.png](https://i3.mjj.rip/2024/06/16/11778bd28373779dd9bee89cde905fd4.png) |
| 6. 看到新增了一条信息，点击下方close|![e9c1f2adf74a4e446232bd2d75a4bfe6.png](https://i3.mjj.rip/2024/06/16/e9c1f2adf74a4e446232bd2d75a4bfe6.png)|
|7. 点击OK退出此界面（注意：这里不能直接关闭，否则添加无效）|![4df1c4a7d0282e263bc8dcd77afa21ca.png](https://i3.mjj.rip/2024/06/16/4df1c4a7d0282e263bc8dcd77afa21ca.png)|
|8. 点击魔术棒"options for target"|![6812943a739b87d4ce6112a62cd44c92.png](https://i3.mjj.rip/2024/06/16/6812943a739b87d4ce6112a62cd44c92.png)|
|9. 点击 "target" --> "展开"|![f1be0f679fbad7e3d4c2331ca23b936b.png](https://i3.mjj.rip/2024/06/16/f1be0f679fbad7e3d4c2331ca23b936b.png)|
|10. 选择 "V5.06 update 6 (build 750)"|![9a2678a87c3e3c3348879e0dbb56de82.png](https://i3.mjj.rip/2024/06/16/9a2678a87c3e3c3348879e0dbb56de82.png)|
|11. 点击下方"OK"退出界面|![4c8a9f0fcc2df659d0a455fc30dd1ace.png](https://i3.mjj.rip/2024/06/16/4c8a9f0fcc2df659d0a455fc30dd1ace.png)|
</div>


即可完成compiler_v5的相关配置，在可执行project中点击编译，可以看到 "0 error, 0 warning"。
![bfe8739b3d2fa1db6c21ccb7ea85838e.png](https://i3.mjj.rip/2024/06/16/bfe8739b3d2fa1db6c21ccb7ea85838e.png)
project的创建与初始化可以参考视频（3分16秒~11分22秒）：[https://www.bilibili.com/video/BV1th411z7sn](https://www.bilibili.com/video/BV1th411z7sn?p=4&vd_source=cc1a55267bfd4977e53958893f16a4a9) 

---
## 常见问题

### 1：编译报错 "Error: CreateProcess failed"

编译后报错 "Error: CreateProcess failed ......"

![3c9771edf5e926768ae11daaa4538cd0.png](https://i3.mjj.rip/2024/06/16/3c9771edf5e926768ae11daaa4538cd0.png)

一个可能的原因是在上面的步骤10不小心选择错误，错选为了"use defult compiler version 5"，另一个可能的原因是keil版本不同fromelf.exe的位置不一样导致路径冲突。
对于第一种原因：在上面步骤10中重新选择 "V5.06 update 6 (build 750)"
对于第二种原因：参考文章 [https://blog.csdn.net/weixin_38748999/article/details/116012799](https://blog.csdn.net/weixin_38748999/article/details/116012799) 

### 2：Target栏界面空白
魔术棒"options for target"中，Target栏绝大部分选项消失，无法选择编译器版本等。

<div class='center'>  

| Target栏界面空白 | 正常的Target |
| ------ | ------ |
| ![0607a9c266030e9bd1bdc8c23f1811f0.png](https://i3.mjj.rip/2024/06/16/0607a9c266030e9bd1bdc8c23f1811f0.png)|![ba8cb368d360cd0ad3b15a1b4abdda2f.png](https://i3.mjj.rip/2024/06/16/ba8cb368d360cd0ad3b15a1b4abdda2f.png) |
</div>

可能是因为AMRCC文件夹路径错误。
解决方法：检查ARMCC文件夹路径是否正确，上上级文件夹是否的确为keil软件根目录，且上级文件夹为ARM


## 参考文章

[KeilMDK V5编译器的安装：https://blog.csdn.net/weixin_42727214/article/details/132378555](https://blog.csdn.net/weixin_42727214/article/details/132378555) 