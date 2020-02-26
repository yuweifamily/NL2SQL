# NL2SQL
Natural Language to SQL( 以下简称NL2SQL)，是将自然语言（NL）转换成标准SQL语言的过程，属于自然语言处理-语义分析（Semantic Parsing）领域中的子任务。

它的目的可以简单概括为：**“打破人与结构化数据之间的壁垒”**，即用户可以通过文本描述完成对复杂数据库的查询工作，得到想要的结果。

## NL2SQL 简单示例

表_1-1

|  代码  |  名称  |    上市地点    | 收盘价 | 周涨跌幅 | 月涨跌幅 |
| :----: | :----: | :------------: | :----: | :------: | :------: |
| SINA.O |  新浪  |    纳斯达克    | 58.93  |  -4.52   |  8.791   |
| BITA.N |  易车  | 纽约证券交易所 | 18.11  |  -4.78   | -11.742  |
| JRJC.O | 金融界 |    纳斯达克    |  1.09  |  -9.17   |  2.834   |
| SFUN.N |  淘屏  |    纳斯达克    |  1.09  |  -9.17   |  2.834   |
| SFUN.N | 搜房网 | 纽约证券交易所 |  1.71  |  -9.52   |  28.575  |
| RENN.N | 人人网 | 纽约证券交易所 |  1.61  |  -9.55   |  14.18   |

Query：新浪和人人网的周涨跌幅分别是多少？

SQL：    **SELECT** 周涨跌幅 **FROM** 表_1-1  **WHERE** 名称=‘新浪’ **OR** 名称=‘人人网’

用户输入一句普通文本，模型将其转换为 SQL，查询数据库得到结果："-4.52, -9.55"

当然实际场景或业务中，需要查询的内容可能更加复杂。

## 已有数据集

现有NL2SQL数据集List：

#### 1.WikiSQL

[WikiSQL 标注数据集](https://github.com/salesforce/WikiSQL)

```
WikiSQL是一个大型的语义解析数据集，由80,654个自然语句表述和24,241张表格的sql标注构成。
WikiSQL中的每一个问句的查询范围仅限于同一张表，不包含排序、分组、子查询等复杂操作。
虽然数据规模大，SQL语法却非常简单；适合做NL2SQL任务入门。
```

#### 2.Spider

[Spider](https://yale-lily.github.io/spider)

```
耶鲁大学在2018年新提出的一个较大规模的NL2SQL数据集。
该数据集包含了10,181条自然语言问句、分布在200个独立数据库中的5,693条SQL，内容覆盖了138个不同的领域。
涉及的SQL语法最全面，是目前难度最大的NL2SQL数据集。
```

#### 3.WikitableQuestion

[3.WikitableQuestion](https://arxiv.org/pdf/1508.00305.pdf)

```
WikitableQuestion是斯坦福自然语言处理小组的工作。数据集中每个问题都带有来自Wikipedia的表格。给定问题和表格，任务是根据表格回答问题。
数据集包含来自各种主题的2,108个表和具有不同复杂性的22,033个问题
```

#### 4.阿里天池NL2SQL中文挑战赛

[NL2SQL天池大赛](https://tianchi.aliyun.com/competition/entrance/231716/information)

```
公开的NL2SQL数据集中唯一一份高质量的中文数据集，由比赛主办方追一科技提供。数据集使用金融以及通用领域的表格数据作为数据源，提供在此基础上人工标注的自然语言和SQL语句的匹配对。
一共包含49,867条有标注的训练集数据，10,000条无标注数据作为测试集
```

## 解决方案

#### 1.Spider榜单开源模型

（1）[EditSQL：关注跨域上下文依赖的文本到sql生成任务](https://github.com/ryanzhumich/sparc_atis_pytorch)

（2）[IRNet：用于复杂和跨域文本到sql的神经网络方法](https://github.com/microsoft/IRNet)

#### 2.NL2SQL中文挑战赛方案

（1）[追一科技-baseline](https://github.com/ZhuiyiTechnology/nl2sql_baseline?spm=5176.12281978.0.0.479040bfhD0GVo)

（2）[基于Bert的NL2SQL模型：一个简明的Baseline](https://kexue.fm/archives/6771)

（3）[阿里天池首届中文NL2SQL挑战赛复赛第6名开源](https://tianchi.aliyun.com/competition/entrance/231716/introduction)

## 参考论文

```
1.《Editing-Based SQL Query Generation for Cross-Domain Context-Dependent Questions》
EditSQL 模型

2.《Towards Complex Text-to-SQL in Cross-Domain Database with Intermediate Representation》
IRNet 模型，Spider 数据集目前已经开源的 SOTA 模型

3.《X-SQL: reinforce schema representation with context》
X-SQL 模型

4.《Memory Augmented Policy Optimization for Program Synthesis and Semantic Parsing》
MAPO：用于程序综合和语义分析的内存增强策略优化

5.《SEQ2SQL- GENERATING STRUCTURED QUERIES FROM NATURAL LANGUAGE USING REINFORCEMENT LEARNING》
SEQ2SQL：使用强化学习从自然语言生成结构化查询
```

详见 **paper** 目录

## 参考资料

1.[NL2SQL 这个领域研究进展如何](https://www.zhihu.com/question/323109035/answer/683975497)

2.[首届中文NL2SQL挑战赛冠军比赛攻略_不上90不改名字](https://github.com/nudtnlp/tianchi-nl2sql-top1)

3.[CSpider：Spider 数据集中文版](https://taolusi.github.io/CSpider-explorer/)

