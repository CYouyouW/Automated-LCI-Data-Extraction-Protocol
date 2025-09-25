# 自动化 LCI 数据抽取
💫本仓库提供一个面向 Ecoinvent 等数据库的自动化数据抽取与矩阵构建工具。它可以直接处理原生 EcoSpold v2 (`.spold`) 文件，无需商业软件，自动完成解析、清洗与标准化，最终生成稀疏的“流 × 过程”矩阵。

借助此工作流，研究人员可以：

高效抽取整合 LCI 数据，规避手工处理的复杂度与易错性；

得到包含数万条过程与流的高质量数值矩阵；

保留丰富文本信息，为语义建模和机器学习任务提供支撑；

为缺失数据预测和自动化 LCA 分析建立扎实的数据基础。



# 输入与输出
**输入**
- Ecoinvent 3.11 APOS 版本的 EcoSpold v2 `.spold` 数据集（放入 `data/spold/`，或使用环境变量 `ECOSPOLD_ROOT` 指向其他目录）。
- `FilenameToActivityLookup.csv`（分号分隔），用于把文件前缀映射到活动名称与地区（默认查找 `data/FilenameToActivityLookup.csv`，可通过 `FILENAME_LOOKUP` 覆盖）。
- `batch_number.txt`（批次自增计数），默认在 `outputs/` 自动创建，可通过 `LCA_BATCH_FILE` 指向自定义路径。

**输出**
每次运行会创建一个带时间戳的批次文件夹（`<output_root>/<MMDD>_<batch_number>/`），其中包含：
- 每个 `.spold` 文件对应的清洗后 CSV，文件名与原始 `.spold` 一致；
- 日志与诊断文件：`processing_debug.txt`、`summary.txt`、`failed_files.txt`、`non1_amount_files.csv`、`neg1_amount_files.csv`；
- `global_activity_mapping.csv`，记录全部发现的活动 ID。

`build_lca_matrix` 辅助脚本会将这些 CSV 汇总成稀疏的“流 × 过程”矩阵，并写入 `LCA_MATRIX_TARGET`（默认仍为当前批次目录）。

### 环境变量
- `ECOSPOLD_ROOT` — 原始 `.spold` 文件目录（默认 `data/spold/`）。
- `FILENAME_LOOKUP` — 映射表路径（默认 `data/FilenameToActivityLookup.csv`）。
- `LCA_OUTPUT_ROOT` — 批次输出的父目录（默认 `outputs/`）。
- `LCA_BATCH_FILE` — 批次计数文件的位置。
- `LCA_MATRIX_SOURCE`/`LCA_MATRIX_TARGET` — 控制矩阵构建所用的输入/输出路径。
- `COMPARE_DIR1`/`COMPARE_DIR2` — 使用目录比对工具时需要设置的批次目录。


# 📝运行
## ⛏️安装
建议使用虚拟环境。
```
git clone https://github.com/CYouyouW/Automated-LCI-Data-Extraction-Protocol.git
cd Automated-LCI-Data-Extraction-Protocol
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

## ▶️ 执行流程
1. 将授权的 `.spold` 文件放入 `data/spold/`（或设置 `ECOSPOLD_ROOT`）。
2. 将 `FilenameToActivityLookup.csv` 复制到 `data/`（或设置 `FILENAME_LOOKUP`）。
3. 启动笔记本（`JUPYTER_CONFIG_DIR=. jupyter lab`），按顺序运行 `Automated_LCI_Data_Extraction_Protocol.ipynb`。
4. 在 `outputs/` 中查看新生成的批次文件夹，核对 CSV、日志与诊断结果。
5. （可选）通过设置 `LCA_MATRIX_SOURCE`/`LCA_MATRIX_TARGET` 重新运行矩阵构建，以便汇总指定批次。


# 💐贡献指南
- **报告缺陷**：在 GitHub [Issues](https://github.com/CYouyouW/Automated-LCI-Data-Extraction-Protocol/issues) 中提交。
- **提出改进**：无论是新增功能还是小幅优化，也请使用 Issues 讨论。
- **提交 PR**：欢迎提交修复、改进或示例，记得附上验证步骤。
- **提出问题**：如需使用帮助，可在 GitHub 讨论区发帖。


# 🤗引用
💥若本仓库对您有所帮助，请引用我们的论文：SemaNet: Bridging Words and Numbers For Predicting Missing Environmental Data in Life Cycle Assessment. DOI: https://doi.org/10.1021/acs.est.5c07557
