---
{"dg-publish":true,"permalink":"/ccb/"}
---



思考，希望有更好的方式
红色部分：程序评判合理性
1. tp1转tp4，目标：一键转换
	1. 问题
		1. 按钮字体不统一
			1. fnt ttf转换
			2. 描边 转换
		2. 图片不统一：tp1按钮有两种大小不同按钮
		3. 资产不统一：tp1存在单个资产需排查
			1. 金币、主角图片
			2. 除按钮之外较少用的通用资产
	2. 方法
		1. 建立资产规范文档
			1. 美术确定图片效果，包括字体描边 方便程序
			2. 程序确定图片路径
		2. 程序提供插件
			1. 批量替换引用 文字
				1. 用vscode解决 需要再确定
			2. <mark style="background: #FF5582A6;">查找丢失引用</mark> 图片
		3. 难点 <mark style="background: #FFF3A3A6;">按钮批量化更改</mark>
			1. 确定按钮图片，替换
			2. 再确定字体，替换
			3. <mark style="background: #FF5582A6;">再确定描边替换</mark> 描边很难追到并替换
				1. 用jscontroller进行标记
				2. ttf中添加标记
	3. ti1不规范问题解决
		1. 根据文档 一次性更改全部
		2. 从现在起 tp1ccb逐个替换
		3. 以上各有利弊，需要确定
2. 思考 tp1换皮流程优化（抛砖引玉）
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
	- 重名扫描
















！数量代表重要性（使用频率）
- ![Pasted image 20241218155720.png](/img/user/Pic/Pasted%20image%2020241218155720.png)！
	- 可在父文件夹使用，遍历子CCB
- ![Pasted image 20241218155821.png](/img/user/Pic/Pasted%20image%2020241218155821.png)！
	- 会遍历所有文件中ccb，导致速度慢
	- 优化
		- 只遍历当前文件夹，增加速度
		- 是否支持自定义? 选择层级
- ![Pasted image 20241218160328.png](/img/user/Pic/Pasted%20image%2020241218160328.png)！！！
	- 用处很大
	- 优化(已完成)
		- 黑体字不明显，改字体颜色
		- 查找只支持选择路径，建议只支持根目录
			- 速度变化不大
			- 使用频率低
	- 下一步操作：
		- <mark style="background: #FF5582A6;">现有重名文件能否删除？用vscode查找确定</mark>
- ![Pasted image 20241218163705.png](/img/user/Pic/Pasted%20image%2020241218163705.png)！！！！！
	- 查找跨领域 引用图片，精确查找引用位置
- cocosbuilder添加插件
	- https://github.com/cocos2d/CocosBuilder/tree/v3.5.0

























