## 作业说明


**Tasking管道图见task.pdf**


**Tasking任务：**

AllItems: loadAllItems();

AllPromotions: loadAllPromotions();

#1 generateItemsBuy：生成数组ItemsNum，用于记录所点Item的数目

    输入：selectedItems: [string], AllItems;
    
    输出：ItemsNum: [string];
    
#2 generateHeadString：生成菜单Head部分String

    输入：
    
    输出：HeadString: string;
    
#3 generateItemsBuyString：生成所购的所有Item和价格清单String

    输入：ItemsNum, AllItems;
    
    输出：AllItemsBuyString: string;
    
#4 calculateNoDiscount：计算没有任何优惠时的Cost

    输入：ItemsNum, AllItems;
    
    输出：CostWithoutDiscount: number;
    
#5 calculateDiscountWay1：计算第一种优惠方式的价格，即‘满30减6元’

    输入：AllPromotions, CostWithoutDiscount;
    
    输出：CostWithDiscountWay1: number;
    
#6 generateDiscountItems：生成数组DiscountItems，用于记录第二种优惠方式打折的Item

    输入：AllItems, AllPromotions;
    
    输出：DiscountItems: [number];
    
#7 calculateDiscountWay2：计算第二种优惠方式的价格，即‘指定菜品半价’

    输入：ItemsNum, AllItems, AllPromotions;
    
    输出：CostWithDiscountWay2: number;
    
#8 generateDiscount1String：生成使用第一种优惠方式的String

    输入：CostWithoutDiscount, CostWithDiscountWay1, AllPromotions;
    
    输出：Discount1String: string;
    
#9 generateDiscount2String：生成使用第二种优惠方式的String

    输入：CostWithoutDiscount, CostWithDiscountWay2, AllPromotions, AllItems, DiscountItems;
    
    输出：Discount2String: string;
    
#10 generateTailString：生成菜单Tail部分String

    输入：cost: number (CostWithoutDiscount, CostWithDiscountWay1 or CostWithDiscountWay2);
    
    输出：TailString: string;
    
#11 chooseBestDiscount：自动选择最优惠的方式并计算出最终金额，生成最优惠方式的String

    输入：ItemsNum, AllItems, AllPromotions;
    
    输出：BestDiscountString: string;
    
#12 bestCharge

    输入：selectedItems;
    
    输出：resultString: string;



***

## 需求描述

某快餐品牌推出了它独家的外卖应用，用户可以在手机上直接下单。该应用会根据用户选择的菜品(Item)、数量(Count)和优惠方式(Promotion)进行计算，告诉用户需要支付的金额(Charge)。

优惠活动有多种形式。假设用户一次只能使用一种优惠，那么使用哪种优惠省钱最多就会是一个让用户头疼的问题。所以该外卖应用为了方便用户，在用户下单时，会自动选择最优惠的方式并计算出最终金额让用户确认。

我们需要实现一个名为`bestCharge`的函数，它能够接收用户选择的菜品和数量（以特定格式呈现）作为输入，然后返回计算后的汇总信息。

已知：

- 该店的菜品每一个都有一个唯一的id
- 当前的优惠方式有:
  - 满30减6元
  - 指定菜品半价
- 除菜品外没有其它收费（如送餐费、餐盒费等）
- 如果两种优惠方式省钱一样多，则使用前一种优惠方式

输入样例
-------

```
["ITEM0001 x 1", "ITEM0013 x 2", "ITEM0022 x 1"]
```

输出样例
-------

```
============= 订餐明细 =============
黄焖鸡 x 1 = 18元
肉夹馍 x 2 = 12元
凉皮 x 1 = 8元
-----------------------------------
使用优惠:
指定菜品半价(黄焖鸡，凉皮)，省13元
-----------------------------------
总计：25元
===================================
```

使用另一种优惠的样例
------------------

输入：

```
["ITEM0013 x 4", "ITEM0022 x 1"]
```


输出：

```
============= 订餐明细 =============
肉夹馍 x 4 = 24元
凉皮 x 1 = 8元
-----------------------------------
使用优惠:
满30减6元，省6元
-----------------------------------
总计：26元
===================================
```

如果没有优惠可享受
---------------

输入：

```
["ITEM0013 x 4"]
```

输出：

```
============= 订餐明细 =============
肉夹馍 x 4 = 24元
-----------------------------------
总计：24元
===================================
```


## 基础作业

1. 相关代码在`src`目录下
1. 实现`best-charge.js`中的`bestCharge`函数
1. 写代码前先使用tasking整理思路并画出管道图
1. 先写测试再写实现，代码须跟管道图匹配
1. 代码整洁、函数粒度合适、命名有意义


## 作业提示

1. 可使用`loadAllItems()`方法获取全部的菜品
2. 可使用`loadPromotions()`方法获取全部的优惠方式

## 运行测试

### 浏览器

可使用浏览器打开`run-specs.html`文件运行测试
# take-out-food-yth
