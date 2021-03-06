---
layout: post
title: "归因对A/B测试的影响"
category: technium
tags: [data]
---
当你的产品中有两个相似的模块，并且它们都会对用户的时间和注意力进行争夺，那么你在做A/B实验的时候可能需要小心了。

比如在一个电商网站的A/B实验中，因为推荐算法改进，实验组用户的点推荐的次数大大增加，点搜索结果的次数降低了，同时总体购买率又没什么变化。

这里有两种可能，一种是通过推荐商品的购买转化确实提升了，说明改进有效，但是因为太有效了，导致搜索购买转化有所下降，两者相互抵消了。另一种是是推荐算法虽然提高了点击率，但确实对购买转化没有任何帮助。

## 购买漏斗归因

这取决于我们怎么归因购买转化这个无法通过A/B实验直接观测的指标。一般是将用户分成两组，只计算那些「点击了商品A的推荐→购买了商品A」用户的转化。然而这种简单的归因方法有两个缺点：

- 如果推荐能够让用户留得更久，用户可能在其他页面产生购买行为，而它显然无法捕捉到对这些用户的影响，因为它只考虑了用户的点击行为，而没有考虑用户的停留
- 如果用户在推荐里点击了商品A，又搜索了A，又在搜索结果中点击了A，然后又在其他地方点击了A，最终购买了A，这种情况带来的转化提升没有得到归因

其次归因后计算指标会让A/B实验成立的假设失效。因为实验时随机分组的对象是所有用户，而分析对象是「流过购买漏斗」的用户，这些用户在这实验分组中实际上不是随机分布的了。

## 实验后归因的Bias

假设我们通过进行一组A/B实验来研究「公民教育」对「投票率」的影响，A组接受公民教育，B组不接受，然后比较它们的投票率，因为分组是随机的，其他因素比如社会经济地位就可以消除。但是一旦我们用实验后变量作条件，比如「对政治不感兴趣」，就会让两个分组不具有相似性：

- A组是尽管接受了教育但对政治不感兴趣的人
- B组是没接受教育但是对政治不感兴趣的人

很可能因为A的这个条件过滤出了那些社会经济地位更低的人，导致A组投票率反而不如B组。

### 参考

1. [The Causal Analysis of Cannibalization in Online Products
](https://codeascraft.com/2020/02/24/the-causal-analysis-of-cannibalization-in-online-products/)
2. [How conditioning on post-treatment variables can ruin
your experiment and what to do about it](https://www.dartmouth.edu/~nyhan/post-treatment-bias.pdf)