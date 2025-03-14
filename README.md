# Autoticket
大麦网自动抢票工具

讨论QQ群：680269358

## Preliminary
Python 3.6+

## Set up
Firefox Browser (测试版本：v68.0.1.7137)

geckodriver.exe (测试版本：v0.24.0)

pip install selenium

## Basic usage
在config.json中输入相应配置信息，具体说明如下：

{
    
    "sess": [ # 场次优先级列表，如本例中共有三个场次，根据下表，则优先选择1，再选择2，最后选择3；也可以仅设置1个。
        1,
        2,
        3,
    ],
    "price": [ # 票价优先级，如本例中共有三档票价，根据下表，则优先选择1，再选择3；也可以仅设置1个。
        1,
        3
    ],
    "real_name": 2, # 实名者序号，如本例中共有两位实名者，根据序号，选择第二位实名者。
    "nick_name": "<Your nick_name>", # 用户的昵称，用于验证登录是否成功
    "ticket_num": 1, # 购买票数
    "damai_url": "https://www.damai.cn/", # 大麦网官网网址
    "target_url": "https://detail.damai.cn/item.htm?id=599834886497" # 目标购票网址
    
}

![avatar](/picture/1.png)

![avatar](/picture/2.png)

若是首次登录，根据终端输出的提示，依次点击登录、扫码登录，代码将自动保存cookie文件（cookie.pkl）

使用前请将待抢票者的姓名、手机、地址设为默认。

配置完成后执行python Autoticket.py即可。

## Advance usage
最后成功测试运行时间：2019-08-21。

此方法太过于依赖大麦网页面源码的元素的title、Xpath、class name等，若相应的绝对路径寻找不到则代码无法运行。

建议自己先测试一遍，自行修改相应的绝对路径或用更好的定位方法替代。

具体修改方案请参见Wiki。

## Change log

v0.1: 

基本功能实现：

  1）用户登录cookie记录
  
  2）场次、票档自动勾选，优先级设定，自动跳过无票/缺货登记
  
  3）实名者/观演人设定
  
v0.2：

鲁棒性提升：

  1）添加用户昵称，验证登录成功
  
  2）修改提交订单按钮的索引方式，增强适配性
  
v0.3:

增强适配性，添加piao.damai.cn类别网页支持

v0.4:

鲁棒性提升，修改终端输出内容，添加指定购买票数功能（暂未测试第二类网址）
  
## To-do List

1. 适配piao.damai.cn（不成熟）

2. 增加日期选择功能

3. 实名售票适配

4. 指定购买票数（部分完成）

5. 增强场次、票档定位稳定性，避免因刷新过快带来的影响

6. 适配手机APP端

## Ref
本代码修改自Ref 1，2两个Repo。

1. Oliver0047: https://github.com/Oliver0047/Concert_Ticket

2. MakiNaruto: https://github.com/MakiNaruto/Automatic_ticket_purchase

3. JnuMxin: https://github.com/JnuMxin/damaiAuto
