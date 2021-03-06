- 传统社会力模型的实现
	- 已完成
		- 行人自驱动力的计算
		- 行人之间相互作用力的计算
		- 行人与墙相互作用力的计算
		- 对每个行人合力的计算
		- 经过每个仿真时间（dt = 0.5）对行人的运动状态（速度，位置）进行更新
		- 使用A*算法对行人目标方向进行规划

	- GUI合作内容
		- 生成一个背景地图，显示墙和障碍物的位置
		- 背景地图具有形如(x,y)的二维坐标
		- 为每一个人生成一个圆形
		- 人的位置由ai.pos二维向量唯一确定。
		- 可以显示人的位置的变化过程

	- 运行方式&数据检查
		- 运行social_force.py
		- 数据输出部分分别表示对每一个行人的加速度，速度和位置
		- 加速度和速度为二维向量，位置是一个坐标
		- 可以在social_force.py的全局变量定义（第11-14行修改人的数量，场地大小和时间推进次数）

	- 某一次的运行结果及其说明
		- 结果
		加速度：  [-1.13137085 -1.91103791] 当前实际速度： [-0.56568542 -0.95551895] 位置： [7.39691898 3.69155596]
		加速度：  [-1.13137085 -1.13137085] 当前实际速度： [-0.56568542 -0.56568542] 位置： [8.11951482 7.31243001]
		加速度：  [-1.59999360e+00 -1.87610804e-04] 当前实际速度： [-7.99996798e-01 -9.38054022e-05] 位置： [5.81870692 1.26720217]
		加速度：  [-5.30097051e-06 -1.60000000e+00] 当前实际速度： [-2.65048526e-06 -8.00000000e-01] 位置： [1.55233362 7.86782387]
		加速度：  [-1.60007730e+00 -2.44889534e-05] 当前实际速度： [-8.00038651e-01 -1.22444767e-05] 位置： [3.987313   1.41022269]
		====================
		加速度：  [ 5.82477372e-12 -1.46626010e+01] 当前实际速度： [-0.56568542 -8.28681944] 位置： [7.11407627 1.38097136]
		加速度：  [ 2.23347781e-29 -3.40518589e-19] 当前实际速度： [-0.56568542 -0.56568542] 位置： [7.83667211 7.0295873 ]
		加速度：  [-0.00523844 -0.00046013] 当前实际速度： [-8.02616018e-01 -3.23872621e-04] 位置： [5.41805371 1.26709775]
		加速度：  [-4.39068825e-11 -3.03795839e-21] 当前实际速度： [-2.65050721e-06 -8.00000000e-01] 位置： [1.55233229 7.46782387]
		加速度：  [-8.60528078e-04  8.70380762e-05] 当前实际速度： [-8.00468915e-01  3.12745614e-05] 位置： [3.58718611 1.41022745]
		====================
		[[1. 1. 1. 1. 1. 0. 1. 1. 1. 1.]
		 [1. 0. 0. 0. 0. 0. 0. 0. 0. 1.]
		 [1. 0. 0. 0. 0. 0. 0. 0. 0. 1.]
		 [1. 0. 0. 0. 0. 0. 0. 0. 0. 1.]
		 [1. 0. 0. 0. 0. 0. 0. 0. 0. 1.]
		 [1. 0. 0. 0. 0. 0. 0. 0. 0. 1.]
		 [1. 0. 0. 0. 0. 0. 0. 0. 0. 1.]
		 [1. 0. 0. 0. 0. 0. 0. 0. 0. 1.]
		 [1. 0. 0. 0. 0. 0. 0. 0. 0. 1.]
		 [1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]]

		***Repl Closed***

		- 说明
		每一步仿真的时间间隔为0.5s，共仿真两步，每一步用===分割
		最后输出了一个地图方阵，其中1为墙。

	- 关于墙在social_force.py中的说明
		- 目前实现的效果尚不完善，墙的定义分成两段
			- 一：用直线定义墙line 42 - 54,主要用于计算墙给人的力
			- 二：用矩阵存储障碍物（包括墙），主要用于A*算法规划人的前进方向。
		- 后续修改方向
			完全用0-1矩阵存储障碍物