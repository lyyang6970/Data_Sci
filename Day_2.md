# Statistical and interpretable predictive modelling

**From clean longitudinal data to one prediction row**

<img width="722" height="77" alt="Screenshot 2026-11-03 at 09 13 06" src="https://github.com/user-attachments/assets/18c228c7-8bca-420a-95dd-bd65302396c6" />


## Formulating the prediction problem

**Constructing the binary teaching target**

<img width="822" height="286" alt="Screenshot 2026-11-03 at 17 56 05" src="https://github.com/user-attachments/assets/0702327c-ce23-4d51-90ab-a22c64f25c6f" />

> [!NOTE]
>
> 把 Medium 和 Severe 合并，可以使二分类任务更容易开展，但这也改变了原来的研究问题。
>
> 原来的问题是：
>
> “这个肝脏属于 Low、Medium 还是 Severe？”
>
> 合并后变成：
>
> “这个肝脏属于 Low，还是 Medium/Severe？”
>
> 因此，我们失去了区分 Medium 和 Severe 的能力。


**Development, resampling, and final test data**

<img width="332" height="209" alt="Screenshot 2026-11-03 at 18 07 48" src="https://github.com/user-attachments/assets/8c694291-8d99-4e1e-b9d0-16bbb3f0a6b1" />

Development set（开发集）用于：
- 拟合 Logistic Regression。
- 开发 Random Forest。
- 比较不同的模型参数。
- 确定最终模型的设置。

而 Final test set（最终测试集）必须保留到最后。

<img width="725" height="399" alt="Screenshot 2026-11-03 at 18 09 58" src="https://github.com/user-attachments/assets/0d504797-a668-408a-90d9-a355ede7d0c6" />

<img width="652" height="312" alt="Screenshot 2026-11-03 at 18 10 54" src="https://github.com/user-attachments/assets/bb0d7d61-ab69-491d-a040-0c2e19aed44e" />

> [!IMPORTANT]
> 注意：Validation set（验证集）与 Final test set（最终测试集）不是一回事。
>
> 验证集用于模型开发过程中的选择，最终测试集用于模型选择完成后的独立评估。

**Data leakage: four common pathways 数据泄漏的四种常见途径**

> [!NOTE]
> Data Leakage 的核心含义：模型在开发过程中使用了本不应该获得的信息，从而使模型的预测表现看起来比实际更好。

1. Target leakage（目标泄漏）: Include risk_score, which defines the label.

将直接决定目标标签的 risk_score 放进预测变量中。

2. Entity leakage（实体泄漏）: Place rows from one liver in several partitions.

将同一个肝脏的测量记录分配到不同的数据分区。

<img width="749" height="196" alt="Screenshot 2026-11-03 at 18 29 44" src="https://github.com/user-attachments/assets/fe44b698-b97d-49ae-93a9-43edd50037af" />

正确方法：按 unique_id 划分数据，确保同一个肝脏只属于一个分区。

3. Preprocessing leakage（预处理泄漏）: Estimate scaling or selection using all livers.

使用所有肝脏的数据来计算标准化参数或进行特征选择。

<img width="562" height="578" alt="Screenshot 2026-11-03 at 18 31 20" src="https://github.com/user-attachments/assets/1ea69742-1e8b-4045-b0fc-acbcb5d0a230" />

4. Identifier leakage（标识符泄漏）: Include unique_id, exported row indices, or identifier like centre.

**K-fold cross validation K 折交叉验证**

<img width="818" height="373" alt="Screenshot 2026-11-03 at 18 36 49" src="https://github.com/user-attachments/assets/da089cb0-3d7e-4bc6-99eb-a58a2acc5b26" />

> [!NOTE]
> K-fold Cross Validation（K 折交叉验证，简称 K-fold CV）是一种评估模型在未参与该次训练的数据上表现的方法。
>
> 它的基本思想是：
>
> 把开发数据分成 K 组，每次用其中 K−1 组训练模型，剩下 1 组验证模型。
>
> 重复 K 次，让每组数据都轮流充当一次验证集。

<img width="410" height="257" alt="Screenshot 2026-11-03 at 18 38 51" src="https://github.com/user-attachments/assets/d6ec9b9f-013a-4745-9452-2ba6f6591ef4" />

**Why preprocessing belongs inside each fold 为什么数据预处理必须在每一折交叉验证内部进行？**

<img width="829" height="331" alt="Screenshot 2026-11-03 at 18 42 13" src="https://github.com/user-attachments/assets/ad4651c2-700b-4c8d-8321-cbf3b7a271d8" />

<img width="783" height="693" alt="Screenshot 2026-11-03 at 18 49 09" src="https://github.com/user-attachments/assets/7a745ea2-96bf-4f68-8f4f-3f00f761197f" />

> [!IMPORTANT]
> *这种问题叫作：Preprocessing leakage（预处理泄漏），这里具体表现为特征选择泄漏。*

<img width="776" height="420" alt="Screenshot 2026-11-03 at 18 50 48" src="https://github.com/user-attachments/assets/e8df5c5c-8092-4ee0-8c37-c82b614257de" />

**Regression predicts a numerical outcome**

<img width="822" height="186" alt="Screenshot 2026-11-03 at 18 55 11" src="https://github.com/user-attachments/assets/38065860-37d3-426e-b83f-291e1d8f7eaa" />

*Regression:* Regression 的目标是预测一个**数值**，而不是一个类别。

*Classification:* 预测一个**类别**，通常先估计属于某个类别的概率。

<img width="774" height="389" alt="Screenshot 2026-11-03 at 18 59 40" src="https://github.com/user-attachments/assets/2a5d294e-307d-41a6-8bf5-280b37f94ee6" />


## Clustering and logistic regression

**Clustering as exploratory data analysis**

<img width="711" height="296" alt="Screenshot 2026-11-03 at 19 14 01" src="https://github.com/user-attachments/assets/28cf2f0e-60aa-4a31-adac-b6ddb58b375b" />

Clustering是一种 **无监督学习（Unsupervised Learning）** 方法。我们没有一个已知的结果标签来告诉模型哪些分组是正确的。

Clustering 结果取决于：
- 选择了哪些变量。
- 使用什么距离衡量相似性。
- 是否进行了标准化。
- 使用了哪一种聚类算法。
因此，clustering 得到的组并不自动代表真实存在的生物学群体。

举例来说：

同样的 75 个肝脏，如果我们只使用 Age 和 BMI 聚类，可能得到两组。

但如果改用 Lactate 和 Bilirubin，可能得到完全不同的分组。

所以聚类结果不是绝对的，它依赖于分析方法。

**K-means clustering: compact groups around centroids K 均值聚类——围绕聚类中心形成紧凑的分组**

K-means 希望最小化所有观察对象到其所属聚类中心的平方距离总和。

<img width="750" height="367" alt="Screenshot 2026-11-03 at 19 23 32" src="https://github.com/user-attachments/assets/c7a85c4d-ef4e-44c4-834f-6db619459f36" />

*K-means:* 将观察对象分成 K 个组，使每个观察对象尽可能接近自己所在组的中心。

Centroid 就是这个 Cluster 中所有点的平均位置。

<img width="479" height="561" alt="Screenshot 2026-11-03 at 19 26 15" src="https://github.com/user-attachments/assets/e14d0d56-007c-47a5-bf06-a00edc446bea" />

<img width="756" height="388" alt="Screenshot 2026-11-03 at 19 31 31" src="https://github.com/user-attachments/assets/bcd4f5f7-0a41-499f-ad34-b74af7427df1" />

**Hierarchical clustering: building a tree of similarity 层次聚类——构建表示相似关系的树状图**

<img width="697" height="380" alt="Screenshot 2026-11-03 at 19 35 32" src="https://github.com/user-attachments/assets/d39642fa-90c1-499e-935d-c184c56442a4" />

1. *Agglomerative idea：凝聚型层次聚类的基本思想*

首先，将每个观察对象看作一个独立的 Cluster。

然后，不断合并距离最近的两个 Cluster，直到所有观察对象都被连接到同一棵树中。

<img width="688" height="410" alt="Screenshot 2026-11-03 at 19 41 18" src="https://github.com/user-attachments/assets/a1c188ed-2756-4a97-8db8-fafda97469f3" />

2. *What defines “closest”？*

Distance（距离）：衡量两个观察对象之间有多相似。

Linkage（连接准则）：定义两个 Cluster 之间的距离应该如何计算。

> [!NOTE]
>
> *Complete linkage（完全连接法）*
>
> 计算两个 Cluster 中所有跨组观察对象之间的距离，取其中最大的距离作为两组之间的距离。
>
> *Average linkage（平均连接法）*
>
> 计算两个 Cluster 中所有跨组观察对象之间的距离，然后取平均值。
>
> *Ward linkage*
>
> 选择合并后使组内变异增加最少的两个 Cluster。Ward 方法希望合并后的 Cluster 仍然尽可能紧凑。

<img width="756" height="581" alt="Screenshot 2026-11-03 at 19 47 50" src="https://github.com/user-attachments/assets/bd2e3c2b-6007-458c-bddf-e356b0c11ba6" />

第一步：观察 A 和 B

A 和 B 在较低的位置合并。

这意味着 A 和 B 比较相似。

第二步：观察 D 和 E

D 和 E 也在较低的位置合并。

这说明它们也比较相似。

第三步：观察 C

C 与已经形成的 A、B 组合在更高的位置合并。

说明按照当前的距离和 Linkage 规则，C 与 A、B 组合的差异比 A 与 B 之间的差异更大。

第四步：最后合并

左边的 A、B、C 和右边的 D、E 最终在更高的位置合并。

这表示两个大组之间的差异更大。

注意：树状图的纵轴是 Dissimilarity（不相似程度），不是时间。

*K-means VS Hierarchical clustering*

<img width="765" height="213" alt="Screenshot 2026-11-03 at 19 49 10" src="https://github.com/user-attachments/assets/38c20e33-4743-495f-86ca-998ff1ec8abe" />

**Choosing and checking clusters**

<img width="765" height="285" alt="Screenshot 2026-11-03 at 19 58 14" src="https://github.com/user-attachments/assets/10a82ace-f7a7-4c29-bc37-4be3074d4a4e" />

1. Elbow Method：肘部法则

寻找这样一个位置：超过这个位置之后，即使继续增加 Cluster 数量，组内变异的下降幅度也已经很小。

2. Silhouette Width：轮廓系数

a(i) 与自己所在组的其他观察对象平均距离。

b(i) 不是到最近一个其他观察对象的距离，而是到其他 Cluster 的平均距离中最小的那个。

<img width="530" height="139" alt="Screenshot 2026-11-03 at 20 21 56" src="https://github.com/user-attachments/assets/b445fc41-83f4-4412-913e-b75ab6ade2dc" />

**Returning to the binary prediction risk**

<img width="819" height="216" alt="Screenshot 2026-11-04 at 08 03 13" src="https://github.com/user-attachments/assets/55a4f126-de28-4ec5-a28b-1c2d1e3b58b3" />

*Continuous outcome regression:* 在已知这个肝脏预测变量的情况下，连续结果ri的条件平均值。

*Binary classification:* 在已知第i个肝脏预测变量的条件下，该肝脏属于 Elevated risk 的概率。

Suitable Training Loss（合适的训练损失）:

<img width="786" height="278" alt="Screenshot 2026-11-04 at 08 09 11" src="https://github.com/user-attachments/assets/dcc7729b-5451-40a1-a34b-91f0a35f44ff" />

**Why ordinary linear regression is unsuitable 为什么普通线性回归不适合二分类预测？**

<img width="816" height="240" alt="Screenshot 2026-11-04 at 08 12 49" src="https://github.com/user-attachments/assets/ac78ff1f-e594-468e-86ef-8e1d9d768cfd" />

<img width="440" height="308" alt="Screenshot 2026-11-04 at 08 14 15" src="https://github.com/user-attachments/assets/97569fee-c2a2-40dd-89fc-1c192120155b" />

<img width="527" height="385" alt="Screenshot 2026-11-04 at 08 15 08" src="https://github.com/user-attachments/assets/8d0c9c2d-a780-4c32-b25e-2d88c4b4e4d7" />

Problem 1: 线性预测分数 η 没有固定的上下界，但概率必须位于 0 和 1 之间。

<img width="455" height="212" alt="Screenshot 2026-11-04 at 08 17 47" src="https://github.com/user-attachments/assets/124a6dcc-f75f-4225-ab68-3d4f9bc677a1" />

<img width="699" height="522" alt="Screenshot 2026-11-04 at 08 18 59" src="https://github.com/user-attachments/assets/70df5594-0d85-4a5e-a099-675fc03ce717" />

Problem 2：方差不是常数。

- 当概率接近 0 时，方差很小。
- 当概率接近 1 时，方差也很小。
- 当概率等于 0.5 时，方差最大，为 0.25。

为什么？

因为当事件概率为 0.5 时，结果最不确定。

而当事件概率接近 0 或 1 时，结果相对更确定。

*考试重点：* 二分类变量具有 Heteroscedasticity（异方差性），即条件方差随预测概率变化。

Problem 3：直线无法很好地描述概率边界附近的变化

<img width="739" height="484" alt="Screenshot 2026-11-04 at 08 23 56" src="https://github.com/user-attachments/assets/04bba72f-3e4a-423a-975f-241cb0d47bee" />

<img width="501" height="330" alt="Screenshot 2026-11-04 at 08 24 47" src="https://github.com/user-attachments/assets/582134e5-3ded-4b36-8c10-53bca4e5b813" />

**Odds and log odds**

<img width="582" height="169" alt="Screenshot 2026-11-04 at 08 27 28" src="https://github.com/user-attachments/assets/ebac4977-7b30-4fab-b99d-761189b94125" />

> [!NOTE]
>
> Odds 表示：事件发生的概率与事件不发生的概率之比。
>
> Log Odds: 这里的log是自然对数，也就是ln。Logit 是 Log odds 的另一种名称。
>
> 为什么要取Log？
>
> <img width="677" height="688" alt="Screenshot 2026-11-04 at 08 36 21" src="https://github.com/user-attachments/assets/780827b1-441b-4405-8beb-153951d7aa98" />

<img width="776" height="448" alt="Screenshot 2026-11-04 at 08 37 26" src="https://github.com/user-attachments/assets/d3d7c81b-8494-453e-ac84-5c46d831c0db" />

**Deriving the inverse logit**

<img width="807" height="276" alt="Screenshot 2026-11-04 at 08 39 58" src="https://github.com/user-attachments/assets/5b6071ad-ff18-4829-91a8-60c40311be9c" />

**The logistic-regression model 逻辑回归模型**

<img width="682" height="444" alt="Screenshot 2026-11-04 at 08 43 43" src="https://github.com/user-attachments/assets/4f201049-fcaf-442d-aae2-d316cb0d07cd" />

- 第一步：计算 Linear predictor

<img width="531" height="596" alt="Screenshot 2026-11-04 at 08 44 44" src="https://github.com/user-attachments/assets/6a70f057-db08-4c71-b017-55f4e7628b6b" />


- 第二步：将 Linear predictor 转换成 Probability

- 第三个公式：为什么 Logistic Regression 是线性的？

<img width="774" height="604" alt="Screenshot 2026-11-04 at 08 47 15" src="https://github.com/user-attachments/assets/4d0e4115-e2b3-40a4-9f78-b08fa6da16e3" />

<img width="770" height="496" alt="Screenshot 2026-11-04 at 08 47 54" src="https://github.com/user-attachments/assets/24ab46fd-8950-4792-94a1-d44f928ca963" />

**Coefficient interpretation**

<img width="822" height="338" alt="Screenshot 2026-11-04 at 08 52 00" src="https://github.com/user-attachments/assets/5bc51972-2807-4d05-91d2-72a2393b8ac5" />

> [!IMPORTANT]
>
> 预测变量增加一个单位，Log odds 增加 βj。回归系数 β 描述的是 Log odds 的变化，而不是 Probability 的直接变化。
>
> <img width="675" height="681" alt="Screenshot 2026-11-04 at 08 55 57" src="https://github.com/user-attachments/assets/3afca545-e2de-4fd9-bbf2-2184a53348c7" />

<img width="785" height="140" alt="Screenshot 2026-11-04 at 09 01 45" src="https://github.com/user-attachments/assets/d159abbb-a17b-45c0-87f6-577927a6aa2c" />

**From Bernoulli probabilities to likelihood**

<img width="824" height="169" alt="Screenshot 2026-11-04 at 09 10 02" src="https://github.com/user-attachments/assets/66d1d1f2-da00-4462-8934-fe871ad2e671" />

> [!IMPORTANT]
>
> **Bernoulli distribution（伯努利分布）**用于描述只有两种可能结果的随机变量。
>
> 例如：
> - 抛硬币：正面或反面。
> - 患病情况：患病或未患病。
> - 本次肝脏分类：Elevated 或 Low。

<img width="785" height="323" alt="Screenshot 2026-11-04 at 09 17 46" src="https://github.com/user-attachments/assets/776aee11-1b72-4046-b3a4-aab0bc3f1205" />

Likelihood 衡量在某组模型参数下，已经观察到的这些真实标签有多合理。

> [!NOTE]
> 
> Probability（概率）
>
> 给定模型参数，研究不同结果出现的可能性。
>
> Likelihood（似然）
>
> 观察结果已经确定，我们比较不同模型参数对这个结果的支持程度。

**Log-likelihood and cross-entropy**














