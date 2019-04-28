# predicting-housing-price
Udacity Machine Learning Project1

### 概述
该经典项目源自kaggle竞赛[预测波士顿房价](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/overview)，我们需要根据爱荷华州埃姆斯的个人住宅物业销售情况所整理的波士顿房屋信息（例如：地理位置，面积，卧室数量等）预测房源的价格。

本项目主要目的是：**练习模型评价与验证**，我最终的R2得分为***0.7627***。

### 开发环境与所需工具
* 开发环境：Windows10, anaconda5.3.0, jupyter notebook5.7.2, python3.7

* 库：numpy, pandas, matplotlib, seaborn, sklearn

### 数据集
此数据集可从[kaggle下载](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data)

### 方法
1. 导入数据，观察数据
* 导入数据
```
pandas.read_csv()
```

* 观察数据基本信息
```
df.head().append(df.tail()), df.describe().T, df.info()
```
2. 数据预处理
* 预处理：观察并填充缺失值，删除异常值

3. 探索性数据分析（EDA）：单变量分析（标签自身），多变量主观、客观分析（特征与标签之间）

* 单变量分析
```
sns.distplot()
```

* 多变量主观分析
```
类别特征：sns.barplot()、sns.pointplot()
数值型特征：sns.jointplot()
```

* 多变量客观分析
```
sns.pairplot()、sns.heatmap()
```
  
4. 特征分析，模型实现，作出预测
* 划分训练集与测试集，定义衡量标准，绘制学习曲线

* 网格搜索（GridsearchCV），交叉验证（KFold）
## 总结与收获

1. 熟悉了模型评价与验证的流程，seaborn中jointplot、barplot、pointplot、pairplot、distplot等方法的运用
```
sns.distplot(data_df['SalePrice'])
sns.pairplot(data_df,vars=['GrLivArea','OverallQual','TotalBsmtSF','GarageCars','1stFlrSF','SalePrice'],size=2)
sns.barplot(x='OverallQual',y='SalePrice',data=data_df)
sns.pointplot(x='PoolArea',y='SalePrice',data=data_df)
sns.jointplot(x='LotArea',y='SalePrice',data=data_df,kind='hex')
```
2. 统计并打印超过25%空数据的特征
```
limit_percent = 0.25
limit_value = len(data_df) * limit_percent
ls=list(data_df.columns[(data_df.shape[0]-data_df.count())>limit_value])
print(ls)
```
3. **类别特征：sns.barplot()、sns.pointplot()，数值型特征：sns.jointplot()**,sns.pairplot()、sns.heatmap(),sns.distplot()

4. **df.head().append(df.tail())**
