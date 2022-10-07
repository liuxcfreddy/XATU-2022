# **XATU-寻迹车2022**
## 此代码是西安工业大学的循迹车的2022年新款代码，相较于之间的代码有功能的更新的与去除。更加符合当前的比赛要求。
本代码为电信科协嵌入式2022年编写,由之前的“循”我改成了“寻”，是因为在本代码中加入了与之前不同的思路，我们无法保证不发生错误，但是可以纠正错误，所以通过数值判断代替条件判断可以增加速度，也可以提高拓展性。


运行环境：keil 5

-*2022-10-07*-
	-更新说明

		1.增加了抬起车辆后停车的功能，方便调试
		2.车辆被拿起后车轮回正
		3.车辆重新放在地上后会开始前进

-*2022-09-25*-
	-更新说明

		1.增加了中心对正调节
		2.优化代码可读性
		3.增加了转向助力（本人发现，转弯时前轮阻力就会增大，更需
		要动力输出，故转弯时会适当增大电机功率，详见参数posx）

-*2022-09-25*-
	-更新说明

		-更新了转向与速度的双重调节，利用编码器进行调节，左低4位
		是电机的转速调节，15档，二进制计数，低权位在左。右高4位
		是舵机转向大小调节，峰值是正负45°，等比例15级调节。（相
		当于如果全部下拉右侧4个，最大叫角度就是45/15=3度）。增
		加了舵机的防抖功能，避免在转向间隙归位的bug.

-*2022-09-21*
	-更新说明

		-更新了PCB图，PCB用于感应板的制作，减轻重复劳动。为
		了节省成本使用两块小板拼接成一个完整的板子，因为是偶
		数，所以拼接完成后有一个感应头是多余的，可以不用管，
		但是这也以为值感应板是非对称安装的，一侧是会多余出来的。

-*2022-09-20*
    -更新说明

		-1.更新了舵机的选择模式，主要是通过对P2^3接口的高低
		更改舵机的矫正方向，无论你的感应板线序如何都没关系，
		调节P2^3的接口电平高低就可以。
		-2.增加了倒车的刹车灯，在P2^1,P2^2接口。
-*2022-09-19*
	-更新说明：

		 -1.优化了路径判断的速度，改为使用switch的选择模式
		  由之前的条件判断改为了数值判断。
		  
		 -2.舵机转向不可调，在程序内定为了30°~150°，如需
		  更改转向角度请计算周期后直接在ctry函数内修改返回
		  的高电平时间，相关知识请自行补充PWM的舵机控制。
		  
		 -3.增加了倒车巡线的功能，在丢失路径后，经过“防抖
		  判断后”车辆会车头回正，倒车两个防抖周期的时间，
		  然后前进一个防抖周期的时间，以此往复直到重新选线
		  后继续前进。
		  
		 -4.程序分为A、B两个版本，主要为了应对感应板的线序
		  可能出现凌乱。
		  
		 -5.对于感应板的判断要求更高，请尽可能校准感应板的
		  基准电压。程序内对于非预定情况的判断是统一回正，
		  所以当你将车悬空时车头是不会动的。只有符合仅一个
		  灯亮时才会有舵机动作。
		  
		 -6.取消了干簧管的启动功能。
		 
		 -7.电机速度的由编码器控制，接通的数量越多，车越慢
		  编码器数值为其对应的二进制码值。（简单理解为推上
		  去的越多车越慢，拉下来的越多车越快，越往右权重越
		  大）
									

