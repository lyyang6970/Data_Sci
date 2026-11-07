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

**Likelihood for independent observations**

<img width="818" height="280" alt="Screenshot 2026-11-04 at 09 33 06" src="https://github.com/user-attachments/assets/ea89b337-3959-4eba-86c3-49e244d38081" />

<img width="773" height="309" alt="Screenshot 2026-11-04 at 09 34 18" src="https://github.com/user-attachments/assets/d41d3e65-0ca7-4b3c-b6c8-6fa5d19e6eab" />

**Log-likelihood and cross-entropy**

*使用log-likelihood的原因：* 如果我们有很多数据，每个概率都小于 1，不断相乘就可能得到一个非常接近 0 的数。取对数之后，原本的连乘就可以转换成求和。

所以 Log-likelihood 通常是非正数。

而我们希望定义一个：

越小越好的 Loss（损失函数）。

因此，对 Log-likelihood 取负号。
于是：
- Maximum Log-likelihood：越大越好。
- Minimum Negative Log-likelihood：越小越好。
它们对应相同的优化目标。

**How logistic regression minimises the loss 逻辑回归如何最小化损失函数**

<img width="823" height="324" alt="Screenshot 2026-11-04 at 09 57 17" src="https://github.com/user-attachments/assets/ed2c1f30-5de7-448b-b1ea-6d4b7e011a2e" />

<img width="754" height="515" alt="Screenshot 2026-11-04 at 09 58 06" src="https://github.com/user-attachments/assets/325d3b8e-3659-46ff-b181-5cd25969c9e4" />

<img width="700" height="301" alt="Screenshot 2026-11-04 at 10 20 38" src="https://github.com/user-attachments/assets/b10d8444-2e9e-4401-80b3-56f1cc7eed03" />

**Reading the logistic output before interpreting effects**

<img width="813" height="243" alt="Screenshot 2026-11-04 at 10 23 07" src="https://github.com/user-attachments/assets/70bb9a2f-672b-4927-b648-5c9bbf45331d" />

<img width="732" height="662" alt="Screenshot 2026-11-04 at 10 29 36" src="https://github.com/user-attachments/assets/b7eeba6a-99c8-4e4d-932e-64531d3892ad" />

<img width="795" height="596" alt="Screenshot 2026-11-04 at 10 29 55" src="https://github.com/user-attachments/assets/b8ca49d7-925a-4ba2-bc5a-6b7fc20301ec" />

<img width="684" height="98" alt="Screenshot 2026-11-04 at 10 31 02" src="https://github.com/user-attachments/assets/48b0a705-a378-411a-9be8-68e42cfb04b3" />

<img width="599" height="356" alt="Screenshot 2026-11-04 at 10 31 20" src="https://github.com/user-attachments/assets/b7a87c23-eaec-404c-b56b-64c0eb0d1945" />

<img width="715" height="446" alt="Screenshot 2026-11-04 at 10 52 04" src="https://github.com/user-attachments/assets/7b9a4f81-edd5-408a-986e-6c333a8040cf" />

## From decision trees to the random forest comparator

**Why include one nonlinear model?**

Logistic regression assumes an additive linear relationship on the log odds scale unless interactions or transformations are specified.

如果没有额外加入交互项或变量变换，Logistic Regression 假设预测变量与 Log odds 之间存在加性线性关系。

<img width="812" height="206" alt="Screenshot 2026-11-05 at 10 33 02" src="https://github.com/user-attachments/assets/c90b37b1-ee92-4bc9-9c29-b9841440c26b" />

<img width="747" height="538" alt="Screenshot 2026-11-05 at 10 33 44" src="https://github.com/user-attachments/assets/03063ba7-d942-4a9b-8f0d-7fd2d64bef8c" />

**Recursive binary partitioning: the leaf majority**

> [!NOTE]
>
> Recursive binary partitioning 就是反复使用二元判断，将数据逐步划分成更小的组。
>
> 叶节点中数量较多的类别，决定该叶节点的最终分类结果。

**Gini impurity**

<img width="822" height="322" alt="Screenshot 2026-11-05 at 10 38 07" src="https://github.com/user-attachments/assets/3cc65e69-4533-4f95-8616-1443a675125d" />

*类别越均衡地混合，Gini 越高；节点越接近只有一种类别，Gini 越低。*

**Choosing a split**

当决策树有很多种可能的分裂方式时，它选择能够使 Gini Impurity *降低最多*的分裂方式。

<img width="782" height="265" alt="Screenshot 2026-11-05 at 10 45 35" src="https://github.com/user-attachments/assets/5eb20dc7-69c5-431a-a8e8-8d56b8e68b94" />

Compare the eligible candidate splits and choose the one with the largest positive impurity reduction.

比较所有符合条件的候选分裂，选择能够带来最大正向不纯度下降的分裂。

**Why trees overfit? 为什么决策树容易过拟合？**

> [!NOTE]
>
> Overfitting 指的是：模型过度适应训练数据中的细节和随机噪声，导致它在训练集上表现很好，但在新数据上的表现可能较差。

<img width="803" height="305" alt="Screenshot 2026-11-05 at 10 53 56" src="https://github.com/user-attachments/assets/9a48a606-bc32-427d-8f7e-1df020a8e883" />

<img width="486" height="478" alt="Screenshot 2026-11-05 at 10 54 58" src="https://github.com/user-attachments/assets/6713d6a2-6246-41fd-8b9c-51552f2bd094" />

<img width="774" height="612" alt="Screenshot 2026-11-05 at 10 54 39" src="https://github.com/user-attachments/assets/2b13947b-e978-4042-b584-88b7641beb13" />

> [!IMPORTANT]
>
> Locally optimal（局部最优）不一定等于 Globally optimal（全局最优）。
>
> 这种每一步选择当前最优分裂的策略称为 Greedy approach（贪心策略）。

**From one decision tree to a random forest**

<img width="770" height="343" alt="Screenshot 2026-11-05 at 10 59 09" src="https://github.com/user-attachments/assets/c8983ea7-aef8-44da-88e8-b3390a0a39e3" />

> [!NOTE]
>
> 当训练数据发生变化时，单棵决策树可能发生很大的改变。而随机森林将许多有意构建得不同的决策树组合起来。
>
> Random Forest 可以理解为：
>
> 建立很多棵不同的 Decision Trees，然后综合它们对同一个新观察对象的预测。

<img width="760" height="520" alt="Screenshot 2026-11-05 at 11 43 58" src="https://github.com/user-attachments/assets/6408447c-9dad-4feb-9f90-438e33914499" />

**Bootstrap sampling: a different training sample for each tree**

<img width="799" height="312" alt="Screenshot 2026-11-06 at 18 23 15" src="https://github.com/user-attachments/assets/c420a246-439c-4bc2-909b-bc7248b8962c" />

Bootstrap Sampling 是从训练数据中有放回地随机抽样，并且抽取次数等于原始训练样本的行数。

*Bootstrap sample size ≠ Number of unique observations。*

> [!NOTE]
> 
> Out-of-bag（OOB）：什么是袋外样本？
>
> 对于某棵树而言，在它的 Bootstrap sample 中没有被抽中的肝脏，叫作 Out-of-bag（袋外样本，OOB）。
>
> <img width="501" height="302" alt="Screenshot 2026-11-06 at 18 34 44" src="https://github.com/user-attachments/assets/e1860cf6-b483-46b8-ad3c-c314339ec5f3" />

*必须对完整的肝脏特征行进行重抽样，不能对单独的时间点测量记录进行重抽样。*

**Bootstrap sampling: why approximately 63.2%? 为什么 Bootstrap 抽样平均只包含约 63.2% 的不同观察对象？**

一个 Bootstrap sample 会从 \(N\) 个肝脏中，进行 \(N\) 次有放回抽样。

我们现在只关注某一个特定的肝脏。

例如，在 60 个肝脏中，我们只关注 Liver A。

我们希望计算：

Liver A 在这 60 次抽样中，至少出现一次的概率是多少？

<img width="812" height="318" alt="Screenshot 2026-11-06 at 18 47 37" src="https://github.com/user-attachments/assets/0a415f7e-2aea-4d5d-a715-85ad685ac67c" />

<img width="211" height="72" alt="Screenshot 2026-11-06 at 18 50 47" src="https://github.com/user-attachments/assets/ca4bbdc7-4933-43fe-a0f9-32d103f2895e" />

**Random predictors at every split**

<img width="802" height="293" alt="Screenshot 2026-11-06 at 18 56 15" src="https://github.com/user-attachments/assets/6f4c4cab-260d-4d5d-84d6-6ea35db43958" />

我们一共有 4 个预测变量，但每次分裂时，只随机选择其中 2 个供模型考虑。

<img width="752" height="461" alt="Screenshot 2026-11-06 at 19 03 03" src="https://github.com/user-attachments/assets/f9f8e178-cdb8-4399-a7d2-7673093d8b85" />

**Probability prediction: average the leaf probabilities**

<img width="774" height="354" alt="Screenshot 2026-11-06 at 19 22 19" src="https://github.com/user-attachments/assets/57944e21-eb6b-461a-a81c-73635a93d243" />

如果使用多数投票，这个例子会预测 Elevated，但多数投票与概率平均是两种不同的组合规则。

<img width="419" height="157" alt="Screenshot 2026-11-06 at 19 25 31" src="https://github.com/user-attachments/assets/2da12258-a2c0-4a6f-a6c3-68acc7507710" />

> [!IMPORTANT]
>
> The forest's flexibility does not solve the small sample problem.
>
> 随机森林的灵活性不能解决样本量过小的问题。

<img width="732" height="377" alt="Screenshot 2026-11-07 at 13 42 45" src="https://github.com/user-attachments/assets/dac2fdab-15b9-44fb-a560-fd03f7430ecc" />

## Evolution that matches health decisions

**Confusion-matrix notation**

<img width="275" height="273" alt="Screenshot 2026-11-07 at 14 34 30" src="https://github.com/user-attachments/assets/e22c7b5a-dd4a-4906-85be-7ce3afc9d658" />

True / False 表示预测是否正确。

Positive / Negative 表示模型预测的类别。

> [!NOTE]
>
> TP: 真实类别是 Positive，模型也预测为 Positive。
>
> TN: 真实类别是 Negative，模型也预测为 Negative。
>
> FP: 真实类别是 Negative，但模型错误地预测为 Positive。
>
> FN: 真实类别是 Positive，但模型错误地预测为 Negative。（Missed case（漏检））

The four counts depend on a selected probability threshold and define sensitivity, specificity, precision, and accuracy.

TP、FP、FN 和 TN 这四个数量取决于所选择的预测概率阈值，并且可以用于计算敏感度、特异度、精确率和准确率。

<img width="769" height="174" alt="Screenshot 2026-11-07 at 14 38 49" src="https://github.com/user-attachments/assets/e9d44ecd-9050-4147-8557-98911b31c427" />

**Core classification metrics**

<img width="799" height="276" alt="Screenshot 2026-11-07 at 14 40 34" src="https://github.com/user-attachments/assets/ea440549-1d95-4797-9032-20ea197992c7" />

*Sensitivity:* 在所有真实属于 Positive 的观察对象中，有多少比例被模型正确预测为 Positive？

*Specificity:* 在所有真实属于 Negative 的观察对象中，有多少比例被模型正确预测为 Negative？

*Precision:* 在所有被模型预测为 Positive 的观察对象中，有多少比例实际上属于 Positive？

*Accuracy:* 在所有观察对象中，有多少比例被正确分类？

**F1 score and macro-F1**

<img width="810" height="383" alt="Screenshot 2026-11-07 at 14 44 08" src="https://github.com/user-attachments/assets/2034460a-641f-41a8-8e2f-20754fd22b26" />

*不包含TN*

Macro-F1 对每个类别给予相同的权重。当我们希望少数类别与常见类别的表现同样受到重视时，Macro-F1 很有用。

应该使用验证预测结果比较模型，同时报告每个类别各自的 F1，因为平均值可能掩盖某个类别表现很差的问题。

**ROC curve and AUROC**

<img width="823" height="350" alt="Screenshot 2026-11-07 at 15 27 37" src="https://github.com/user-attachments/assets/84c1a17a-9583-4c32-a800-915c8032ce2a" />

理想情况下，我们希望：
- TPR 越高越好。
- FPR 越低越好。

ROC 图的左上角是理想位置。

> [!NOTE]
>
> <img width="440" height="654" alt="Screenshot 2026-11-07 at 15 47 26" src="https://github.com/user-attachments/assets/484753f9-092f-4a39-bb38-f5f3e3ce13c0" />
>
> ROC 曲线就是把不同阈值对应的 FPR 和 TPR 画在同一张图上。
>
> 注意：真实标签始终不变，改变的只是模型将概率转换成类别的规则。

*AUROC:* ROC 曲线下面积

<img width="778" height="385" alt="Screenshot 2026-11-07 at 15 54 33" src="https://github.com/user-attachments/assets/ca18b6d5-f1d1-40b0-904c-d565d1c14d79" />

AUROC 衡量模型将 Positive 排在 Negative 前面的能力，而不是预测概率数值本身是否准确。

**Precision–recall curve and its area**

<img width="819" height="305" alt="Screenshot 2026-11-07 at 16 00 27" src="https://github.com/user-attachments/assets/f5d54dbf-4f61-479e-a939-4bf1e68affd5" />

<img width="516" height="171" alt="Screenshot 2026-11-07 at 16 01 22" src="https://github.com/user-attachments/assets/62a88007-5252-4fe2-8df6-db574900cdb1" />

PR 曲线的理想位置是右上角，对应Recall=1，Precision=1，这意味着：

- 所有真实 Positive 都被找到了。
- 所有预测 Positive 都是正确的。

也就是既没有漏检，也没有误报。

随机排序模型的 PR 参考水平是数据中的 Positive prevalence。

> [!IMPORTANT]
>
> ROC 关注 FPR 与 TPR 的关系，而 PR 关注 Precision 与 Recall 的关系。

<img width="541" height="161" alt="Screenshot 2026-11-07 at 16 24 40" src="https://github.com/user-attachments/assets/b2d747a2-8c4c-46ab-8137-fa93851c4d6b" />

<img width="615" height="187" alt="Screenshot 2026-11-07 at 16 24 57" src="https://github.com/user-attachments/assets/83bf9d56-1387-4cf2-8614-cc7eb30680ad" />

ROC 曲线
- 新加入一个 TP，曲线向上。
- 新加入一个 FP，曲线向右。
- 关注 TPR 与 FPR 的关系。

PR 曲线
- 新加入一个 TP，Recall 上升，Precision 可能上升。
- 新加入一个 FP，Recall 不变，Precision 下降。
- 关注 Recall 与 Precision 的关系。

需要特别记住三个结论：
1. ROC：新增 TP 向上，新增 FP 向右。
2. PR：新增 TP 可能使 Precision 上升；新增 FP 会使 Precision 下降，而 Recall 不变。
3. AUROC = 0.75 和 AUPRC = 0.792 不能直接比较大小来判断哪一种评价更好，因为它们衡量的内容不同。

**Why precision–recall depends on positive prevalence**

*为什么一个模型即使具有很高的 Sensitivity（敏感度）和 Specificity（特异度），它的 Precision 仍然可能非常低？*

<img width="813" height="389" alt="Screenshot 2026-11-07 at 16 43 42" src="https://github.com/user-attachments/assets/de3278ad-b3e5-4ff8-8b64-dbec8bbfe3cf" />

<img width="748" height="710" alt="Screenshot 2026-11-07 at 16 44 16" src="https://github.com/user-attachments/assets/17ab2b34-0c70-4d6e-96d6-64755e9edde9" />

**Calibration**

<img width="763" height="349" alt="Screenshot 2026-11-07 at 16 46 31" src="https://github.com/user-attachments/assets/7b73c709-39f1-444d-81c5-a5faa624b419" />

*Calibration:* 

<img width="771" height="349" alt="Screenshot 2026-11-07 at 18 03 00" src="https://github.com/user-attachments/assets/66d2b66b-38a9-4582-b8f8-3945fdc5844e" />

1. Perfect calibration（完美校准）模型预测多少，实际发生比例就大约是多少。
2. Overconfident（过度自信）过度自信意味着模型的预测概率太极端。（模型预测过于接近 0 或 1。）

例如：
- 对高风险组预测 90%，但实际只有 70%。
- 对低风险组预测 10%，但实际有 30%。
注意这里的两个方向：

对于高预测风险：

Observed < Predicted

对于低预测风险：

Observed > Predicted

3. Underconfident（信心不足）模型预测概率不够极端，过于靠近 0.5。

整体校准用于判断模型总体上是否低估或高估事件发生风险。

<img width="783" height="137" alt="Screenshot 2026-11-07 at 18 08 01" src="https://github.com/user-attachments/assets/c1dfa7be-e7dd-4b86-8d3e-dfd66a4f844b" />

**Brier score（布里尔评分）**

<img width="819" height="268" alt="Screenshot 2026-11-07 at 18 15 56" src="https://github.com/user-attachments/assets/9ca5949a-aa27-4d77-9937-5f2da7a33c0f" />

> [!IMPORTANT]
>
> Brier score 是预测概率与真实标签之间的平均平方误差。
>
> 注意：它与普通回归中的 Mean Squared Error（MSE）在数学形式上相同。
>
> 区别在于，这里：
> - 真实标签只能是 0 或 1。
> - 模型预测的是 0 到 1 之间的概率。
>
> 预测概率越接近真实标签，Brier score 越小。
>
> Brier score 同时反映模型的区分能力和概率校准表现。

<img width="566" height="475" alt="Screenshot 2026-11-07 at 18 25 47" src="https://github.com/user-attachments/assets/51d12701-5f78-447b-9398-8861342344f5" />

<img width="723" height="427" alt="Screenshot 2026-11-07 at 18 40 46" src="https://github.com/user-attachments/assets/3ecb4b5d-3ee8-437f-8c2b-cec414f931cf" />

降低阈值可以减少漏检，但通常会增加误报和后续处理负担。

**Evaluation metrics: what to use and when**

<img width="788" height="471" alt="Screenshot 2026-11-07 at 18 48 31" src="https://github.com/user-attachments/assets/78211f77-2b11-40b3-a51c-6e225ad11819" />

**Comparing models: confidence intervals for differences**

<img width="898" height="427" alt="Screenshot 2026-11-07 at 19 03 39" src="https://github.com/user-attachments/assets/0f8fda30-3360-4edc-a383-a238778b1560" />

配对 Bootstrap：在每一次重抽样中，使用相同的观察对象比较两个模型。

如果我们抽中了 Liver A，那么必须同时保留：
- Liver A 的真实标签。
- Model A 对 Liver A 的预测概率。
- Model B 对 Liver A 的预测概率。

<img width="749" height="524" alt="Screenshot 2026-11-07 at 19 25 14" src="https://github.com/user-attachments/assets/e83ba299-9491-4d8e-9b12-4e2181ec9ccd" />

> [!IMPORTANT]
>
> 差异的哪个方向表示 Model A 更好？
>
> 情况 1：AUROC 或 F1：越大越好。
>
> 情况 2：Brier score 或 Log loss：越小越好。
>
> 两个模型、事先选定的分类阈值以及错误成本都应该保持固定。

**Calculating the endpoints of a 95% interval**

<img width="908" height="419" alt="Screenshot 2026-11-07 at 19 32 37" src="https://github.com/user-attachments/assets/ff30c54f-c3c4-4a22-be77-0a184aff9dbc" />

Step 1：首先，将所有 Bootstrap 结果按照从小到大的顺序排列。

Step 2：计算百分位数的位置

Step 3：Interpolate（插值）: Linear interpolation（线性插值）。

<img width="529" height="200" alt="Screenshot 2026-11-07 at 19 51 33" src="https://github.com/user-attachments/assets/9b0cccd7-f6a8-452b-94af-3d9f95fa66a5" />

置信区间端点是评价指标的数值或两个模型指标的差异，而不是它在排序列表中的位置。












































