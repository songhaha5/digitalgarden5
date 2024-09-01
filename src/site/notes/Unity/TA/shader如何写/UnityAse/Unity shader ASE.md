---
{"dg-publish":true,"permalink":"/Unity/TA/shader如何写/UnityAse/Unity shader ASE/"}
---

 
# 1 遮罩

## 材质设置
创建文件夹：图片、材质
![Pasted image 20240129141811.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129141811.png)
导入图片（Q群文件）：
![Pasted image 20240129133522.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129133522.png)
材质：创建shader
![Pasted image 20240129133626.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129133626.png)
接入界面：创建节点
![Pasted image 20240129133713.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129133713.png)
快捷键：按住T，再点击鼠标左键使用 
- T：贴图采样（Texture Sample 蓝色节点）
	- 更改名称
	- ![Pasted image 20240129134514.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134514.png)
	- ![Pasted image 20240129134522.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134522.png)
- U：UV采样（Texture Coordinates 橙色节点）
	- 更改uv节点映射
	- ![Pasted image 20240129134411.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134411.png)
	- ![Pasted image 20240129134355.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134355.png)
- 2：向量节点（Vector 绿色节点），控制贴图流动速度
- p：显示图片
- color（记得更改颜色）：鼠标右击输入![Pasted image 20240129134100.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134100.png)找Color【5】
- M：Multiply节点
更改设置
![Pasted image 20240129134227.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134227.png)
- ZwriteMode：off
- BlendRGB：Additive
更改Tags-type-Transparent
![Pasted image 20240129135450.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129135450.png)
右击创建材质
![Pasted image 20240129135617.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129135617.png)



## 项目设置（后处理）
创建空物体，重命名post，并添加组件
Profile初始为空，需点击new
![Pasted image 20240129134844.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134844.png)
更改layer层
![Pasted image 20240129134701.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134701.png)
![Pasted image 20240129134652.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129134652.png)

摄像机添加组件，并更改Layer为post
![Pasted image 20240129135020.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129135020.png)
创建quad，将材质赋予
![Pasted image 20240129135350.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129135350.png)
如果需要面板显示，更改Type
![Pasted image 20240129135735.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129135735.png)



# 2 硬边溶解

利用step（[深入理解unity中的Step节点（ShaderForge） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/342055482)）：
- A$>$B为0
- A$<=$B为1
A为数值，B为噪波。让A变大，开始出现黑色区域，再乘以A通道，让人物部分出现黑色区域（消失效果）。
[[Unity/TA/shader如何写/UnityAse/ASE节点\|ASE节点]]

更改Shader设置
![](/img/user/pic/20240129203210.png)

- ![](/img/user/pic/20240130101025.png)创建节点
	- K：![image.png](/img/user/pic/20240130100835.png)
		- 去掉A通道
		- ![image.png](/img/user/pic/20240130095952.png)
	- ![image.png](/img/user/pic/20240130100849.png)
		- 更改1维变量
		- ![image.png](/img/user/pic/20240130100046.png)



# 3 光边溶解

原理：整体变亮，step后溶解变慢（时间相同时，边缘会比以前大，中间明暗不变（都为1有最大值限制）），大减小，只剩下多出来的边缘。
lerp节点：alpha为1显示B，alpha为0时显示A，为0.5时A与B各显示一半的透明度的混合状态
[[Unity/TA/shader如何写/UnityAse/ASE节点\|ASE节点]]
- 创建节点
	- ![](/img/user/pic/20240130155601.png)
	- 基础设置同上
	- ![image.png](/img/user/pic/20240130101610.png)
		- ![image.png](/img/user/pic/20240130101544.png)
将材质赋予
![image.png](/img/user/pic/20240130155716.png)


# 4 UV扰动
用lerp节点更改UV，让uv运动

更改shader基础设置同上
- Render Queue(渲染对列)
	- Background：1000
	- Geometry：2000
	- Alpha Test：2450
	- Transparent：3000
	- Overlay：4000

- 创建节点
	- ![image.png](/img/user/pic/20240130161357.png)
赋予材质
![image.png](/img/user/pic/20240130161424.png)

# 5 边缘光
新建材质（Fresnel1）
 ![image.png](/img/user/pic/20240131202926.png)
![image.png](/img/user/pic/20240131204553.png)
- 颜色使用HDR
	- ![image.png](/img/user/pic/20240131204633.png)
- 更改Texture Coordinates
	- ![image.png](/img/user/pic/20240131204708.png)
Fresnel基本原理：
- 法线向量 点乘 摄像机向量：
- ![image.png](/img/user/pic/20240131205448.png)
- 使用安全Power，解决溢值问题
	- ![image.png](/img/user/pic/20240131205034.png)
# 6 扰动火焰
根据游戏效果逆推
项目设置
![image.png](/img/user/pic/20240131212234.png)

使用3种noise 不同程度进行扰动
外观排序
- ![](/img/user/pic/20240201210900.png)
- ![image.png](/img/user/pic/20240201211218.png)

节点
![](/img/user/pic/20240201210545.png)

![Pasted image 20240129133626.png](/img/user/Unity/TA/shader%E5%A6%82%E4%BD%95%E5%86%99/UnityAse/One_Image/Pasted%20image%2020240129133626.png)





# 7 URP后处理变体数量
- 新建Urp场景，
	- 更改Shader设置
		- ![image.png](/img/user/pic/20240201211405.png)
		- ![image.png](/img/user/pic/20240201211457.png)
	- 更改后处理设置
		- ![image.png](/img/user/pic/20240201211719.png)
			- 不需要添加层级
			- 
		- ![image.png](/img/user/pic/20240201211807.png)

Shader性能
- 变体数量
- 单个Shader计算量
- 采样贴图的数量
- 数学指令树
- 顶点着色器 是否需要贴图采样

考虑项目大小时，创建Shader，需要注意变体数量，会占用空间（ASE 与 ShaderGraph 差5倍）
- 变体：创建功能（扰动、溶解、遮罩等）时，会出现变体。例如123，出现1，2，3，12，13，123
	- Ase创建Unit shader只有一个变体（1variants included）
		- ![image.png](/img/user/pic/20240201211930.png)
	- ShadreGraph 有5个变体
		- ![image.png](/img/user/pic/20240201212016.png)
# 8 深度渐变（Depth）
可以做海岸边的泡沫

Shader设置
![image.png](/img/user/pic/20240201212634.png)
创建节点
![image.png](/img/user/pic/20240201214317.png)
- 计算距离，根据深度图，相交为0，远处为1，
- 用1- 反过来，变成相交为1，远处为0

碰撞边界不是一条线，而是渐变的线（面）

# 9 软粒子（没有切边） 与  顶点颜色
没有软粒子，相交时会出现切边
创建Shader(VertexColor)
项目设置（先不关深度写入）
![image.png](/img/user/pic/20240201214738.png)

创建粒子材质器
![image.png](/img/user/pic/20240203154105.png)

	深度写入：前面覆盖后面，特效一般为叠加，不需要深度写入
		使用情况：溶解特效，前面溶解，后面没有，会看到背面
		此时关闭深度写入
![image.png](/img/user/pic/20240203154430.png)

粒子发射器发射片，4个顶点基于顶点颜色计算，所以ShaderASE，需要添加顶点着色
![image.png](/img/user/pic/20240203154640.png)

软粒子(用来描述一种效果 不是功能)：解决切边，用深度图（Depth Fade），比较浪费
![image.png](/img/user/pic/20240203154713.png)
制作溶解
![](/img/user/pic/20240203161726.png)
# 10 CustomData与顶点数据流
![image.png](/img/user/pic/20240217163504.png)
![image.png](/img/user/pic/20240227181645.png)
硬边溶解
![image.png](/img/user/pic/20240227181721.png)
添加到particle system（粒子发射器）
![image.png](/img/user/pic/20240227181909.png)


![image.png](/img/user/pic/20240227182210.png)
![image.png](/img/user/pic/20240227182225.png)






# 11 软溶解
# 12 Ramp采样 护盾小案例