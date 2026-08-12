[README.md](https://github.com/user-attachments/files/30985501/README.md)
# 澳大利亚零售销售绩效仪表板

这是我的第一个 Tableau 求职作品集项目。项目使用模拟零售数据，构建交互式仪表板，从时间、产品类别、客户群体和澳大利亚各州等维度分析销售表现。

> **数据说明：** 本项目使用为 Tableau 与商业分析练习而创建的模拟数据集，不代表真实企业数据。

## 项目概述

该仪表板帮助业务决策者快速了解整体经营表现，并回答以下问题：

1. 整体销售额和利润表现如何？
2. 哪些产品类别和州贡献了最多销售额？
3. 哪些客户具有最高的销售贡献？
4. 不同年份、月份和客户群体的表现有何变化？

## 仪表板预览

> 仪表板截图尚未上传。上传至 `images/dashboard-preview.png` 后将在此处展示。

## 数据集与数据模型

数据模型由四张关系表组成：

| 数据表 | 行数 | 用途 | 关键字段 |
|---|---:|---|---|
| Orders | 350 | 订单与销售明细 | Order ID |
| Customers | 90 | 客户信息与客户群体 | Customer ID |
| Products | 36 | 产品与品类信息 | Product ID |
| Regions | 8 | 澳大利亚州及地区信息 | State |

### 表关系

- `Orders.Customer ID` → `Customers.Customer ID`
- `Orders.Product ID` → `Products.Product ID`
- `Customers.State` → `Regions.State`

表之间使用客户 ID 和产品 ID 建立关系，而不是使用名称，因为名称不一定唯一。

## 核心指标

| KPI | 结果 |
|---|---:|
| 总销售额 | A$167,314 |
| 总利润 | A$58,149 |
| 整体利润率 | 34.8% |
| 订单量 | 350 |
| 活跃客户数 | 86 |

### Tableau 计算字段

```tableau
// Profit Margin（利润率）
SUM([Profit]) / SUM([Sales])
```

```tableau
// Total Orders（订单量）
COUNTD([Order ID])
```

```tableau
// Active Customers（活跃客户数）
COUNTD([Customer ID])
```

`Active Customers` 使用 Orders 表中的 Customer ID，只统计至少产生过一笔订单的客户。

## 仪表板组成

- **KPI Summary：** 展示销售额、利润、订单量和活跃客户数
- **Monthly Sales Trend：** 展示 2024–2025 年月度销售趋势
- **Category Performance：** 对比各产品类别的销售额、利润和利润率
- **Sales by State：** 使用地图展示澳大利亚各州销售额
- **Top 10 Customers：** 展示销售额最高的十位客户
- **Interactive Filters：** 支持按年份、月份和客户群体筛选

## 核心业务洞察

### 1. Technology 是主要收入来源

Technology 销售额为 **A$107,623**，占总销售额的 **64.3%**，利润率为 **34.5%**。

### 2. Furniture 的盈利效率最高

Furniture 销售额为 **A$46,954**，利润率达到 **36.8%**，是三个品类中最高的。虽然销售规模低于 Technology，但每澳元销售额带来的利润更高。

### 3. Office Supplies 表现最弱

Office Supplies 仅贡献总销售额的 **7.6%**，利润率为 **29.5%**，也是所有品类中最低的。

### 4. 销售额集中在澳大利亚东部州

NSW、QLD 和 VIC 合计贡献约 **73%** 的总销售额。其中 NSW 是最大市场，销售额为 **A$49,511**。

### 5. 销售增长快于利润增长

2024 至 2025 年：

- 销售额增长 **12.0%**
- 利润增长 **4.3%**
- 利润率从 **36.1%** 下降至 **33.6%**

业务规模有所扩大，但利润增长没有跟上销售增长，说明盈利效率出现下降。

### 6. 销售额依赖少数高价值客户

销售额最高的十位客户贡献了总销售额的 **44.6%**。其中 Leo Thomas 和 Chloe Smith 两位客户合计贡献约 **19.9%**，存在一定客户集中风险。

## 业务建议

1. 在保持高利润率的前提下扩大 Furniture 品类。
2. 检查 Office Supplies 的定价、折扣和产品组合。
3. 分析 2025 年利润率下降是否由成本、折扣或品类结构变化导致。
4. 为高价值客户制定留存方案，同时降低对少数客户的依赖。
5. 评估 NSW、QLD 和 VIC 的成功策略能否复制到其他州。

## 展示的 Tableau 技能

- 多表 Relationship 数据建模
- 数据验证与关系检查
- 计算字段与去重计数（COUNTD）
- 离散日期与连续日期处理
- Top N 筛选与上下文筛选器
- 地理角色与填充地图
- 使用颜色、标签和工具提示进行视觉编码
- 年、月和客户群体交互筛选
- KPI 卡片与 Dashboard 布局设计

## 重要设计思路

- **Rows 和 Columns** 决定视图结构、坐标轴和标记位置。
- **Marks Card** 控制颜色、大小、标签和工具提示等视觉表现。
- 连续度量使用渐变色表示数值大小。
- 离散维度使用不同颜色区分类别。
- Tooltips 用于展示精确数值，避免仪表板信息过度拥挤。
- 客户排名使用 Customer ID，而不是 Customer Name，防止同名客户被错误合并。

## 使用工具

- Tableau Public / Tableau Desktop
- Microsoft Excel
- GitHub

## 计划中的项目文件结构

> 当前仓库暂时只包含 `README.md`，其余项目文件将在后续补充。

```text
├── README.md
├── data/
│   └── Tableau_BA_Retail_Data_Sources.xlsx
├── dashboard/
│   └── Australian_Retail_Sales_Dashboard.twbx
└── images/
    └── dashboard-preview.png
```

## 作者说明

本项目是我的第一个 Tableau 商业分析作品集项目，用于系统学习 Tableau 核心功能，并展示数据建模、可视化设计和业务洞察能力。
