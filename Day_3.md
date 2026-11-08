# Machine learning for complex and high dimensional biomedical data

**Feature Selection（特征选择）**

<img width="887" height="345" alt="Screenshot 2026-11-07 at 21 07 13" src="https://github.com/user-attachments/assets/2b4d23c0-a673-4b3e-9f8d-af48dde9e8a7" />

特征选择是从原始预测变量中保留一部分变量。

<img width="774" height="136" alt="Screenshot 2026-11-07 at 21 08 20" src="https://github.com/user-attachments/assets/67896849-8716-4859-8286-643485996215" />

<img width="766" height="678" alt="Screenshot 2026-11-07 at 21 13 03" src="https://github.com/user-attachments/assets/83c5f56f-23d1-4837-84bd-8f09b55a8b11" />

<img width="773" height="424" alt="Screenshot 2026-11-07 at 21 13 18" src="https://github.com/user-attachments/assets/b570d125-83fe-4abe-85c6-27012425156f" />

**Selection using Random Forest importance**

<img width="899" height="330" alt="Screenshot 2026-11-07 at 21 14 35" src="https://github.com/user-attachments/assets/a226f01a-a2b2-40a6-9f65-ae5efab85cc5" />

1. Impurity Importance（不纯度重要性）

统计某个特征在树的分裂过程中带来的节点纯度改善，并在所有树之间进行汇总和平均。

<img width="769" height="459" alt="Screenshot 2026-11-07 at 21 22 58" src="https://github.com/user-attachments/assets/cc06a1e6-b111-4db5-b658-6b70ec304082" />

2. Permutation Importance（置换重要性）

随机打乱某个特征的取值，观察模型预测表现下降多少，并且不重新训练模型。

<img width="771" height="560" alt="Screenshot 2026-11-07 at 21 26 47" src="https://github.com/user-attachments/assets/763f2503-9aed-43da-8561-2e379c07f3b3" />

<img width="751" height="175" alt="Screenshot 2026-11-07 at 21 27 19" src="https://github.com/user-attachments/assets/2cd38218-f96b-4025-82c4-fd503885e169" />

**Wrapper methods: RFE and sequential selection 包装式特征选择方法——递归特征消除与序列特征选择**

<img width="897" height="421" alt="Screenshot 2026-11-07 at 21 57 16" src="https://github.com/user-attachments/assets/25135fe0-b160-4a84-bdd0-2065d3114403" />

1. RFE（Recursive Feature Elimination）：递归特征消除。
2. Sequential Selection：序列特征选择，包括 Forward Selection 和 Backward Selection。

<img width="558" height="392" alt="Screenshot 2026-11-07 at 22 03 31" src="https://github.com/user-attachments/assets/0a75989b-4365-483e-930a-d88ca50492b8" />

<img width="779" height="369" alt="Screenshot 2026-11-07 at 22 08 30" src="https://github.com/user-attachments/assets/138a4542-6caf-427b-94e5-191e9862807c" />

> [!TIP]
>
> Forward Selection 从没有任何特征开始，每次增加一个最有用的特征。
>
> Backward Selection 从全部特征开始，每次尝试删除一个特征，比较删除哪一个之后模型表现最好。

<img width="696" height="228" alt="Screenshot 2026-11-07 at 22 10 33" src="https://github.com/user-attachments/assets/3a927422-831d-4b92-9b24-d55a5fa22cd5" />

**Embedded selection through regularisation**

<img width="896" height="360" alt="Screenshot 2026-11-07 at 22 22 48" src="https://github.com/user-attachments/assets/20f2afa4-32cb-4d12-b51b-42ea6a238f32" />

Regularisation 是在模型训练过程中，对预测变量的权重（系数）施加惩罚。

Regularisation 的作用就是：在追求预测效果的同时，限制系数的大小，避免模型过度复杂。

<img width="790" height="136" alt="Screenshot 2026-11-07 at 22 29 32" src="https://github.com/user-attachments/assets/b2a2a3f5-c80f-4147-a711-8a6f411db8e0" />

> [!NOTE]
>
> 1. Lasso（L1 Regularisation）：Lasso 使用系数绝对值的和作为惩罚。
> 
> <img width="515" height="209" alt="Screenshot 2026-11-07 at 22 44 33" src="https://github.com/user-attachments/assets/ac0a996c-fd2e-443c-ae61-2d0fc6b3713c" />
>
> <img width="493" height="425" alt="Screenshot 2026-11-07 at 22 35 44" src="https://github.com/user-attachments/assets/b414deaa-a404-4817-a80f-9dc8d44cc8e7" />
>
> 2. Ridge（L2 Regularisation）：Ridge 使用系数平方之和作为惩罚。
>
> <img width="238" height="70" alt="Screenshot 2026-11-07 at 22 44 56" src="https://github.com/user-attachments/assets/86144b80-2683-4335-9927-847218dd1211" />
>
> 经过 Ridge 后，系数整体变小，但通常仍然不等于 0。
>
> 所以 Ridge 的主要作用是 Shrinkage（系数收缩），而不是直接删除变量，这意味着 Ridge 一般不会像 Lasso 那样产生稀疏的特征集合。
>
> 3. Elastic Net（L1 + L2）：Elastic Net 结合了 Lasso 和 Ridge 的惩罚方式。
>
> <img width="329" height="32" alt="Screenshot 2026-11-07 at 22 46 39" src="https://github.com/user-attachments/assets/38cb0950-c31d-4654-8d61-8002b2c2ff39" />
>
> 它同时具备两方面的优势：
> - L1 部分：可以让一些系数变为 0，实现 Feature Selection。
> - L2 部分：帮助稳定相关特征的系数，并可能让相关基因一起保留。

在应用 regularisation 之前，使用训练数据对预测变量进行 standardisation 。

<img width="556" height="234" alt="Screenshot 2026-11-07 at 22 53 30" src="https://github.com/user-attachments/assets/79de1f33-5efd-45cd-b447-0c2ed374174d" />

**Validation of feature selection 特征选择的验证**

The selection procedure is part of the model being evaluated.

特征选择过程本身就是被评估模型的一部分。

> [!NOTE]
>
> Step 1：Split cell lines into training, validation and test before selecting genes.
>
> 在选择基因之前，先将细胞系划分为 Training、Validation 和 Test。
> 
> Step 2：Check that expression values are finite in all three partitions.
>
> 检查三个数据集中的基因表达值是否都是有限数值（Finite Values）。
>
> Step 3：If enabled, run RFE only within training and give both classifiers its selected genes.
>
> 如果启用 RFE，那么只允许在 Training Set 内执行 RFE。
>
> Step 4：Fit the classifiers on training; use validation to choose penalty strength or boosting rounds.
>
> 使用 Training Set 训练模型，使用 Validation Set 选择模型设置。
>
> Step 5：Fix the complete procedure before assessing the test predictions.
>
> 在使用 Test Set 评估之前，固定完整的建模流程。

**Multiclass classification requires one probability per class**

<img width="914" height="342" alt="Screenshot 2026-11-08 at 14 05 46" src="https://github.com/user-attachments/assets/0a09c654-65a7-42ce-a178-7ba4614faabc" />

*One-versus-Rest（OvR）:* 为每个类别分别训练一个二分类器，预测概率可能需要额外校准或归一化。

OvR 有什么问题？

因为四个模型是分别训练的，所以它们输出的概率不一定加起来等于 1。

*Multinomial Model（多项分类模型）:* 同时拟合所有类别，并通过 Softmax 直接产生一个符合概率规则的分布。

<img width="776" height="211" alt="Screenshot 2026-11-08 at 14 20 44" src="https://github.com/user-attachments/assets/60de57d3-5b17-4e94-b7a4-c75d90faaa41" />

**Deriving softmax from class log odds**

<img width="913" height="415" alt="Screenshot 2026-11-08 at 14 22 49" src="https://github.com/user-attachments/assets/9200166c-c04a-4617-862b-b49a1f5104fc" />

<img width="473" height="158" alt="Screenshot 2026-11-08 at 14 26 37" src="https://github.com/user-attachments/assets/970c6f47-c209-4d3f-8696-b7fb028c4cfd" />

> [!IMPORTANT]
>
> Softmax 的四个重要性质:
>
> 性质 1：指数运算使所有数值变为正数。
>
> 性质 2：除以所有指数值的总和，使概率归一化。
>
> 性质 3：给所有类别的分数同时加上同一个常数，不会改变 Softmax 概率。
>
> 性质 4：原始分数最高的类别，Softmax 概率也最高。Softmax 改变了分数的数值尺度，但不会改变类别的排名。

**Deriving multiclass cross-entropy from likelihood**

<img width="910" height="367" alt="Screenshot 2026-11-08 at 14 51 55" src="https://github.com/user-attachments/assets/9661a426-4810-4486-87db-1a64cdd24d6d" />

> [!NOTE]
>
> Cross-Entropy 是一种 Loss Function（损失函数），用于衡量模型预测的概率与真实类别之间的差异。
> - 模型给真实类别的概率越高，Cross-Entropy 越小。
> - 模型给真实类别的概率越低，Cross-Entropy 越大。
> - Cross-Entropy 越小，代表模型的概率预测表现越好。

<img width="867" height="404" alt="Screenshot 2026-11-08 at 15 12 34" src="https://github.com/user-attachments/assets/6c51be98-7727-44b9-a3b2-874a9efcf1a9" />

Cross-Entropy 在训练过程中评价预测概率的质量，而 Accuracy 只评价最终选择的类别是否正确。

**Why high dimensional models need regularisation**

<img width="858" height="301" alt="Screenshot 2026-11-08 at 15 14 34" src="https://github.com/user-attachments/assets/c6ba0168-28cf-4dcf-9f82-07a7776e521f" />

























































































































































