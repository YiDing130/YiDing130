# 前言

近几天（2024.4.17）使用 VScode Latex 编辑Latex时，发现反向搜索功能失灵（无法由PDF预览器反向定位到代码位置）。 
经检验，这是 Latex Workshop 插件在 2024.4.15 的更新导致的，旧版本 (9.19.2) 中实现反向搜索功能的代码在新版本 (9.20.0) 中不适用。下面给出两种解决方案：回退至旧版本或修改新版本的json代码。

---

# Solution.1 回退版本

由版本9.20.0回退至版本9.19.2，步骤如下：

::: center  
|步骤 | 图片 |
| ------ | ------ |
|1.   在扩展页面找到 Latex Workshop，点击右下角齿轮  | ![image](/static/uploads/2024/4/21/c2aaf5738e62f79a6c8a105b1e70c6a4.png) |
| 2. 选择 “安装另一个版本” |![image](https://gitee.com/zongminz_admin/images/raw/master/pic/20240424/005113147-1.png)|
| 3. 选择版本 9.19.2| ![image](/static/uploads/2024/4/21/7b4358c5898d390a0f1af23926a3e156.png) |
| 4. 下载完成后，点击 “restart” 重启插件，重新打开.tex文件及其PDF预览 |（无图片） |
:::

即可完成版本回退，反向搜索功能恢复正常。

---
# Solution.2 调整新版 json 代码

>此部分待完善

```c
// to be completed...
```