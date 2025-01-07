---
{"dg-publish":true,"permalink":"/CCB_Note/"}
---


思考，希望有更好的方式
红色部分：程序评判合理性
1. tp1转tp4 简单些（批量化操作）
	1. 问题（坑点）
		1. 按钮字体不统一
			1. fnt ttf是否需要转换
			2. 描边/tag转换（分情况）
		2. 图片不统一：tp1有两种大小不同按钮
		3. 资产不统一：tp1存在单个资产需排查
			1. 金币、主角图片
			2. 除按钮之外较少用的通用资产
				1. 批量替换会造成丢失
	2. 方法
		1. 建立资产规范文档，tp1换皮强制按照文档
			1. 美术确定图片效果，包括字体描边 方便程序
			2. 程序确定图片路径
		2. 程序提供插件
			1. 关键词替换，更改文字图片
				1. 替换内容 写死还是自定义？
				2. 用vscode解决 需要再确定？
			2. <mark style="background: #FF5582A6;">查找丢失引用</mark> 图片
		3. 难点 <mark style="background: #FFF3A3A6;">按钮批量化更改</mark>？
			1. 确定按钮图片，替换
			2. ~~再确定字体，替换（如果tp1按钮为ttf）~~
			3. <mark style="background: #FF5582A6;">再确定描边替换</mark> 描边很难追到并替换
				1. 用jscontroller进行标记
				2. ttf中添加标记
	3. tp1旧内容不规范，以下各有利弊，需要思考
		1. 根据文档 一次性更改全部
		2. 现在起 tp1ccb换皮逐个替换

1. 思考 tp1换皮流程优化（抛砖引玉）
	1. 拆包
		1. 文件夹迁移
		2. 图集拆开
		3. 更改图片引用，删除.plist
	2. 修改
		1. 文件夹添加新图
		2. 更改图片引用
		3. 删除未使用图片
			1. <mark style="background: #FFF3A3A6;">程序替换图片，需单独文件夹</mark>
	3. 合包
		1. 打图集
		2. 引用添加.plist
	4. 插件
		1. 图片文件夹：<mark style="background: #FF5582A6;">删除无引用图片</mark>
		2. 引用路径更改：文件 互转 文件夹.plist
		3. 批量更改文件夹名字
- 插件优化
	- 搜索中文名
	- 删除未引用图片
		- 删除图集/文件夹（建议图集）




！数量代表重要性（使用频率）
- ![Pasted image 20250106094509.png](/img/user/Pic/Pasted%20image%2020250106094509.png)
	- 鸡肋：可以复制，不能粘贴，粘贴还是需要开访达，为什么不直接开访达重命名
- ![Pasted image 20250103185123.png](/img/user/Pic/Pasted%20image%2020250103185123.png)
	- 需要分析？
- ![Pasted image 20241218155720.png](/img/user/Pic/Pasted%20image%2020241218155720.png)！
	- 可在父文件夹使用，遍历子CCB!
- ![Pasted image 20250103184620.png](/img/user/Pic/Pasted%20image%2020250103184620.png)
	- 内容迁移
- ![Pasted image 20250103184854.png](/img/user/Pic/Pasted%20image%2020250103184854.png)！！！！！
	- 批量操作
- ![Pasted image 20241218155821.png](/img/user/Pic/Pasted%20image%2020241218155821.png)
	- ![Pasted image 20250103183454.png](/img/user/Pic/Pasted%20image%2020250103183454.png)
	- 会遍历所有文件中ccb，导致速度慢
	- 优化：支持自定义选择层级(1或2层)
- ![Pasted image 20241218160328.png](/img/user/Pic/Pasted%20image%2020241218160328.png)！！！
	- ![Pasted image 20250103183921.png](/img/user/Pic/Pasted%20image%2020250103183921.png)
	- 优化(已完成)
		- 黑体字不明显，改字体颜色
		- 查找只支持选择路径，建议只支持根目录
			- 速度变化不大
			- 使用频率低
	- 图片重名不是问题，重名但内容不同才是问题。
	- 下一步操作：
		- 删除重名文件，需要精准确定，存在旧项目文件
- ![Pasted image 20241218163705.png](/img/user/Pic/Pasted%20image%2020241218163705.png)！！！！！
	- 跨域引用图片
		- 更新版，只支持当前文件，无法检索子文件之间
		- 实现：检索难度会增加多少
	- 丢失引用图片（很好用）
- cocosbuilder添加插件
	- https://github.com/cocos2d/CocosBuilder/tree/v3.5.0

