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
































