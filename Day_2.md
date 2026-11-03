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


























