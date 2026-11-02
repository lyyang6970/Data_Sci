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















