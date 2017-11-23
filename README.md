# ThirdCompetition
目标top6

特征1：
用户信息：训练集和测试集不变
order信息：训练集：8月，9月，10月订单次数；三个月消费总金额，三个月优惠后的总金额，总的订单数目
		   测试集：9月，10月，11月订单次数；三个月消费总金额，三个月优惠后的总金额，总的订单数目
click信息：训练集：8月，9月，10月点击次数；三个月点击总次数，三个月点击页面种类次数
           测试集：9月，10月，11月点击次数；三个月点击总次数，三个月点击页面种类次数
loan信息：训练集：8月，9月，10月借款金额（计算分期钱）；
		  测试集：9月，10月，11月借款金额（计算分期钱）；
loanSum信息：训练集：11月的借款金额

本地结果：2.297
线上结果：2.365565

特征2：
用户信息：训练集和测试集不变
order信息：训练集：8月，9月，10月订单次数；三个月消费总金额，三个月优惠后的总金额，总的订单数目
		   测试集：9月，10月，11月订单次数；三个月消费总金额，三个月优惠后的总金额，总的订单数目
click信息：训练集：8月，9月，10月点击次数；三个月点击总次数，三个月点击页面种类次数
           测试集：9月，10月，11月点击次数；三个月点击总次数，三个月点击页面种类次数
loan信息：训练集：8月，9月，10月借款金额（计算分期钱）；
		  测试集：9月，10月，11月借款金额（计算分期钱）；
loanSum信息：训练集：11月的借款金额
其中用户信息中的limit 和 order信息中的月消费金额都是用5x-1计算，loanSum中11月借款金额保持不变

本地结果：1.35
线上结果：1.847417

尝试1：
只对进行过借贷的用户进行预测
线上结果1.96

尝试2：
只对活跃用户进行训练和预测


IDEAS:

    用户每个月使用的限额减当前使用的额度
    用户每个月消费额度的方差
    用户的消费星期
    用户是否最近一个月进行了消费
    用户是否最近一个周进行了消费
    用户是否最近两周进行了消费
    用户是否最近两天进行了消费
    用户是否最近三周进行了消费
    用户是否最近一个月进行了借款
    用户是否最近一个周进行了借款
    用户是否最近两周进行了借款
    用户是否最近两天进行了借款
    用户是否最近三周进行了借款
    用户最近一个月点击商品最大次数

    将8、9、10月每月进行行为的用户剔除，即使该类用户11月进行了消费，该类用户不作为训练集

    用户借款金额占该月消费金额比重
    用户当前实际额度：用户最大借款金额=最近4个月分期情况+未分期情况


    order数据当中有value为空的情况，检查后发现这些空用户只有1个uid=69的用户进行了借款
    将用户年龄进行分段，青年中年，老年等 #分段后未发现明显差异