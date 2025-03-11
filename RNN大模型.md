# RNN模型

https://www.bilibili.com/video/BV1JP4y117mX?spm_id_from=333.788.videopod.episodes&vd_source=215f846e3fe30e50c96f9484f6039e33

RNN本质上在信息筛选。

在MLP的基础上进行循环。

![image-20250221102930479](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221102930479.png)

## 数学公式

![image-20250221103315526](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221103315526.png)

输入:x1,x2,x3,...,xn,a0

参数（模型）:waa,wax,wya,wyx,ba,by。

输出:y1,y2,y3,...,yn

## 例子

如何让计算机理解？

![image-20250221103642287](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221103642287.png)

词汇数值化（独热编码）

![image-20250221104040536](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221104040536.png)

x赋值,y赋值。分割训练集和测试集。

![image-20250221104222373](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221104222373.png)

字典生成的另一种方式。

![image-20250221104447138](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221104447138.png)

## 不同类型的RNN模型

## 常见的RNN结构

多输入对多输出，维度相同的RNN结构。

![image-20250221105003058](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221105003058.png)

多输入单输出RNN结构。

给出句子识别感情。

![image-20250221105257670](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221105257670.png)

单输入多输出RNN结构。

例如，给出标题生成整篇文章。

![image-20250221105320625](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221105320625.png)

多输入多输出RNN结构。

![image-20250221105526902](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221105526902.png)

## 普通RNN结构缺陷

因为特征提取的时候，权重逐渐下降。

![image-20250221105702556](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221105702556.png)

梯度消失导致难以求得损失函数的最小值。

![image-20250221105850187](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221105850187.png)

## 长短期记忆网络（LSTM）

增加新的记忆细胞结构c_i用来记忆重要信息。

理论上a_i和c_i可以结合成b_i，但是实际上效果不好。

![image-20250221110159602](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221110159602.png)

网络结构:忘记门，更新门，输出门。

![image-20250221110516758](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221110516758.png)

解决问题：保留重要信息；不会出现梯度消失。

![image-20250221110657054](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221110657054.png)

## 双向循环神经网络（BRNN）

![image-20250221111040886](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221111040886.png)

## 深层循环神经网络（DRNN）

多层RNN+MLP(全连接层)。

![image-20250221111252717](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221111252717.png)

# RNN实战

时间窗口思想:利用前几天的数据去预测未来几天的数据。

预测思想:Batch思想，划分批量，随机打乱，防止欠拟合。

![image-20250221111648236](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221111648236.png)

## 提取序列数据和模型建立

![image-20250221112147301](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221112147301.png)

输入参数：samples,time_steps,features。

样本量,时间步长,样本特征维数（需不需要进行独热编码）。

这里100存疑。

![image-20250221112515518](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221112515518.png)

## LSTM自动生成文本

NLP流程。首先先进行数据预处理。

![image-20250221112804655](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221112804655.png)

![image-20250221112929109](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221112929109.png)

关注输入输出的形状和格式。

![image-20250221113131432](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250221113131432.png)