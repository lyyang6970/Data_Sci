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











































































































































































