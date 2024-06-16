## 前言

近几天（2024.4.17）使用 VScode Latex 编辑Latex时，发现反向搜索功能失灵（无法由PDF预览器反向定位到代码位置）。 
经检验，这是 Latex Workshop 插件在 2024.4.15 的更新导致的，旧版本 (9.19.2) 中实现反向搜索功能的代码在新版本 (9.20.0) 中不适用。下面给出两种解决方案：回退至旧版本或修改新版本的json代码。

---

## Solution.1 回退版本

由版本9.20.0回退至版本9.19.2，步骤如下：

<div class='center'> 

|步骤 | 图片 |
| ------ | ------ |
|1.   在扩展页面找到 Latex Workshop，点击右下角齿轮  | ![33cd6ec92499e93db1dfdb7d235dda9f.png](https://i3.mjj.rip/2024/06/16/33cd6ec92499e93db1dfdb7d235dda9f.png)|
| 2. 选择 “安装另一个版本” |![bb3e23d3e28cd91045989217c6f77c17.png](https://i3.mjj.rip/2024/06/16/bb3e23d3e28cd91045989217c6f77c17.png)|
| 3. 选择版本 9.19.2| ![4570abbc3d9583975b90c99409b2dcd6.png](https://i3.mjj.rip/2024/06/16/4570abbc3d9583975b90c99409b2dcd6.png) |
| 4. 下载完成后，点击 “restart” 重启插件，重新打开.tex文件及其PDF预览 |（无图片） |
</div>

即可完成版本回退，反向搜索功能恢复正常。

---
## Solution.2 调整新版 json 文件

>此部分待完善

```c
// to be completed...
```