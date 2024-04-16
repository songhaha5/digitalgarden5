---
{"dg-publish":true,"permalink":"/GameJam/text/"}
---

https://fabulous-kangaroo-0e9a27.netlify.app/gamejam/text/


问题：

程序
1. 游戏场景Scene（一层一个还是一共一个）（关于数据保存）
2. Shader？
	1. ![Pasted image 20240414180348.png](/img/user/pic/Pasted%20image%2020240414180348.png)
	2. npc视线范围
		1. 给个游戏原型？
3.  GIT流程？
	1. 每人建一个分支，然后定时合并到主分支？

策划
1. 汲声钮如何使用？
	1. 举个游戏案例？
		1. 如何确定远方在对话（使用汲声钮的前提）
		2. 怎么确定窃听远方对话（汲声钮如何使用）
2. <mark style="background: #FF5582A6;">有周目（名片）功能？</mark>：需要存储那些信息？
3. 什么情况下可以点击物品
	1. 信号：
		1. 主角面向物品（此时物品高亮显示）
		2. 并且在一定距离
	2. 只在距离内
4. 玩家有那些状态？
	1. 是否伪装
	2. 血量？
5. 安全、非安全区域的作用明显吗？
6. 需要UI界面吗？
	1. 设置界面![Pasted image 20240416210223.png](/img/user/pic/Pasted%20image%2020240416210223.png)
	2. 奖券界面![Pasted image 20240416205400.png](/img/user/pic/Pasted%20image%2020240416205400.png)
	3. 信息提示界面![Pasted image 20240416202631.png](/img/user/pic/Pasted%20image%2020240416202631.png)
	4. 需要给我实例
7. <mark style="background: #FF5582A6;">什么时候需要回档（死亡）？？？？？</mark>
		1. 时间到时
		2. 血量没有
		3. 对话强制
		4. 警备员发现
8. 场景氛围（打光）？


关于分工的思考
- 计时
	- 倒计时限制
	- 游戏正常时间
	- 暂停功能
	- 时间跳跃
- 数据保存
	- ~~确定何时回退~~
	- 确定保存那些数据
- npc行为
	- 探测玩家（回档），
	- 移动（在一定范围内巡逻/站立）
	- 接收范围（听觉、视觉）
	- 定时离开（按照时间系统）
	- <mark style="background: #FFF3A3A6;">死亡？</mark>怎么死?
- 人物行为
	- 状态：血量、是否伪装、跑步/潜行、死亡（回档）
	- 传播范围
	- 移动
	- 物品交互
		- 播放动画：门，抽屉，密码锁、货架，
		- 弹出界面：信息物品，提示信息
		- 更改设置：灯
	- npc交互
		- 对话：普通npc、需要物品的npc
		- <mark style="background: #FFF3A3A6;">击打？</mark>
	- 按键设置
- 摄像机切换（是第一人称还是固定视角？）
	- 移动到密码锁、抽屉特写等
	- 房间切换
	- 移动到两个npc对话场景
	- 楼层切换
- UI界面
	- 对话（回档）
	- 信息物品
	- 背包物品
	- 提示界面？
	- 玩家界面
	- 思维阁
	- 主界面
	- 设置界面
- 背包
- 解密小游戏设置（单独一个场景？）
	- 密码锁
	- 保险箱
- 物品动画
	- 密码锁按钮按下、门打开、抽屉打开
	- 场景退出、进入
- shader：
	- 物品
	- npc探测范围
- 地图区域设置（安全区）？？？
![动画.gif](/img/user/pic/%E5%8A%A8%E7%94%BB.gif)
1. 
	1. ![Pasted image 20240414175507.png](/img/user/pic/Pasted%20image%2020240414175507.png)
	2. 这个功能：负责场景内物品/NPC互动的老师，调用2次UI对话（没物品时调用1对话，有物品时调用2对话）




我的
1. 这个功能
	1. ![Pasted image 20240413214501.png](/img/user/pic/Pasted%20image%2020240413214501.png)
	2. 在需要原excel文案文件基础上更改（我感觉偏后期）
2. 我想 与npc对话后，将对话界面销毁，使用时再创建，不提供记录功能
	1. 可以与npc重复对话，重复记录？
	2. 有很多细节问题，我感觉我hold不住
		1. 随着是否对话，ui界面动态调整
		2. 对话分支按钮，只能点击一次（记录一次）
		3. ···
3. 基础文本信息（类似海报）放入背包吗？
	1. 如果放，
		1. 什么时候放，没有玩家选择按钮
			1. ![Pasted image 20240414174659.png](/img/user/pic/Pasted%20image%2020240414174659.png)
4. 需要地图界面吗？
	1. ![Pasted image 20240414190516.png](/img/user/pic/Pasted%20image%2020240414190516.png)

```C# fold file:如何调用UI界面
//调用物品UI界面
UIManager.Instance.OpenPanel(UIConst.ItemPanel,DetailName);
//UIConst.ItemPanel / UIConst.PackageItemPanel，界面不同
//ItemPanel是文本物体界面
//PackageItemPanel是道具界面
//DetailName：物品具体名字
```
``
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
# 略
## 与物品交互（信号）
- UI
	- 玩家界面
	- 物品交互
	- 对话
	- 初始界面
		- 播放视频，场景跳转
	- ~~攻击~~
- 人物点击交互事件
	- 输入图片索引(省资源，但麻烦)
	- 创建多个panel，输入指定panel（费资源，但容易）

### 下面是重点
点击--移动--附近有东西
物品交互方式（信号）
- 用对话框显示（提示玩家）信息
{ #1w5qmu}

	- ![Pasted image 20240409150406.png](/img/user/pic/Pasted%20image%2020240409150406.png)
- 弹出<mark style="background: #FFB86CA6;">物品特写</mark>详细UI
{ #360g5y}

	- ![Pasted image 20240409151327.png](/img/user/pic/Pasted%20image%2020240409151327.png)
	- ![Pasted image 20240409151319.png](/img/user/pic/Pasted%20image%2020240409151319.png)
- 弹出<mark style="background: #FFB86CA6;">场景特写（该区域物品较多）</mark>，再点击物品（图片+动画/摄像机）
	- ![Pasted image 20240409142348.png](/img/user/pic/Pasted%20image%2020240409142348.png)
- 可交互物品（放入背包后消失）
{ #nxrkz3}

	- 用对话框显示信息
	- ![Pasted image 20240409142532.png](/img/user/pic/Pasted%20image%2020240409142532.png)
- 移动摄像机物品，且用对话框显示信息
{ #clcglm}

	- 进入，右击退出（动画逆播放）![4月9日.gif](/img/user/pic/4%E6%9C%889%E6%97%A5.gif)
	- ![Pasted image 20240409144752.png](/img/user/pic/Pasted%20image%2020240409144752.png)
	- ![抽屉动画.gif](/img/user/pic/%E6%8A%BD%E5%B1%89%E5%8A%A8%E7%94%BB.gif)
- 密码锁（单纯鼠标点击，2D UI动画（鼠标按下））
	- 如何引导玩家
	- ![Pasted image 20240416161043.png](/img/user/pic/Pasted%20image%2020240416161043.png)确认错误红点，正确绿点，旋转按钮，进入
	- ![密码动画.gif](/img/user/pic/%E5%AF%86%E7%A0%81%E5%8A%A8%E7%94%BB.gif)

确定游玩流程，以此<mark style="background: #FFB86CA6;">具体确定道具</mark>互动效果
综上，将游戏内交互物品分类（按照以下特点），来确定UI展现方式
- 需要经历几次点击
	- 直接点击互动
	- 二次点击：点击进入场景特写，再点击互动
- 是否 放入背包（可交互） [[GameJam/text#^nxrkz3\|text#^nxrkz3]]
- 信息呈现方式
	- [[GameJam/text#^clcglm\|text#^clcglm]] 对话框特写，信息丰富
	- [[GameJam/text#^360g5y\|text#^360g5y]]  图片特写，信息丰富
	- [[GameJam/text#^1w5qmu\|text#^1w5qmu]] 只用对话框，信息少而精

第一关物品
- ![Pasted image 20240409144545.png](/img/user/pic/Pasted%20image%2020240409144545.png)
	- 公司信息
		- 
	- 海报
		- 
	- 公司杂志
		- 
	- 前台的门
		- 没有钥匙的情况
		- 有钥匙的情况




- 对话较简易
	- ![Pasted image 20240409154117.png](/img/user/pic/Pasted%20image%2020240409154117.png)

玩家界面UI，那些使用键盘，那些使用图标
- 举个例子：如何调取背包
	- 在玩家界面，设置背包点击按钮，弹出背包界面
	- 玩家使用键盘，直接调用背包界面
## 略
## 对话
实现方式
	插件
	- fungus
	- Naninovel
	- Dialogue System for Unity
	- NodeCanvas
	无插件
	- [【Unity教程】剧情对话系统_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1v5411D79x/?spm_id_from=..search-card.all.click&vd_source=136e41d3ef50e23d78600ce2ef114fd3)
	[最终选用](文本导入)


问题：
信号：场景探索为主，玩家对话几乎没有（npc较少）
极乐迪斯科：以对话为主（与物品点击也会对话😂）

- 对话文本量是否庞大?
	- 信号（较少）还是极乐迪斯科（较大）
	- 与npc对话完毕后，对话内容是否销毁，
		- 极乐迪斯科是销毁
		- 但这个提供玩家查阅，所以不销毁，将对话保存下来？
- 思维阁是否对 对话有影响?/<mark style="background: #FF5582A6;">思维阁如何设计</mark>
	- 极乐迪斯科（有）还是norca（没有）
		- 因为思维阁，极乐迪斯科的对话有概率失败
		- norca的思维更像一个新的对话(与自己对话)





### 极乐迪斯科拆解
相关网址
[ZA/UM (zaumstudio.com)](https://zaumstudio.com/2016/05/06/reinventing-the-dialogue)


- 对话不一次性展示完，需要玩家点击再展示
	- ![Pasted image 20240410075149.png](/img/user/pic/Pasted%20image%2020240410075149.png)
- 选择自己的回答，对面回答（单项选择，无法选择所有）
	- ![Pasted image 20240410075311.png](/img/user/pic/Pasted%20image%2020240410075311.png)
	- ![Pasted image 20240410075242.png](/img/user/pic/Pasted%20image%2020240410075242.png)
- ~~出现思维阁？（帮助玩家 探索不同回答）~~
	- ![Pasted image 20240410075634.png](/img/user/pic/Pasted%20image%2020240410075634.png)



## 思维阁
- norca


