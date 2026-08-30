# SEU-HEM-W23 – 混合励磁电机 FEM 优化数据集  
# SEU-HEM-W23 – FEM-based Optimization Dataset for Hybrid Excitation Motor

---

## 项目简介 | Project Introduction

**中文**  
本数据集包含 **27,957 个样本**，来源于混合励磁电机（Hybrid Excitation Motor）设计优化过程中，基于有限元（FEM）仿真获得的性能数据。  
该数据集用于评估不同深度神经网络（DNN）在根据电机截面预测关键性能指标（KPI）任务上的表现。  
详细研究请参考论文：  
> *"The Application of Attention Mechanism in Topology Optimization for Motor Design"*, ICEMS 2026.

本仓库提供的数据集与论文中使用的 **SEU-HEM-W23** 数据集完全一致。

**English**  
This dataset contains **27,957 samples**, obtained during the FEM-based design optimization process of a hybrid excitation motor.  
It is designed to evaluate various deep neural networks (DNNs) on the task of predicting key performance indicators (KPIs) from the motor cross‑section.  
For more details, please refer to the paper:  
> *"The Application of Attention Mechanism in Topology Optimization for Motor Design"*, ICEMS 2026.

The dataset provided in this repository is identical to the **SEU-HEM-W23** dataset used in the paper.

---

## 文件说明 | File Description

**中文**  
- **`Topo_Data_23.csv`**：主数据文件，包含 27,957 行，每行 25 个数值字段（**无表头行**）。

**English**  
- **`Topo_Data_23.csv`**：Main data file with 27,957 rows, each containing 25 numerical fields (**no header row**).

---

## 数据字段说明 | Data Field Description

**中文**  
每个样本包含 **25 个元素**，具体含义如下：

| 字段编号 | 字段名称（建议） | 取值范围 | 描述 |
| :---: | :--- | :---: | :--- |
| 1 – 23 | `omega_1` ~ `omega_23` | [-1, 1] | NGnet 网络权重向量的 23 个分量，表示电机截面的拓扑特征 |
| 24 | `torque_avg` | 浮点数 | 对应设计下的平均转矩（单位：N·m） |
| 25 | `torque_ripple` | 浮点数 | 对应设计下的转矩脉动（单位：N·m） |

> **注意**：CSV 文件中不包含列名（header），每行按上述顺序直接存储 25 个数值。若需读取，可使用 `pandas.read_csv('Topo_Data_23.csv', header=None)`。

**English**  
Each sample consists of **25 elements**, with the following meanings:

| Field Index | Suggested Name | Range | Description |
| :---: | :--- | :---: | :--- |
| 1 – 23 | `omega_1` ~ `omega_23` | [-1, 1] | The 23 components of the NGnet weight vector, representing topological features of the motor cross‑section |
| 24 | `torque_avg` | float | Average torque corresponding to the given design (unit: N·m) |
| 25 | `torque_ripple` | float | Torque ripple corresponding to the given design (unit: N·m) |

> **Note**: The CSV file does **not** contain a header row. Each row stores the 25 numeric values in the order listed above. Use `pandas.read_csv('Topo_Data_23.csv', header=None)` to load it.

---

## 快速加载示例（Python）| Quick Loading Example (Python)

```python
import pandas as pd
import numpy as np

# 读取数据（无列名） | Load data (no header)
df = pd.read_csv('Topo_Data_23.csv', header=None)

# 分别提取特征和标签 | Extract features and labels
X = df.iloc[:, :23].values   # 前23列为omega权重 | first 23 columns are omega weights
y_torque = df.iloc[:, 23].values    # 第24列为平均转矩 | column 24 is average torque
y_ripple = df.iloc[:, 24].values    # 第25列为转矩脉动 | column 25 is torque ripple

print(f"数据形状 | Data shape: {df.shape}")
print("前5个样本的前3个omega分量 | First 5 samples, first 3 omega components:\n", X[:5, :3])

```

---

## 引用与许可 | Citation and License

**中文**  
如果你在研究中使用本数据集，请引用以下论文：

```bibtex
@inproceedings{Bao2026,
  title     = {The Application of Attention Mechanism in Topology Optimization for Motor Design},
  booktitle = {2026 29th International Conference on Electrical Machines and Systems (ICEMS)},
  author    = {Bao, Liwen and Du, Yunlu and Peng, Fei and Huang, Yunkai and Yao, Yu},
  year      = {2026}
}
```

本数据集仅供学术研究使用，任何商业用途请联系作者。

**English**

If you use this dataset in your research, please cite the following paper:

```bibtex
@inproceedings{Bao2026,
  title = {The Application of Attention Mechanism in Topology Optimization for Motor Design},
  booktitle = {2026 29th International Conference on Electrical Machines and Systems (ICEMS)},
  author = {Bao, Liwen and Du, Yunlu and Peng, Fei and Huang, Yunkai and Yao, Yu},
  year = {2026}
}
```

This dataset is provided for academic research purposes only. For commercial use, please contact the authors.

---

## 原始数据来源 | Original Data Source

**中文**

数据集最初托管于 GitLab（东南大学）, https://gitlab.seu.edu.cn/230238791/to_hem_w23.git 

本仓库为 GitHub 镜像，方便国际用户获取。

**English**

The dataset was originally hosted on GitLab (Southeast University), https://gitlab.seu.edu.cn/230238791/to_hem_w23.git 

This repository is a GitHub mirror for easier access by international users.
