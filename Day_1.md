# Day 1

**Equality VS Equity**

<img width="679" height="364" alt="Screenshot 2026-11-02 at 09 15 23" src="https://github.com/user-attachments/assets/3d5caaf1-20bb-49c9-bf9d-fc0a6b248686" />

用医疗资源举例
假设有两个地区：
- A 地区：1000 人，其中大多数是健康的年轻人。
- B 地区：1000 人，其中有很多老年人和慢性病患者。
Equality 的做法：

两个地区各分配 5 名医生。

因为人口相同，所以医疗资源相同。

但问题是，B 地区患者更多，5 名医生可能根本不够。

Equity 的做法：

A 地区分配 3 名医生，B 地区分配 7 名医生。

因为 B 地区的医疗需求更高，所以获得更多资源。

这种分配虽然不相同，但可能更加公平。

## Health Data and Clinical Meaning
<img width="754" height="342" alt="Screenshot 2026-11-02 at 09 19 14" src="https://github.com/user-attachments/assets/6d174a96-5737-4b3c-8d88-29b0147c926b" />


<img width="907" height="300" alt="Screenshot 2026-11-02 at 09 20 28" src="https://github.com/user-attachments/assets/28a2baad-78aa-4c79-8605-f4f316484d9f" />

**Step 1: Question and Target Quantity（研究问题与目标量）**
这是整个研究的起点。

在收集或分析数据之前，必须先明确：
- 我们究竟想研究什么？
- 我们想研究哪一类人？
- 我们最终想估计或预测什么？

**Step 2: Extract and Document（提取数据并记录）**
明确问题之后，需要获取数据。

Extract（提取）可以包括：
- 从医院电子病历中提取患者数据。
- 从公共卫生数据库下载数据。
- 从调查问卷中获取数据。
- 从多个数据源导入数据。
Document（记录）是指清楚地说明：
- 数据来自哪里？
- 数据什么时候收集？
- 每个变量是什么意思？
- 数据提取过程中进行了哪些操作？

**Step 3: Clean and Merge（清洗和合并数据）**
现实世界中的医疗数据通常不是完美的。

可能出现：
- Missing values（缺失值）
- Duplicate records（重复记录）
- Incorrect values（错误值）
- Inconsistent formats（格式不一致）
Clean（清洗） 是发现并合理处理这些问题。

**Step 4: Explore and Audit（探索与审查数据）**
这一阶段的重点是：

在建模之前，先了解数据的特点并检查数据质量。

Explore（探索）通常包括：
- 查看变量分布。
- 计算均值、中位数、标准差。
- 绘制直方图和散点图。
- 检查变量之间的关系。

**Step 5: Model and Evaluate（建模与评估）**
完成前面的步骤后，才进入建模阶段。

Model（建模）可以包括：
- Linear regression（线性回归）
- Logistic regression（逻辑回归）
- Survival analysis（生存分析）
- Machine learning（机器学习）

1. The process is iterative; it does not proceed in only one direction.
数据分析是一个迭代过程，并不是只能单向进行。
2. Each transformation should be reproducible and traceable.
每一次数据转换都应该是可复现、可追踪的。
3. Modelling begins only after the final processed dataset has a defensible meaning.
只有当最终处理后的数据集具有合理、可解释且有依据的含义时，才应该开始建模。


<img width="736" height="669" alt="Screenshot 2026-11-02 at 09 26 55" src="https://github.com/user-attachments/assets/d5e229f9-11ee-4499-aff0-35655020ea37" />

<img width="794" height="344" alt="Screenshot 2026-11-02 at 09 27 12" src="https://github.com/user-attachments/assets/7779c917-ad53-4b8e-b633-6fa900b6e704" />

<img width="922" height="322" alt="Screenshot 2026-11-02 at 09 28 41" src="https://github.com/user-attachments/assets/02e0b0d2-216e-40d8-b582-09e15ef75f4d" />

<img width="719" height="223" alt="Screenshot 2026-11-02 at 09 29 06" src="https://github.com/user-attachments/assets/6e480c23-dec5-471b-b46e-2d1c9728afce" />

> [!IMPORTANT]
> A dataset may be technically structured while its clinical meaning remains inconsistent.
> 一个数据集即使在技术上是结构化的，其临床含义仍然可能不一致。<img width="918" height="419" alt="Screenshot 2026-11-02 at 09 32 44" src="https://github.com/user-attachments/assets/183ffeff-093e-47da-bfe8-5a1a65c7acb4" />


<img width="804" height="609" alt="Screenshot 2026-11-02 at 09 31 21" src="https://github.com/user-attachments/assets/3f3a4dc8-357d-458c-82cf-3a451973876d" />

Terminology 是一套标准化的医学语言，用来准确描述患者的疾病、症状、诊断和治疗。
Classification 用于报告、比较和统计分析的更广泛的类别。

> [!NOTE]
> Classification 与 Terminology 的区别在于：
> - Terminology 强调准确、详细地描述临床概念。
> - Classification 强调把疾病或其他概念归入适合统计和报告的类别。

Identifier Code System（标识符编码系统）:为观察项目、药物、文档或其他数据元素提供稳定的标识符。

<img width="734" height="138" alt="Screenshot 2026-11-02 at 09 35 20" src="https://github.com/user-attachments/assets/0d77ac8a-fbf8-41c2-bf90-26487d8a9274" />

<img width="575" height="176" alt="Screenshot 2026-11-02 at 09 35 44" src="https://github.com/user-attachments/assets/e8a03c26-e17c-43ac-97d6-cdb21696ab3d" />

**Phenotype and computable phenotype**

Phenotype: An observable physical, biochemical, behavioural, or cognitive trait influenced by biological and environmental processes.
表型是指受到生物因素和环境因素共同影响的、可以观察到的身体、生化、行为或认知特征。

Computable Phenotype: A machine executable specification for identifying a condition or cohort from recorded data.
可计算表型是一套可以由计算机执行的规则，用于从已有记录数据中识别某种健康状况或特定研究人群。

<img width="758" height="349" alt="Screenshot 2026-11-02 at 09 37 55" src="https://github.com/user-attachments/assets/f4a8a4c6-f7b0-4c94-b362-066cb2cfb77b" />

Sensitivity and Specificity（敏感度与特异度）:Sensitivity and specificity depend on coding and measurement practices.
敏感度和特异度取决于疾病编码方式和测量实践。

Sensitivity: 在真正患病的人中，算法能够正确识别多少人？

<img width="506" height="190" alt="Screenshot 2026-11-02 at 09 39 36" src="https://github.com/user-attachments/assets/611c405f-8408-4504-9a65-63dbf6c3c6e3" />

Specificity: 在真正没有患病的人中，算法能够正确排除多少人？

<img width="240" height="87" alt="Screenshot 2026-11-02 at 09 39 54" src="https://github.com/user-attachments/assets/0b7a0cf4-fe4c-4736-87a5-8474f335743b" />

## From a question to an analytical table

**Unit of Analysis**

The unit of analysis is the entity about which the analysis draws conclusions. Independence is a separate modelling assumption that must be assessed from the study design and repeated measurement structure.

分析单位是指研究最终希望对其得出结论的对象。独立性是一个单独的统计建模假设，需要根据研究设计和重复测量结构进行评估。

<img width="619" height="121" alt="Screenshot 2026-11-02 at 09 47 20" src="https://github.com/user-attachments/assets/421e8635-d8aa-4128-b54c-550c8689e5b1" />

**Identifiers: labels are not automatically keys**
<img width="907" height="219" alt="Screenshot 2026-11-02 at 09 49 23" src="https://github.com/user-attachments/assets/86539d32-4412-43e7-9826-0664467c599e" />

*Primary key:* 主键是一个字段或字段组合，它必须在数据表中对每一行都是唯一的，并且不能缺失。
> [!IMPORTANT]
> Unique & Non-missing

*Foreign key:* 外键是指向另一张数据表中某个键的字段。
> [!IMPORTANT]
> 主要作用是：建立不同数据表之间的关系。

*Composite key:* 需要多个字段组合起来，才能唯一识别一条记录。

<img width="794" height="487" alt="Screenshot 2026-11-02 at 09 53 14" src="https://github.com/user-attachments/assets/6c1c55d3-10f0-4d89-93e0-877e4c4bb0d9" />

*Linkage key:* 用于连接不同数据来源中相关记录的稳定标识值。

它与 Foreign Key 有点相似，但重点不同。

Foreign Key 通常描述数据库表之间的引用关系。

Linkage Key 更强调跨不同数据源连接记录。

<img width="706" height="228" alt="Screenshot 2026-11-02 at 09 54 10" src="https://github.com/user-attachments/assets/eaa070db-777a-4abe-8f3e-54087d244404" />

**A safe join begins with a cardinality question**

<img width="439" height="195" alt="Screenshot 2026-11-02 at 09 56 39" src="https://github.com/user-attachments/assets/90ef330c-fe8f-4b20-80c1-3764ea533d12" />


**Data Provenance（数据溯源）**

Provenance records where data came from, how they were generated, and every material transformation applied before analysis.

数据溯源记录数据来自哪里、如何产生，以及在正式分析之前经历了哪些重要的数据转换。

<img width="637" height="506" alt="Screenshot 2026-11-02 at 10 15 00" src="https://github.com/user-attachments/assets/3613e3ec-dbcb-40b5-9168-bb4a9d585957" />

<img width="642" height="290" alt="Screenshot 2026-11-02 at 10 15 43" src="https://github.com/user-attachments/assets/dcd2ab36-ff3f-437d-b348-c84b48cdf35a" />


**FAIR Data Principles**

<img width="905" height="164" alt="Screenshot 2026-11-02 at 10 16 31" src="https://github.com/user-attachments/assets/c83b9d3b-fceb-4423-bfff-bd29cd1d01b5" />


## Cleaning and exploratory analysis

**Units and Plausibility**

<img width="505" height="89" alt="Screenshot 2026-11-02 at 10 29 41" src="https://github.com/user-attachments/assets/6bbe8c29-6587-4ade-b18b-fd7ec5d4a4b8" />

<img width="706" height="180" alt="Screenshot 2026-11-02 at 10 30 12" src="https://github.com/user-attachments/assets/e6d72b6f-9ab7-4c49-8c96-2b447fbae9a6" />

**Robust centre and spread**

<img width="468" height="147" alt="Screenshot 2026-11-02 at 10 31 19" src="https://github.com/user-attachments/assets/b93c2564-7d67-413d-af48-c7dbe809b974" />

> [!NOTE]
> 判断规则：
> - 低于 Lower fence → 潜在异常值。
> - 高于 Upper fence → 潜在异常值。
> - 位于两个界限之间 → 不会被这条规则标记。

**Outliers, anomalies, and influential observations**

<img width="902" height="192" alt="Screenshot 2026-11-02 at 10 33 24" src="https://github.com/user-attachments/assets/d55b62d1-c386-46d2-adba-e4f11de42803" />

**Gene expression before and after log2 transformation**

<img width="717" height="415" alt="Screenshot 2026-11-02 at 10 34 39" src="https://github.com/user-attachments/assets/416c441b-6c94-46cf-8d65-2b96f4033fed" />

> [!IMPORTANT}
> 少数特别大的表达值会拉长横坐标，并且可能主导可视化结果和距离计算。
> 对数转换改变的是基因表达数据的数值尺度，并不会创造新的生物学信息。

**Empirical cumulative distribution: reading quantiles（经验累积分布函数与分位数）**

<img width="483" height="154" alt="Screenshot 2026-11-02 at 10 36 30" src="https://github.com/user-attachments/assets/499d8b6c-5fc2-4266-8ced-e4647db40565" />

<img width="715" height="183" alt="Screenshot 2026-11-02 at 10 36 46" src="https://github.com/user-attachments/assets/277d8f89-f00c-42a9-8447-6b0b1a16d81b" />

<img width="410" height="257" alt="Screenshot 2026-11-02 at 10 37 34" src="https://github.com/user-attachments/assets/ad9f7026-2253-46f1-9a9a-e832e0ddc63b" />

ECDF shows the proportion of observations at or below each threshold, allowing us to read quantiles and compare entire distributions.

**Missing data: MCAR, MAR, and MNAR**

1. MCAR — Missing Completely At Random（完全随机缺失）:数据是否缺失，与已经观测到的数值以及未观测到的数值都无关。

2. MAR — Missing At Random（随机缺失）:缺失可能与已经观测到的变量有关，但在控制这些已观测变量后，不再依赖缺失值本身。

<img width="475" height="65" alt="Screenshot 2026-11-02 at 10 41 03" src="https://github.com/user-attachments/assets/991bd0ca-abc7-4f31-a201-6fbf14eb56a7" />

3. MNAR — Missing Not At Random（非随机缺失）:即使已经考虑其他观测变量，缺失概率仍然与缺失值本身有关。(e.g.:当检测值超过仪器的测量范围时，检测可能失败，因此特别高的数值更容易缺失。)

<img width="901" height="239" alt="Screenshot 2026-11-02 at 10 40 19" src="https://github.com/user-attachments/assets/4eacb7ca-af65-4340-8f59-7a69405757db" />

<img width="759" height="395" alt="Screenshot 2026-11-02 at 10 42 11" src="https://github.com/user-attachments/assets/61737bbd-4197-4055-adba-dc1b98fac612" />

**Handling missing data**

<img width="785" height="197" alt="Screenshot 2026-11-02 at 10 44 02" src="https://github.com/user-attachments/assets/be8b4513-6c86-43d6-a68d-48c0cdf5e0d2" />

> [!IMPORTANT]
> Imputation is a model, not clerical replacement.
> 插补是一种建模过程，而不是简单地把空白格填上数字。

**Imputation toolbox: from simple rules to models**

<img width="896" height="317" alt="Screenshot 2026-11-02 at 10 45 59" src="https://github.com/user-attachments/assets/946acb74-9bcb-4d21-a256-59adc3465d16" />

*利用时间信息插补：*

使用前一次观测值插补；使用下一次观测值插补；使用缺失值前后两个时间点的信息进行估计；平滑轨迹：不只是利用前后两个点，而是使用多个时间点的数据，估计整体变化趋势。

*利用相似记录：*

寻找与缺失记录相似的其他记录，利用它们的信息估计缺失值。

> [!IMPORTANT]
> Imputation should use the structure of the data; constants, time, similar records, and predictive models each make different assumptions.
> 插补应该利用数据本身的结构。使用固定值、时间信息、相似记录或预测模型，都意味着不同的统计假设。
> 例如：
> - 均值插补假设使用一个代表性中心值是合理的。
> - 时间插值假设相邻时间点之间存在可以利用的变化规律。
> - KNN 假设相似记录在目标变量上也可能相似。
> - 回归插补假设其他已观测变量可以预测缺失变量。
> 因此，没有一种插补方法永远是最好的。

> 需要根据数据结构、缺失机制和研究目标选择方法。

**Scaling variables: putting measurements on comparable scales（变量缩放：让不同变量处于可比较的尺度）**

Why scale: Large numerical ranges can dominate methods based on distances or variable magnitude.

<img width="449" height="226" alt="Screenshot 2026-11-02 at 10 51 47" src="https://github.com/user-attachments/assets/d11ed630-e537-4a59-9f42-2985f865206f" />

*Min-max normalisation 的目标是：把原始数据的最小值转换成 0，最大值转换成 1。*

**Using similar records or prediction models**

1. Nearest Neighbour Imputation（最近邻插补）

2. Regression or Machine Learning Imputation（回归或机器学习插补）

<img width="778" height="341" alt="Screenshot 2026-11-02 at 10 54 31" src="https://github.com/user-attachments/assets/de57dd2a-5d3e-49d9-bd9d-902b273c3fec" />

*Nearest Neighbour Imputation: Euclidean Distance*

*Regression or Machine Learning Imputation: 线性回归预测公式* 

Record based and model based imputation both estimate missing values conditionally on observed information.

基于相似记录的插补和基于模型的插补，都是利用已经观测到的信息，有条件地估计缺失值。

**KNN imputation: visual intuition**

> [!NOTE]
> KNN; meaning k nearest neighbours; imputes a missing value by looking for observations that are most similar on the variables that are already observed.
> 它通过寻找在已观测变量上最相似的其他记录，来填补缺失值。

<img width="485" height="432" alt="Screenshot 2026-11-02 at 11 02 52" src="https://github.com/user-attachments/assets/2cf90a9e-ea6e-4837-9a88-340f142da443" />

<img width="675" height="171" alt="Screenshot 2026-11-02 at 11 03 26" src="https://github.com/user-attachments/assets/6b56a5c8-a5d4-4ddd-a1f0-a0f2d2128865" />

**Bivariate visualisation: relationships**

<img width="896" height="188" alt="Screenshot 2026-11-02 at 11 05 42" src="https://github.com/user-attachments/assets/289bf6e2-1894-479f-b37d-af685fea47cb" />

**Pearson and Spearman correlation**

<img width="805" height="269" alt="Screenshot 2026-11-02 at 11 06 59" src="https://github.com/user-attachments/assets/ce9a1454-2bc4-442d-b0e1-20e5ae877c32" />

> [!NOTE]
> Pearson 用于衡量两个变量之间的线性关联。
> Spearman 用于衡量单调关系. *单调关系指：随着 X 增加，Y 总体上持续增加，或者持续减少。但这种关系不一定是一条直线。*


**Correlation**

<img width="773" height="307" alt="Screenshot 2026-11-02 at 11 09 42" src="https://github.com/user-attachments/assets/eb1da27a-c49f-4a73-9646-c29be4d6b1e9" />

> [!NOTE]
> 特点一：对角线永远是 1
> 
> 特点二：矩阵是对称的
> A correlation matrix summarises pairwise relationships between multiple variables, but it does not establish causation or account automatically for repeated measurements.
> 
> 相关矩阵用于同时展示多个变量之间的两两相关关系，但不能证明因果，也不会自动处理重复测量的依赖性。

**Introduction to PCA (Dimension Reduction)**

*What is PCA?* Multivariate dimensionality reduction: Noise / Redundancy.

PCA 是一种多变量降维方法，目的是通过新的变量组合减少数据中的冗余表示，并帮助我们理解数据的主要变化结构。

<img width="352" height="199" alt="Screenshot 2026-11-02 at 11 27 35" src="https://github.com/user-attachments/assets/13bd0207-42d0-46b5-a592-34fd8f37d145" />

<img width="639" height="253" alt="Screenshot 2026-11-02 at 11 28 34" src="https://github.com/user-attachments/assets/44d6ce25-11b0-4444-99f5-ed60124fc325" />

> [!NOTE]
> PCA 会寻找：
> - PC1：数据变异最大的方向。
> - PC2：与 PC1 正交，并且在剩余方向中变异最大的方向。
> - PC3：与前两个方向正交，继续寻找剩余的主要变异方向。

<img width="767" height="518" alt="Screenshot 2026-11-02 at 11 32 40" src="https://github.com/user-attachments/assets/20267ee3-82b2-4d7a-bbe6-a145d2dfeb68" />

<img width="914" height="297" alt="Screenshot 2026-11-02 at 11 36 14" src="https://github.com/user-attachments/assets/7b9a786d-fb9a-412e-8026-40f2da8a59fd" />

**Variance and Covariance**

<img width="820" height="417" alt="Screenshot 2026-11-02 at 11 39 07" src="https://github.com/user-attachments/assets/496e3576-8a3d-4199-b521-3fe5bf35a308" />

- Positive covariance：两个变量倾向于同向变化。
- Negative covariance：两个变量倾向于反向变化。
- Covariance near zero：两个变量没有明显的线性共同变化。

<img width="151" height="60" alt="Screenshot 2026-11-02 at 11 42 39" src="https://github.com/user-attachments/assets/6d4a6b10-aaed-49cf-86e3-6b7c14bd67a3" /> <img width="249" height="65" alt="Screenshot 2026-11-02 at 11 42 19" src="https://github.com/user-attachments/assets/878c3e10-fd49-47ba-9a8a-6a2e16bfdeec" /> <img width="334" height="79" alt="Screenshot 2026-11-02 at 11 43 26" src="https://github.com/user-attachments/assets/6e20fa01-165a-421a-a223-a64db89eebba" />

<img width="317" height="286" alt="Screenshot 2026-11-02 at 11 43 54" src="https://github.com/user-attachments/assets/aedac362-f689-47a0-aceb-ec9fd11a67b5" />

**From a transpose product to the covariance matrix（从矩阵转置乘法推导协方差矩阵）**

<img width="676" height="426" alt="Screenshot 2026-11-02 at 11 45 22" src="https://github.com/user-attachments/assets/f93243b5-6b8d-4d26-8356-c95742fb4843" />

<img width="751" height="240" alt="Screenshot 2026-11-02 at 11 45 56" src="https://github.com/user-attachments/assets/e1a9ca43-d26b-4c13-9150-00bf028a3ad1" />

> [!IMPORTANT]
> Diagonal（对角线）→ Variance
> Off-diagonal（非对角线）→ Covariance

**Eigenvectors & Eigenvalues（特征向量与特征值）**

<img width="912" height="380" alt="Screenshot 2026-11-02 at 11 47 45" src="https://github.com/user-attachments/assets/8efd2fc9-e8df-47a6-a3fe-7e46cef1ca02" />

> [!NOTE]
> Eigenvector 是在矩阵变换下仍保持其所在方向轴线的特殊向量，决定方向。
> Eigenvalue（特征值）：在 PCA 中表示对应方向的方差。

**Eigen Decomposition（特征值分解）**

<img width="749" height="478" alt="Screenshot 2026-11-02 at 11 51 02" src="https://github.com/user-attachments/assets/b7ff70b3-4e92-4d85-a95a-663c8398f578" />

<img width="908" height="399" alt="Screenshot 2026-11-02 at 11 51 27" src="https://github.com/user-attachments/assets/25e25e38-9e64-4ed0-866b-8e7a0ef79bed" />

> [!NOTE]
> 1. U：Eigenvector matrix（特征向量矩阵）
> 2. Σ：Eigenvalue matrix（特征值对角矩阵）非对角线是0，特征值排列在对角线上。
> 3. \(U^T\)：特征向量矩阵的转置
> Eigen decomposition allows PCA to rotate the original data into a new coordinate system where the principal components are uncorrelated and ordered by variance.
> 特征值分解让 PCA 将原始数据转换到新的坐标系，使主成分之间不相关，并按照方差大小排列。


**Leakage**

*Definition:* Information from evaluation data enters model development, directly or indirectly, producing optimistic performance estimates.

评估数据中的信息直接或间接进入模型开发过程，导致模型性能评估过于乐观。

> [!WARNING]
> 举个简单例子:
> 假设我们训练一个模型预测患者是否会死亡。
> 如果模型训练时已经知道了测试患者的死亡结果，那么预测当然可能非常准确。
> 但这并不能证明模型真正具有预测能力。
> 因为现实中，我们需要在患者结局发生之前进行预测。
> *这就是 Leakage 的危险：模型看起来表现很好，但实际上利用了不应该知道的信息。*

<img width="742" height="148" alt="Screenshot 2026-11-02 at 11 58 45" src="https://github.com/user-attachments/assets/ee478b72-8d59-4c89-abf2-c37173ffcfd9" />

**EDA**

*Definition:* The iterative use of summaries and visualisations to understand structure, quality, relationships, and anomalies before formal modelling.

在正式建模之前，通过反复使用统计汇总和可视化，理解数据的结构、质量、变量关系和异常情况。

> [!NOTE]
> Step 1：Ask a precise question（提出一个明确的问题）
> 
> Step 2：Choose a representation that can answer it（选择能够回答问题的表示方式）
> 
> Step 3：Inspect the result for signal and artefact（检查结果中的真实信号与人为假象）
> 
> *EDA 的任务之一，就是区分 Signal 和 Artefact。*
> 
> Step 4：Revise the question or data transformation（修正问题或数据转换方式）
> 
> Step 5：Document what changed and why（记录修改内容及原因）
>
> **必要时重新提出问题，开始下一轮 EDA**


## Privacy, Bias, and reproducibility

**Personal and special category data（个人数据与特殊类别数据）**

<img width="894" height="294" alt="Screenshot 2026-11-02 at 13 17 41" src="https://github.com/user-attachments/assets/6fe015fd-a59b-41b9-a713-ea3d71624bf1" />

> [!NOTE]
>
> 个人数据是指与已经被识别或能够被识别的在世自然人有关的信息。*（个人数据不一定需要包含姓名）*
>
> 健康数据和基因数据在 UK GDPR 下受到额外保护。当生物识别数据被用于唯一识别某个人时，也属于特殊类别数据。
>
> <img width="734" height="192" alt="Screenshot 2026-11-02 at 13 19 36" src="https://github.com/user-attachments/assets/74d0509e-ee2f-4133-93fa-d006d0ab4882" />
>
> 处理个人数据，需要具有并记录 UK GDPR 第 6 条规定的合法依据。
>
> 处理特殊类别个人数据，还需要满足 UK GDPR 第 9 条规定的条件。

**Anonymisation, pseudonymisation, and disclosure control（匿名化、假名化与信息披露控制）**

<img width="900" height="301" alt="Screenshot 2026-11-02 at 13 22 50" src="https://github.com/user-attachments/assets/220ca493-6e6a-41bb-a03a-7a2b8ef53502" />

1. *Anonymisation（匿名化）:* 在具体使用环境中，通过合理可能使用的识别手段，已经无法识别数据对应的个人。
> [!IMPORTANT]
> 
> 有效匿名化的信息不再属于 UK GDPR 所保护的个人数据。

2. *Pseudonymisation（假名化）:* 用其他标识符替换直接身份信息，同时另外保存受到保护的关联信息，使数据在必要时仍可以重新关联到个人。
> [!IMPORTANT]
> 
> 假名化数据仍然属于个人数据，需要遵守 UK GDPR。

<img width="671" height="236" alt="Screenshot 2026-11-02 at 13 25 29" src="https://github.com/user-attachments/assets/436c7b10-bf72-43a9-9544-5b9cfff0f564" />

3. *Masking（掩码处理）:* 例如原始电话号码07123456789， masking后07123******；原始姓名：Alice Smith，masking后A**** S****。
4. *Generalisation（泛化）:* 降低数据的精确程度，例如使用年龄分组或更广泛的地理区域。
5. *Date shifting（日期偏移）:* 修改准确日期，同时在适当情况下保留事件的相对顺序。
6. *Tokenisation（令牌化）:* 使用稳定的随机令牌替换标识符。


**k-anonymity（k-匿名性）**

A quasi-identifier is a variable combination that may identify people when linked to external information.

准标识符是指某些变量或变量组合，在与外部信息结合时，可能用于识别个人身份。

<img width="493" height="520" alt="Screenshot 2026-11-02 at 13 35 20" src="https://github.com/user-attachments/assets/3fb3b5e8-dda0-4962-aec4-0e9ddf97b500" />

Quasi-identifiers are not necessarily direct identifiers, but their combinations may enable re-identification.

> [!IMPORTANT]
> Direct identifier：例如姓名、NHS Number，可以直接识别个人。
> 
> Quasi-identifier：例如年龄和地区，可能通过组合或外部信息识别个人。

An equivalence class is a set of records sharing the same quasi-identifier values.

等价类是指在选定的准标识符上，具有完全相同取值的一组记录。

<img width="784" height="308" alt="Screenshot 2026-11-02 at 13 37 47" src="https://github.com/user-attachments/assets/1d12f117-3d31-4ccc-91e0-e91df2932860" />

<img width="747" height="314" alt="Screenshot 2026-11-02 at 13 38 34" src="https://github.com/user-attachments/assets/91d4931d-107f-4031-8717-8c6ffae53d86" />

*k-anonymity 的正式定义：* Every equivalence class contains at least k records, so each record is indistinguishable from at least k−1 others on the selected quasi-identifiers.

每个等价类都必须至少包含 k 条记录，使得每条记录在选定的准标识符上，至少与另外 k−1 条记录无法区分。

<img width="782" height="733" alt="Screenshot 2026-11-02 at 13 40 13" src="https://github.com/user-attachments/assets/eabb63dc-f35d-4668-9b44-57cd4448caf7" />

<img width="803" height="93" alt="Screenshot 2026-11-02 at 13 41 03" src="https://github.com/user-attachments/assets/83ab0e6b-fe38-481f-81ed-f4fcfd94e8a7" />

**ℓ-diversity addresses attribute homogeneity（ℓ-多样性：解决敏感属性同质性问题）**

<img width="918" height="373" alt="Screenshot 2026-11-02 at 13 44 16" src="https://github.com/user-attachments/assets/e9fe6b57-2da3-449b-945a-04f0f2cc0a65" />

*Attribute homogeneity（敏感属性同质性）:* 三个人的 Disease 都是 HIV。

如果有人知道某个人属于这个等价类，虽然不知道他对应 A、B、C 中的哪一条记录，却仍然可以推断出他的疾病是 HIV。

Attribute homogeneity（敏感属性同质性）意思是：同一个等价类中的敏感属性过于相似，甚至完全相同。

> [!NOTE]
> Quasi-identifiers 用于分组；Sensitive attributes 是我们不希望被轻易推断的信息。
>
> 在 distinct ℓ-diversity 的定义下，每个等价类必须至少包含 ℓ 个不同的敏感属性取值。

<img width="787" height="729" alt="Screenshot 2026-11-02 at 13 47 49" src="https://github.com/user-attachments/assets/6795b7fb-ec35-438c-b464-3a2a42ad8c4b" />

<img width="641" height="217" alt="Screenshot 2026-11-02 at 13 48 34" src="https://github.com/user-attachments/assets/94e31ef9-d985-421f-9e2b-9a6524038e38" />

**Health data governance: beyond GDPR compliance（健康数据治理：超越 GDPR 合规）**

<img width="867" height="418" alt="Screenshot 2026-11-02 at 13 53 59" src="https://github.com/user-attachments/assets/0184c99d-6d97-4a86-9855-765c9a988809" />

<img width="763" height="210" alt="Screenshot 2026-11-02 at 13 54 12" src="https://github.com/user-attachments/assets/b8039d1a-a7e6-41a8-8c97-0c8116b24e50" />

**Bias**

1. Population and access → Selection bias
2. Measurement → Measurement bias
3. Target and proxy → Label or proxy bias
4. Deployment → Allocation and feedback bias

*Selection bias（选择偏差）*

假设我们想研究某种疾病在全国人口中的发生情况。

但我们的数据只来自医院。

这意味着：
- 去医院就诊的人可能进入数据集。
- 没有医疗服务可及性的人可能无法进入数据集。
- 症状较轻、没有就诊的人可能没有记录。
因此，医院数据不一定代表全国人口。
举个例子
假设某地区有 1,000 名居民：
- 600 人居住在城市。
- 400 人居住在农村。
但研究数据中：
- 90% 来自城市患者。
- 10% 来自农村患者。
这意味着农村人口在数据中代表性不足（Underrepresentation）。

如果我们直接用这些数据训练模型，模型可能更适合城市患者。

Measurement bias（测量偏差）

假设两家医院测量同一种生物标志物。

医院 A 使用经过校准的仪器。

医院 B 使用存在系统性偏差的仪器。

真实乳酸浓度为：3 mmol/L

但医院 B 的仪器总是测得：4 mmol/L

那么医院 B 的记录就存在系统性测量偏差。

这可能让模型错误地认为医院 B 的患者乳酸浓度普遍更高。

医疗数据中的另一个例子
假设：
- 严重患者每天测量乳酸。
- 病情较轻的患者每周测量一次。
那么两组患者的测量频率不同。

这种测量过程差异可能影响数据的完整性、分布和后续模型结果。

这也联系到前面学习的 Missing data（缺失数据）。

*重点：即使数据已经成功记录，也不代表它能无偏地反映真实健康状况。*

<img width="748" height="252" alt="Screenshot 2026-11-02 at 14 05 09" src="https://github.com/user-attachments/assets/4e949893-e2b5-4849-a9ca-18cdeab510e9" />

<img width="821" height="397" alt="Screenshot 2026-11-02 at 14 11 19" src="https://github.com/user-attachments/assets/a164f820-9a7d-4879-99d5-1fee596c9e81" />

Feedback bias（反馈偏差）

假设模型认为某类患者风险较低，因此减少对他们的检查。

结果：
1. 这些患者接受的检查更少。
2. 医疗系统记录到的疾病更少。
3. 下一轮训练数据中，这类患者的疾病记录仍然偏少。
4. 新模型继续认为他们风险较低。

<img width="787" height="181" alt="Screenshot 2026-11-02 at 14 16 22" src="https://github.com/user-attachments/assets/9d8bb67d-de6e-45e8-9ea9-e785f35aa87c" />

A race blind or group blind model can remain biased because inequity is encoded in outcomes, proxies, and measurement processes.

即使模型不直接使用种族或群体身份变量，仍然可能存在偏差，因为不平等可能已经体现在结局变量、代理变量和测量过程中。

<img width="724" height="468" alt="Screenshot 2026-11-02 at 14 25 00" src="https://github.com/user-attachments/assets/8fb24d9e-e214-4927-bac0-97130ad55b6b" />

> [!IMPORTANT]
> 不使用群体身份 ≠ 没有偏差。
>
> 例如，模型不使用 Ethnicity，但使用 Postcode，而 Postcode 可能间接反映群体身份或社会经济差异。

**Data justice in global health（全球健康中的数据正义）**

<img width="904" height="327" alt="Screenshot 2026-11-02 at 14 29 11" src="https://github.com/user-attachments/assets/c864b6bb-515e-4bb1-a2d9-7641364ef386" />

*Representation and authority（代表性与决策权）:* 哪些群体被数据代表？谁定义研究问题？谁控制数据访问、数据关联以及可接受的二次使用？


1. Representation（代表性）

假设某国际研究团队研究全球糖尿病风险, 但是数据来源主要是高收入国家。

那么：
- 高收入国家患者被充分代表。
- 低收入国家患者可能代表性不足。
即使模型在已有数据中表现很好，也不一定适合全球所有人群。


2. Authority（决策权）

例如：

某个非洲国家的医院向国际研究项目提供了医疗数据。但所有研究问题、分析方法和后续数据使用决定都由国外研究团队制定,当地机构没有参与决策。

>[!IMPORTANT]
>
> Representation concerns who is included; authority concerns who controls decisions about the data.

*Capacity and credit（能力建设与贡献认可）:* 谁拥有分析和治理数据所需的基础设施、技能、领导权和作者署名机会？

1. Capacity（能力）

某个低收入国家的医院提供了大量患者数据。

但当地医院缺乏：
- 数据分析基础设施。
- 统计软件和计算资源。
- 专业数据科学人员。
- 独立开展研究的机会。

如果国际合作只提取当地数据，却不帮助提升当地研究能力，就可能造成长期的不平等。

Capacity building（能力建设）可以包括培训、技术支持和研究基础设施建设。

2. Credit（贡献认可）

Credit 关注研究贡献是否获得适当认可。

例如：

当地研究人员参与了数据收集、研究设计和结果解释。

但最后发表论文时，他们没有得到与贡献相符的署名或认可。

这就涉及研究中的公平性。

这里有一个重要术语：

Authorship（论文作者署名）


*Participation and accountability（参与和问责）:* 受到研究影响的社区，能否参与并影响研究设计、结果解释、模型部署，以及对潜在伤害的纠正？

1. Participation（参与）

假设研究人员开发一个模型，决定哪些患者优先获得医疗资源。

如果研究设计完全由技术团队决定，而患者和受影响社区没有参与，那么研究可能忽略一些重要问题。

例如：
- 模型使用的指标是否符合当地医疗实际？
- 某些人群是否会被不公平地排除？
- 预测结果应该如何解释？

因此，受影响群体的参与可能帮助研究团队发现原本没有注意到的问题。

2. Accountability（问责）

假设模型部署后，某些患者群体持续被低估疾病风险。

谁来负责？
- 是否有人监测模型表现？
- 患者能否提出异议？
- 是否有纠正错误的机制？
- 是否能够调整或停止有害的部署？

这就是 Accountability。

*Benefit Sharing:* 研究产生的健康收益、知识、基础设施和经济价值，是否回馈给提供数据的人群？

某国际研究项目使用一个低收入国家的患者数据，开发出新的疾病预测工具。

研究完成后：
- 国际研究团队发表高水平论文。
- 科技公司获得商业收益。
- 但当地医院无法使用该工具。
- 当地患者也没有获得明显的健康改善。

这就涉及 Benefit sharing 的问题。

<img width="597" height="270" alt="Screenshot 2026-11-02 at 14 34 19" src="https://github.com/user-attachments/assets/03d6ea64-966d-45fd-b8f6-7c50885e6aa4" />





























