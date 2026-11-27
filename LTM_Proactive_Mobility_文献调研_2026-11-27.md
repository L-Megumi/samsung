# L1/L2-triggered mobility 与 Proactive Mobility Management 文献调研

检索截止与重整日期：2026-11-27。重点年份：2023—2026；同一工作的预印本、作者稿与正式发表版本合并记录。

本版逐篇列出研究工作、方法步骤、实验结果、正文核验位置和原文版本；两条方向仍分别调研。29 篇主清单论文的原文 PDF 已全部收录，另附 1 篇技术文章、1 篇降级参考和 1 份规范，共 32 份原始 PDF。

## 范围与结果

按两条独立主线整理，不要求论文同时包含 LTM 和主动移动性管理。

- **方向 A：L1/L2-triggered mobility（含 C-LTM）**：保留 6 篇已核对正文的机制、建模或优化论文。
- **方向 B：Proactive mobility management**：保留 16 篇已核对正文的预测式切换、参数优化或主动资源管理论文；不要求使用 LTM。
- **预测支撑**：3 篇，明确区分预测任务与完整切换验证。
- **综述及标准化进展**：4 篇。
- 合计 **29 篇已核对正文并保留的论文**；另附 1 篇厂商技术文章、8 条待取得正文/确认版本的线索，以及 2 篇审读后降级的论文。

“正文已核验”指取得论文 PDF 或完整正文，逐篇检查研究对象、方法/流程、实验设置与结果，并记录可定位的章节、图表或 PDF 页码；不表示已复现作者实验。下列数字均来自论文报告，不是本次复测结果。不同论文的 HOF、RLF、时延、资源预留指标口径不一，不直接据此横向排名。

## 检索与纳入方法

分别执行六组检索，并沿核心论文的参考文献、作者机构主页和正式出版记录补查。聚合站用于发现线索；技术判断回到论文正文、作者稿、出版社或标准原文。

| 检索组 | 检索式及扩展词 | 本报告对应条目 |
|---|---|---|
| LTM | “L1/L2-triggered mobility”; “L1/L2 triggered mobility”; “lower layer mobility”; “L1/L2 inter-cell mobility” | A01—A06、T01、U01—U03 |
| C-LTM | “C-LTM”; “CLTM”; “conditional LTM”; “conditional lower-layer triggered mobility” | A02、A03、A04；规范 N01 |
| Predictive Handover | “predictive handover”; “prediction-based handover”; “early-scheduled handover” | B01—B07、B10—B16 等 |
| Proactive Mobility | “proactive mobility”; “proactive mobility management”; “proactive handover” | A05、B01—B16、U04—U05 |
| Mobility Prediction | “mobility prediction” + handover/next-cell/trajectory; “next-cell prediction” | B02、B07、B10—B12、P01—P03、U06 |
| AI-enabled Mobility Management | “AI-enabled mobility management”; “AI-driven mobility management”; “AI/ML” + mobility management | B03—B10、B12—B14、S01—S04 |

纳入方向 A 的依据是：正文实际描述、建模或评估低层触发的小区切换。仅在引言提到 LTM 不足以归入 A。纳入方向 B 的依据是：未来位置、信号、事件、连接持续时间或风险信息被用于提前准备、决策、执行切换或配置资源；预测论文若尚未评估切换控制，则列为支撑。

## 概念边界

| 概念 | 判断要点 |
|---|---|
| LTM | 重点是候选配置、早期同步和 MAC CE 小区切换命令等机制。现行规范允许网络利用 L1 或 L3 测量报告；“输入用了 L1-RSRP”本身不能证明实现了 LTM。 |
| C-LTM / CLTM | UE 按预配置的 L1/L3 执行条件自主触发 LTM 小区切换。条件触发本身不要求预测器或 AI。 |
| Proactive / predictive mobility | 重点是提前多久知道什么，以及据此提前做什么；可以采用传统 L3 切换、CHO 或另行设计的流程。 |
| AI-enabled mobility | 范围包括预测、参数优化、关联及资源控制。需要另查是否实际使用未来信息；例如 A06 是直接研究 LTM 的 AI 优化论文，但并未显式预测未来信道。 |
| Mobility prediction | 下一小区、轨迹或事件预测是移动性管理的输入。分类准确率不能直接解释为切换成功率。 |

## 方法总览

下表只压缩方法与验证类型；具体输入、控制动作和实验条件见后面的逐篇说明。A05 横跨两方向，仍只计数一次。

### 方向 A LTM 与 C-LTM

| 编号 | 年份 | 研究对象 | 主要方法 | 控制动作或用途 | 验证类型 |
|---|---|---|---|---|---|
| [A01](#a01) | 2023 | L1 测量与候选配置 | L2 IIR 滤波及动态配置保留 | 低层触发及后续切换 | 系统级仿真 |
| [A02](#a02) | 2024 | 测量报告与条件执行 | 预配置 早期同步 MAC CE 条件触发 | LTM 和 conditional LTM | 机制分析及系统级仿真 |
| [A03](#a03) | 2026 | Rel-19 协议增强与 TCP | 协议流程分析及 TCP 对照仿真 | inter-CU LTM CLTM 早期 CSI | 标准机制及系统级仿真 |
| [A04](#a04) | 2026 | 星内波束与星间切换 | C-LTM 与 BHO 或 CHO 的混合机制 | 星内条件执行及星间切换 | NTN 系统级仿真 |
| [A05](#a05) | 2025 | 未来 L1 与 L3 SINR | 未来窗口上的准备及执行条件 | 准备 执行 替换 释放 | 完美未来信息下的系统仿真 |
| [A06](#a06) | 2026 | 关联 PRB 候选资源预留 | INLP 松弛上界及带动作掩码的 PPO | 服务关联 分配 候选准备 | 优化上界及多规模仿真 |

### 方向 B Proactive 与 Predictive Mobility

| 编号 | 年份 | 研究对象 | 主要方法 | 控制动作或用途 | 验证类型 |
|---|---|---|---|---|---|
| [B01](#b01) | 2024 | A3 entry criterion 的到达时间 | TCN 时间回归及 ESHOP 调度 | 提前准备切换 | 信道及切换流程仿真 |
| [B02](#b02) | 2025 | 未来位置 信道及 RB 需求 | LSTM GAP 近似及启发式资源分配 | 主动关联及 RB 分配 | SUMO 与无线网络联合仿真 |
| [B03](#b03) | 2025 | 未来切换结果类型 | XGBoost 与扩展 DQN | 动态 TTT 与 HOM | 分类及闭环参数仿真 |
| [B04](#b04) | 2025 | 波束状态与未来 L3 RSRP | 压缩测量 ConvLSTM CNN 或 LSTM | 测量压缩及主动小区切换 | QuaDRiGa 信道及切换仿真 |
| [B05](#b05) | 2025 | RSRQ 趋势与目标选择 | DQN 及多智能体 DQN | 预连接及目标侧缓存 | NS-3 与 NS3-Gym 联合仿真 |
| [B06](#b06) | 2026 | 跨小区未来 RSRP | 波束自适应嵌入及选择性微调 GPT-2 | 提前准备及双模式执行 | 信道仿真 HOF 及 GPU 推理计时 |
| [B07](#b07) | 2026 | 未来窗口稳定服务 BS | 编码器 LSTM 解码器及迁移学习 | 减少不稳定目标选择 | 多拓扑仿真 |
| [B08](#b08) | 2024 | 未来服务与邻近 RSRP | 多层 LSTM FedAvg 误差感知门限 | 动态切换触发阈值 | 离线预测及规则比较 |
| [B09](#b09) | 2025 | 多维 KPI 与运动状态 | LSTM FedAvg 近端正则及可行性规则 | 候选排序及受约束 HO | OAI Open5GS FlexRIC 软件测试床 |
| [B10](#b10) | 2025 | 未来窗口的 HO 事件 | LSTM 二分类及成本感知资源策略 | 提前购买或配置覆盖资源 | 商业 O-RAN 测量及成本评估 |
| [B11](#b11) | 2024 | 下一小区 | 轨迹图像编码 CNN 及 I-DPBMA | 预测驱动的带宽预留 | 地图覆盖及资源仿真 |
| [B12](#b12) | 2026 | 未来 cell ID 序列及 RB 需求 | AR-LSTM 或 AR-GRU 二进制编码 | 避开不可用候选及资源预留 | SUMO 及真实 GPS 加覆盖仿真 |
| [B13](#b13) | 2024 | 遮挡状态与发生时间 | 雷达特征 双输出网络及联邦学习 | 遮挡前预切换 | 真实感知数据及射线追踪仿真 |
| [B14](#b14) | 2026 | TN 与 NTN 的未来 RSRP | CNN LSTM 编解码及 QMIX | 协同选择未来目标和时机 | MATLAB 星地融合网络仿真 |
| [B15](#b15) | 2026 | 星历 未来链路与负载 | 预测计划 交替优化及动态规划 | 提前计划及定时执行 | 软件原型及星历驱动仿真 |
| [B16](#b16) | 2026 | 未来遮挡及链路质量 | 前瞻价值界 雷达追踪及成本感知规划 | 不确定性下的主动切换 | 射线追踪及误差敏感性仿真 |

### Mobility Prediction 预测支撑

| 编号 | 年份 | 研究对象 | 主要方法 | 控制动作或用途 | 验证类型 |
|---|---|---|---|---|---|
| [P01](#p01) | 2024 | 未来轨迹 下一 BS 到达时刻 | 轨迹插值 K-means 原型及在线匹配 | 提供准备时机输入 | 车辆轨迹与覆盖模型 预测指标 |
| [P02](#p02) | 2025 | UE 与 cell 的潜在连接 | VGAE 与 SEAL 图链路预测 | 为 O-RAN 候选选择提供输入 | 连接分类及运行开销 |
| [P03](#p03) | 2025 | 轨迹及代理 HO 事件 | GRU Reptile EWMA 触发的持续学习 | 预测器在线适应 | GPS 及无线代理数据 预测指标 |

### AI-enabled Mobility 综述与标准化

| 编号 | 年份 | 研究对象 | 主要方法 | 控制动作或用途 | 验证类型 |
|---|---|---|---|---|---|
| [S01](#s01) | 2025 | AI 移动性方法与场景 | 分类综述及技术比较 | 组织相关工作 | 综述 无独立控制实验 |
| [S02](#s02) | 2026 | 预测 决策 执行 反馈生命周期 | 全生命周期分类综述 | 组织 AI 管理框架 | 综述 无独立控制实验 |
| [S03](#s03) | 2025 | RRM 测量值及事件预测 | 标准化技术梳理与问题分析 | 厘清预测接口与研究路线 | 标准化进展综述 |
| [S04](#s04) | 2026 | ML 切换优化文献 | PRISMA 式系统综述及方法分类 | 追踪证据与研究缺口 | 系统综述 |

## 方向 A LTM 与 C-LTM 逐篇说明

<a id="a01"></a>

### A01 — On the Modelling and Performance Analysis of Lower Layer Mobility in 5G-Advanced

- **作者/发表**：Alperen Gündogan, Akın Badalıoglu, Panagiotis Spapis, Ahmad Awada；IEEE WCNC 2023。预印本首发 2022，按正式会议年份列入。
- **文献**：[DOI: 10.1109/WCNC55385.2023.10118691](https://doi.org/10.1109/WCNC55385.2023.10118691)；[作者公开稿](https://arxiv.org/pdf/2211.02725)。
- **核验位置**：正文低层移动性模型、L2 filtering / dynamic switching；§5、表 1—2、图 3—6；§6 结论。公开稿 PDF 第 4—9 页。

**研究工作**：针对低层切换响应快、但容易乒乓和重复准备的问题，建立统一的 lower-layer mobility 模型，量化低层触发、滤波和候选配置保留分别带来的收益与代价。

**采用的方法**：

1. 在同一测量、波束选择与无线链路模型中实现 BHO、CHO、CHO-L1 和低层移动性 LLM，使触发层次、准备及执行时间可以对照。
2. 在低层测量之后加入 L2 IIR 滤波，得到 LLM-F，以减小瞬时信号波动引起的切换。
3. 进一步提出 LLM-F-DS：完成一次切换后保留仍然可用的候选配置，支持后续动态切换，减少重新准备。

**实验与主要结果**：28 GHz、7 站点三扇区、420 UE、60 km/h 系统级仿真；同时统计链路问题、失败、乒乓、准备率和预留资源。L2 滤波使乒乓降低约 28%，可靠性未受损；动态保留配置进一步减少准备，但资源预留明显增加。

**相关性与适用条件**：直接属于方向 A。表 2 把 LLM 中断设为 1 ms，属于模型输入；不能将其表述为商用网络实测中断。LLM 在此指 lower-layer mobility。

**已收录原文**：arXiv 预印本 v1（2022），对应 WCNC 2023 工作，9 页。包内路径：`01_LTM_C-LTM/A01_2023_Lower_Layer_Mobility_Model.pdf`；[原始下载入口](https://arxiv.org/pdf/2211.02725)。

<a id="a02"></a>

### A02 — On L1/L2-Triggered Mobility in 3GPP Release 18 and Beyond

- **作者/发表**：Behnam Khodapanah, Sanjay Goyal, Murat Gursu, Jedrzej Stanczak, Anastasios Kakkavas, Recep Temelli, Akin Badalioglu, Panagiotis Spapis, Chitradeep Majumdar；IEEE Access 12, 171790—171806，2024-11-05 在线。
- **文献**：[DOI: 10.1109/ACCESS.2024.3491500](https://doi.org/10.1109/ACCESS.2024.3491500)；[公开全文](https://www.researchgate.net/publication/385586453_On_L1L2-Triggered_Mobility_in_3GPP_Release_18_and_Beyond)。
- **核验位置**：§II-A—D、§II-E；§III-B/C，图 8—10；附录 A 仿真参数。

**研究工作**：解释 Rel-18 LTM 怎样缩短切换中断，并研究低层测量带来的鲁棒性、乒乓和报告开销；还实际评估了条件式 LTM。

**采用的方法**：

1. 将流程分为候选准备、提前下行同步/上行 TA 获取及执行；提前下发和解码候选配置，执行阶段用轻量 MAC CE 触发小区切换。
2. 用 L1 测量提高对信道恶化的响应速度，并对事件式测量报告与周期报告作比较。
3. 加入 UE 按 L1 或 L3 条件自主执行的 conditional LTM，与网络触发 LTM、CHO 对照，分析条件与滤波的影响。

**实验与主要结果**：正文系统级仿真分别检查中断、RLF、切换次数与报告量。LTM 降低中断和链路失效，但可能增加不必要切换；事件式报告用于缓解报告负担。图 10 包含条件式 LTM 的结果。

**相关性与适用条件**：方向 A 的核心入口。其 Rel-19 内容反映 2024 年的增强提议；最终规范限制应结合 A03 和 N01。它是机制解释与性能评估论文，并未提出学习式预测器。

**已收录原文**：出版正式版，作者公开上传，17 页。包内路径：`01_LTM_C-LTM/A02_2024_LTM_Rel18_and_Beyond.pdf`；[原始下载入口](https://www.researchgate.net/publication/385586453_On_L1L2-Triggered_Mobility_in_3GPP_Release_18_and_Beyond/fulltext/6a55feee7fcc0765f3e81fb1/On-L1-L2-Triggered-Mobility-in-3GPP-Release-18-and-Beyond.pdf)。

<a id="a03"></a>

### A03 — Evolution of Layer1/Layer2-Triggered Mobility in 5G-Advanced: From Release 18 Foundation to Release 19 Enhancements and Beyond

- **作者/发表**：Dogukan Atik, Behnam Khodapanah, Sanjay Goyal, Murat Gursu, Jedrzej Stanczak, Anastasios Kakkavas, Jani-Pekka Kainulainen；IEEE Access 14, 76649—76674，2026-05-18 在线。
- **文献**：[DOI: 10.1109/ACCESS.2026.3694552](https://doi.org/10.1109/ACCESS.2026.3694552)；[公开全文](https://www.researchgate.net/publication/404989506_Evolution_of_Layer1Layer2-Triggered_Mobility_in_5G-Advanced_From_Release_18_Foundation_to_Release_19_Enhancements_and_Beyond)。
- **核验位置**：§II，尤其 §II-F “Conditional LTM”与图 8；§IV、附录 A 的 TCP 仿真。

**研究工作**：将 LTM 的研究范围从 Rel-18 的 intra-CU 基础扩展到 Rel-19 的 inter-CU、条件执行和测量增强，并分析切换中断如何传导至 TCP 吞吐。

**采用的方法**：

1. 分解 inter-CU LTM 所需的信令、安全密钥更新、双连接和 CSI 资源协调，说明新场景增加的协议条件。
2. 分别讨论 CSI-RS L1-RSRP、事件式报告、早期 CSI 获取和 CLTM；CLTM 由 UE 按预置条件执行，后续切换可利用保留配置。
3. 建立含 TCP Reno/CUBIC 的仿真，在相同业务条件下改变切换中断和 TCP 重传超时参数，观察端到端吞吐。

**实验与主要结果**：§IV 比较约 20 ms 的 LTM 中断与约 100 ms 的传统切换中断；当 TCP RTO 为 100 ms 或更小时，缩短中断的吞吐收益更明显。文章的主要贡献是标准机制梳理与跨层性能分析。

**相关性与适用条件**：直接属于方向 A。正文的 inter-CU LTM 与其描述的 intra-CU CLTM 需要分别引用，不能把前者的适用范围自动赋给后者。

**已收录原文**：出版正式版，作者公开上传，26 页。包内路径：`01_LTM_C-LTM/A03_2026_LTM_Rel19_Evolution.pdf`；[原始下载入口](https://www.researchgate.net/publication/404989506_Evolution_of_Layer1Layer2-Triggered_Mobility_in_5G-Advanced_From_Release_18_Foundation_to_Release_19_Enhancements_and_Beyond/fulltext/6a56336c5816bf0fc235bc74/Evolution-of-Layer1-Layer2-Triggered-Mobility-in-5G-Advanced-From-Release-18-Foundation-to-Release-19-Enhancements-and-Beyond.pdf)。

<a id="a04"></a>

### A04 — Performance Evaluation of L1/L2-Triggered Mobility in Non-Terrestrial Networks

- **作者/发表**：Gyoungmin Been, Byungju Lim, Junsu Kim, Nameseok Ko；IEEE Access 14, 117256—117271，2026-07-24 在线。
- **文献**：[DOI: 10.1109/ACCESS.2026.3716680](https://doi.org/10.1109/ACCESS.2026.3716680)；[公开作者稿](https://www.researchgate.net/publication/410805760_Performance_Evaluation_of_L1L2-Triggered_Mobility_in_Non-Terrestrial_Networks)。
- **核验位置**：流程比较图 2、NTN 模型及仿真设置；性能评估 §C、图 5—10，尤其报告周期/滤波分析。

**研究工作**：研究地球移动小区的 LEO NTN 中，LTM/C-LTM 能否改善波束和卫星切换，以及更快触发是否造成短驻留和无效切换。

**采用的方法**：

1. 构造多卫星、多波束的 EMC 网络与相应传播、测量和处理时延模型。
2. 对比 BHO、CHO、standalone LTM，并设计 C-LTM+BHO 和 C-LTM+CHO：星内由 C-LTM 执行，星间使用 BHO 或 CHO。
3. 扫描 L1 报告周期、L1 滤波等参数，联合评价无线链路失效、切换中断和 unnecessary handover。

**实验与主要结果**：7 卫星、每星 19 波束的仿真；一组设置采用 20 ms L1 报告周期和 5 个样本的 L1 滤波。LTM/混合条件式方案改善 RLF 与过程级中断，同时增加短驻留和不必要切换，参数之间存在取舍。

**相关性与适用条件**：直接属于方向 A，特别适合 NTN 子方向；其收益依赖 EMC 与星内/星间流程，不能直接外推到所有地面或 NTN 部署。

**已收录原文**：公开作者稿，首页 DOI 栏未填写，16 页。包内路径：`01_LTM_C-LTM/A04_2026_LTM_in_NTN.pdf`；[原始下载入口](https://www.researchgate.net/publication/410805760_Performance_Evaluation_of_L1L2-Triggered_Mobility_in_Non-Terrestrial_Networks/fulltext/6a64dc1c6ab5412809c9d616/Performance-Evaluation-of-L1-L2-Triggered-Mobility-in-Non-Terrestrial-Networks.pdf)。

<a id="a05"></a>

### A05 — Proactive Low Level Mobility in Cellular Networks

- **作者/发表**：Anna Prado, Aaron Jakumar, Serkut Ayvasik, Fidan Mehmeti, Wolfgang Kellerer；IEEE WCNC 2025。
- **文献**：[DOI: 10.1109/WCNC61545.2025.10978543](https://doi.org/10.1109/WCNC61545.2025.10978543)；[作者机构 PDF](https://mediatum.ub.tum.de/doc/1771208/rnb35dhg0u1hwopcaw9nos77t.Proactive_Low_Level_Mobility_in_Cellular_Networks_WCNC-FINAL.pdf)。
- **核验位置**：§IV 的准备、执行、替换/释放条件；§V-A—C、图 3—6；§VI。

**研究工作**：把未来信道信息接入 LTM 的准备和执行两个阶段，减少候选准备、预留及频繁切换，并与 proactive CHO 对比。

**采用的方法**：

1. 使用未来窗口内的 L3-SINR 判断目标是否持续优于服务小区，满足准备偏置后才准备候选。
2. 执行时结合当前 L1 测量与未来 L1-SINR，要求优势在执行窗口内保持；同时更新候选的替换和释放条件。
3. 构造 PLTM 与 PCHO，分别比较只预测准备以及同时优化准备和执行，并扫描 200、300、400、500 ms 窗口。

**实验与主要结果**：4 BS、20 UE 的室内工厂仿真。500 ms 配置下，PLTM 相对 LTM 的准备率降低约 76%、切换率降低约 72%，总吞吐略增；只优化准备阶段收益有限。

**相关性与适用条件**：同时直接关联 A/B，但只计一次。§V 明确假设未来 500 ms 信道完全已知；该实验展示未来信息的潜力，没有训练和验证一个含预测误差的信道预测器。

**已收录原文**：机构公开会议作者稿，6 页。包内路径：`01_LTM_C-LTM/A05_2025_Proactive_Low_Level_Mobility.pdf`；[原始下载入口](https://mediatum.ub.tum.de/doc/1771208/rnb35dhg0u1hwopcaw9nos77t.Proactive_Low_Level_Mobility_in_Cellular_Networks_WCNC-FINAL.pdf)。

<a id="a06"></a>

### A06 — Max-Min Fair Mobility Management with Minimum Resource Reservation in 5G

- **作者/发表**：Anna Prado, Susanne Stöckeler, Wolfgang Kellerer, Fidan Mehmeti；IEEE INFOCOM 2026。
- **文献**：[DOI: 10.1109/INFOCOM59046.2026.11571357](https://doi.org/10.1109/INFOCOM59046.2026.11571357)；[作者上传全文](https://www.researchgate.net/publication/398431799_Max-Min_Fair_Mobility_Management_with_Minimum_Resource_Reservation_in_5G)；[机构发表记录](https://portal.fis.tum.de/de/publications/max-min-fair-mobility-management-with-minimum-resource-reservatio/)。
- **核验位置**：§III—V 的联合优化、松弛上界与 PPO；§VII 的规模及 action masking 实验。

**研究工作**：针对 LTM 候选准备会占用无线资源的问题，联合决定服务基站、PRB 分配和目标准备，在用户最差速率与资源预留之间取得平衡。

**采用的方法**：

1. 用整数非线性优化表示关联、PRB 和准备决策，目标考虑 max-min 用户速率与最小资源预留。
2. 将整数变量松弛，并用线性化及 McCormick 约束构造可求解的 LP 上界，作为策略性能参照。
3. 设计两阶段 PPO：先选服务 BS 和 PRB 数，再选是否及为哪个 BS 做准备；通过 action masking 排除容量不足、链路不可用等动作。

**实验与主要结果**：比较不同网络规模、松弛上界和动作约束版本；资源节约和最优性差距随规模变化。摘要中的约 60% 预留节约对应其特定对照，不能当作所有规模的统一收益。

**相关性与适用条件**：直接属于方向 A 的资源优化。输入主要是当前/历史 SINR 与资源状态，没有显式未来信道预测，因此单独不能证明预测式主动切换的收益。

**已收录原文**：公开会议作者稿，10 页。包内路径：`01_LTM_C-LTM/A06_2026_MaxMin_Fair_Mobility_Reservation.pdf`；[原始下载入口](https://www.researchgate.net/profile/Fidan-Mehmeti/publication/398431799_Max-Min_Fair_Mobility_Management_with_Minimum_Resource_Reservation_in_5G/links/69763ec5f5b9fd48849bdd8c/Max-Min-Fair-Mobility-Management-with-Minimum-Resource-Reservation-in-5G.pdf)。

## 方向 B Proactive 与 Predictive Mobility 逐篇说明

<a id="b01"></a>

### B01 — Early-Scheduled Handover Preparation in 5G NR Millimeter-Wave Systems

- **作者/发表**：Dino Pjanić, Alexandros Sopasakis, Andres Reial, Fredrik Tufvesson；IEEE Open Journal of the Communications Society 5，2024。
- **文献**：[DOI: 10.1109/OJCOMS.2024.3488594](https://doi.org/10.1109/OJCOMS.2024.3488594)；[PDF](https://arxiv.org/pdf/2411.09720)。
- **核验位置**：§II 仿真、§III ESHOP、§V ML、§VI 评估；PDF 第 4—11 页。

**研究工作**：减少传统 A3 切换中等待事件与准备串行进行造成的延迟，预测事件何时到来，让准备提前完成。

**采用的方法**：

1. 定义 TEF，即距离 A3 entry criterion 满足的剩余时间，将切换时机预测转化为时间序列回归。
2. 以历史波束测量为输入，用含因果卷积、膨胀卷积和残差结构的 TCN 预测 TEF，分别分析 LoS/NLoS 数据。
3. 将 TEF 接入 ESHOP：在常规 TTT 等待及准备之间安排重叠，使准备在真正需要切换时已完成。

**实验与主要结果**：在 5G NR mmWave 仿真中验证 TEF 预测误差及提前准备后的切换窗口和链路退化表现。它直接连接了预测事件时间与网络动作，而非只报告下一基站分类准确率。

**相关性与适用条件**：方向 B 高相关，适合作为事件时刻预测与提前准备基线；部署和信道设定较简化，TCN 实时开销还需结合目标硬件评估，未实现完整 Rel-18 LTM。

**已收录原文**：arXiv 公开稿，对应 OJCOMS 2024，13 页。包内路径：`02_Proactive_Mobility/B01_2024_Early_Scheduled_Handover_ESHOP.pdf`；[原始下载入口](https://arxiv.org/pdf/2411.09720)。

<a id="b02"></a>

### B02 — AEPHORA: AI/ML-Based Energy-Efficient Proactive Handover and Resource Allocation

- **作者/发表**：Bowen Xie, Sheng Zhou, Zhisheng Niu, Hao Wu, Cong Shi；IEEE ICC 2025, 6297—6303；预印本 2024。
- **文献**：[DOI: 10.1109/ICC52391.2025.11161541](https://doi.org/10.1109/ICC52391.2025.11161541)；[PDF](https://arxiv.org/pdf/2412.11491)。
- **核验位置**：§III 联合目标、§IV 与算法 1—3；§V、图 4；PDF 第 3—7 页。

**研究工作**：联合解决车辆主动切换和 RB 分配，利用未来位置/信道降低发射能耗，同时满足业务时延与可靠性要求。

**采用的方法**：

1. 历史多 BS 信道增益输入堆叠 LSTM 与全连接网络，输出下一 PHO 帧的二维车辆位置。
2. 把预测位置映射为期望信道增益，估算各 BS 满足 QoS 所需的最低 RB 数；将 BS 关联近似为 generalized assignment problem 并采用近似算法。
3. 联合能效切换调度与启发式实时资源分配，形成 AEPHORA；将关联层和细粒度 RB 分配分开处理。

**实验与主要结果**：1 宏站与 4 微站、SUMO 车辆轨迹仿真，并比较预测位置和真实位置两种输入。正文报告较低能耗以及较高负载下的 QoS 支持能力，能直接看到预测误差带来的性能差距。

**相关性与适用条件**：方向 B 高相关，适合预测与资源联合优化；核心验证是能耗、QoS 和负载能力，不能把这些结果改写成真实协议栈零中断。

**已收录原文**：arXiv 公开稿，对应 ICC 2025，7 页。包内路径：`02_Proactive_Mobility/B02_2025_AEPHORA.pdf`；[原始下载入口](https://arxiv.org/pdf/2412.11491)。

<a id="b03"></a>

### B03 — Proactive Handover Type Prediction and Parameter Optimization Based on Machine Learning

- **作者/发表**：Kai Sun, Qingfeng Han, Zongchang Yang, Wei Huang, Haijun Zhang, Victor C. M. Leung；IEEE Transactions on Wireless Communications 24(4), 3515—3528，2025。
- **文献**：[DOI: 10.1109/TWC.2025.3531702](https://doi.org/10.1109/TWC.2025.3531702)；[公开论文与代码仓库](https://github.com/HQF6800/HO)。
- **核验位置**：§III 分类器+DQN 架构；§IV-A—C、表 I—III、预测准确率与参数实验；所查 PDF 第 5—13 页。

**研究工作**：先预测切换会成功、乒乓、过早还是过晚，再动态优化 TTT 和 HOM，避免固定参数难以适应不同速度和网络密度的问题。

**采用的方法**：

1. 根据 UE/BS 位置、RSRP、SINR 等特征构造切换样本与四类标签 SHO、PPHO、TEHO、TLHO。
2. 采用 XGBoost 预测切换类型，并与其他分类器比较。
3. 把分类结果及环境状态接入扩展 DQN，选择 TTT/HOM 参数动作，通过后续切换结果和奖励更新控制策略。

**实验与主要结果**：在不同速度及 49/50/100 BS 的设置中，分别评价分类与参数控制。作者报告切换类型预测准确率 94.83%；最终控制效果另以乒乓和失败等指标衡量。

**相关性与适用条件**：方向 B 高相关，是结果风险预测与参数控制路线。公开仓库仅提供部分数据，不能默认其具备完整复现实验所需内容；分类准确率不是切换成功率。

**已收录原文**：作者代码仓库中的论文稿，首页模板年份不作为发表年，15 页。包内路径：`02_Proactive_Mobility/B03_2025_HO_Type_Prediction_and_DQN.pdf`；[原始下载入口](https://raw.githubusercontent.com/HQF6800/HO/main/Proactive%20Handover%20Type%20Prediction%20and%20Parameter%20Optimization%20Based%20on%20Machine%20Learning.pdf)。

<a id="b04"></a>

### B04 — AI-Driven Mobility Management for High-Speed Railway Communications: Compressed Measurements and Proactive Handover

- **作者/发表**：Wen Li, Wei Chen, Shiyue Wang, Yuanyuan Zhang, Michail Matthaiou, Bo Ai；IEEE Vehicular Technology Magazine 20(4), 84—94，2025。早期预印本题名为 “AI-Based Beam-Level and Cell-Level Mobility Management for High Speed Railway Communications”，不重复计数。
- **文献**：[DOI: 10.1109/MVT.2025.3579515](https://doi.org/10.1109/MVT.2025.3579515)；[PDF](https://arxiv.org/pdf/2407.04336)。
- **核验位置**：§II 波束测量；§III 的主动小区切换，尤其 §III-B/C、图 5、表 VI；PDF 第 5—8 页。

**研究工作**：面向高铁高速移动，减少波束测量开销，同时通过未来小区信号预测提前切换，兼顾波束级和小区级移动性。

**采用的方法**：

1. 波束级部分用压缩测量与 ConvLSTM 等时序学习恢复/追踪波束信息。
2. 小区级实验另以部分历史 L1-RSRP 为输入，比较 CNN/LSTM 对未来多小区 L3-RSRP 的预测。
3. 用预测信号支持主动准备/执行，改变测量的波束和小区范围，比较测量负担与 RLF。

**实验与主要结果**：基于 QuaDRiGa 的高速铁路场景；小区切换部分采用 6 个历史时点预测 4 个未来时点。表 VI 和相关结果说明部分测量方案可以节约约 50% 波束测量，并改善 RLF。

**相关性与适用条件**：方向 B 直接相关。两个层次的实验分开验证；使用 L1-RSRP 输入不构成 LTM 实现证据。早期预印本与正式题名合并为一篇，数据入口见原文链接。

**已收录原文**：arXiv v3（2025），对应 VTM 2025，9 页。包内路径：`02_Proactive_Mobility/B04_2025_HighSpeed_Railway_AI_Mobility.pdf`；[原始下载入口](https://arxiv.org/pdf/2407.04336)。

<a id="b05"></a>

### B05 — Pre-Connect Handover Management for 5G Networks Using Multi-Agent Deep Q-Networks

- **作者/发表**：Yao Wei, Chung-Horng Lung, Samuel Ajila, Ricardo Paredes Cabrera；IEEE Access 13, 176176—176197，2025-10-06 在线。
- **文献**：[DOI: 10.1109/ACCESS.2025.3618587](https://doi.org/10.1109/ACCESS.2025.3618587)；[公开作者稿](https://www.researchgate.net/publication/396260258_Pre-Connect_Handover_Management_for_5G_Networks_using_Multi-Agent_Deep_Q-Networks)。
- **核验位置**：§III PHO 流程与目标缓存、§IV DQN/MADRL、§V 实验。

**研究工作**：在服务链路恶化之前预连接目标基站，并提前缓存数据，减少传统切换中的业务中断及丢包。

**采用的方法**：

1. 利用 RSRQ 及其变化率判断链路趋势，将其纳入 DQN 的状态与目标 BS 选择。
2. 离线训练、在线选择目标，结合预连接信令和目标侧缓存形成 PHO 流程。
3. 针对多 UE 扩展为多智能体深度 Q 网络，在 NS-3/NS3-Gym 中评估协同控制、缓存与高速移动的影响。

**实验与主要结果**：正文比较不同速度、缓存和多用户场景。部分情况下预连接可比常规触发提前约 800—900 ms；论文还讨论训练成本、参数依赖以及数据缓存的额外开销。

**相关性与适用条件**：方向 B 直接相关。提前量是预连接触发的时间优势，不能写成中断时间；该方案主要学习提前动作和目标，不能直接等同于显式多步 RSRP 预测。

**已收录原文**：公开作者稿，首页含占位 DOI，22 页。包内路径：`02_Proactive_Mobility/B05_2025_PreConnect_MultiAgent_DQN.pdf`；[原始下载入口](https://www.researchgate.net/publication/396260258_Pre-Connect_Handover_Management_for_5G_Networks_using_Multi-Agent_Deep_Q-Networks/fulltext/68e4cb5e02d6215259b9c5d3/Pre-Connect-Handover-Management-for-5G-Networks-Using-Multi-Agent-Deep-Q-Networks.pdf)。

<a id="b06"></a>

### B06 — LLM–Empowered Wireless Channel Quality Prediction for Reliable Cell Handover

- **作者/发表**：Wen Li, Wei Chen, Bo Ai, Yuanyuan Zhang, Yao Peng, Michail Matthaiou；IEEE Wireless Communications，2026-05-28 Early Access。
- **文献**：[DOI: 10.1109/MWC.2026.3691074](https://doi.org/10.1109/MWC.2026.3691074)；[机构记录](https://pure.qub.ac.uk/en/publications/llmempowered-wireless-channel-quality-prediction-for-reliable-cel/)；[作者上传全文](https://www.researchgate.net/publication/404448943_LLM-empowered_wireless_channel_quality_prediction_for_reliable_cell_handover)。
- **核验位置**：§II 主动流程、§III beam-adaptive embedding/GPT-2、§IV 与表 I。

**研究工作**：将 GPT-2 用于跨小区信道质量预测，并把预测接入提前准备和自适应执行，以提高高速场景切换可靠性。

**采用的方法**：

1. beam-adaptive embedding 将不同输入波束配置的 RSRP 映射到统一表示，再输入 GPT-2。
2. 选择性微调 GPT-2 的前馈/归一化等部分参数，通过回归头输出未来服务及邻小区 RSRP；模型部署在源 BS。
3. 若预测 A3 将持续满足 TTT，先启动准备；执行分为等待真实 A3 验证与平稳信道下立即执行两种模式，平衡误预测和延迟。

**实验与主要结果**：QuaDRiGa、7 BS/21 扇区、30 GHz，覆盖 60/90/120/350 km/h。表 I 在 120 km/h 时，HOF 从反应式 48.33% 降至 30.15%。A40 单样本推理约 5.88 ms，不含 UE 上传历史测量的时延。

**相关性与适用条件**：方向 B 高相关，可对比轻量预测器与大模型。HOF 和硬件耗时对应指定模拟场景；文中是基于 RRC 的提前准备/执行设计，不能因输入 L1 测量就归为 LTM。

**已收录原文**：公开作者稿，对应 2026 Early Access，8 页。包内路径：`02_Proactive_Mobility/B06_2026_LLM_Channel_Prediction_Handover.pdf`；[原始下载入口](https://www.researchgate.net/profile/Michail-Matthaiou/publication/404448943_LLM-empowered_wireless_channel_quality_prediction_for_reliable_cell_handover/links/69f9dd47751e8801513ea8f0/LLM-Empowered-Wireless-Channel-Quality-Prediction-for-Reliable-Cell-Handover.pdf)。

<a id="b07"></a>

### B07 — A Deep and Transfer Learning Approach for Handover Management in O-RAN

- **作者/发表**：Ioannis Panitsas, Akrit Mudvari, Ali Maatouk, Leandros Tassiulas；IEEE WCNC 2026。arXiv 条目仍显示旧题 “Predictive Handover Strategy in 6G and Beyond: A Deep and Transfer Learning Approach”；合并为同一工作。
- **文献**：[DOI: 10.1109/WCNC65185.2026.11555653](https://doi.org/10.1109/WCNC65185.2026.11555653)；[作者 PDF](https://panitsasi.github.io/A_Deep_and_Transfer_Learning_Approach_for_Handover_Management_in_O_RAN.pdf)；[所核 arXiv v2](https://arxiv.org/pdf/2404.08113v2)。
- **核验位置**：§III 架构/标签构造、§IV 评估、图 2—4；PDF 第 3—6 页。

**研究工作**：预测未来一段时间内更稳定的服务 BS，并通过迁移学习适应新基站，减少追随瞬时最优信号造成的频繁切换。

**采用的方法**：

1. 把过去多基站测量输入编码器、堆叠 LSTM 和解码器，输出服务 BS 分类。
2. 标签不是瞬时信号最大基站，而是未来窗口内最常出现的关联 BS，以偏向稳定服务。
3. 构造兼容 O-RAN xApp/E2 测量和控制的架构；网络新增基站时，用迁移学习适配已有模型。

**实验与主要结果**：21/36/51 BS 的仿真统计预测准确率与 HO 次数。所核 v2 正文报告准确率超过 95%、HO 数降低约 13%—46.2%；迁移学习减少适配训练工作量。

**相关性与适用条件**：方向 B 直接相关。O-RAN 架构兼容是设计，不能改称真实 O-RAN 实网验证。旧版题名和摘要的 92% 不与新版正文数值混用。

**已收录原文**：arXiv v2，新题名版本，对应 WCNC 2026，6 页。包内路径：`02_Proactive_Mobility/B07_2026_Deep_Transfer_Learning_ORAN.pdf`；[原始下载入口](https://arxiv.org/pdf/2404.08113v2)。

<a id="b08"></a>

### B08 — Privacy-Preserving Handover Optimization Using Federated Learning and LSTM Networks

- **作者/发表**：Wei-Che Chien, Yu Huang, Bo-Yu Chang, Wu-Yuin Hwang；Sensors 24(20), 6685，2024-10-17。
- **文献**：[DOI 与全文](https://doi.org/10.3390/s24206685)。
- **核验位置**：§3.1—3.3、§4 实验与图表、§5。

**研究工作**：让分散客户端共同训练信号预测器，再利用未来信号与预测误差动态调整切换门限，减少集中收集原始数据。

**采用的方法**：

1. 客户端用多层 LSTM 预测服务 RSRP 和最强邻近 RSRP；NR-RSRP 在此表示邻近信号。
2. 用 FedAvg 按客户端数据聚合模型，比较同质/异质客户端及集中式方案。
3. 以预测值和 MAE 构造动态触发阈值，再与固定 Event A3 规则对比。

**实验与主要结果**：10 客户端设置，四层 LSTM 的单元数为 120/50/50/50；评价预测误差和相应切换规则表现，研究客户端差异的影响。证据主要来自数据驱动的离线分析。

**相关性与适用条件**：方向 B 直接相关于联邦预测与触发阈值。仅交换模型权重不等于已经证明差分隐私；文章没有完整真实蜂窝协议栈部署的证据。

**已收录原文**：出版正式版，18 页。包内路径：`02_Proactive_Mobility/B08_2024_Federated_LSTM_Handover.pdf`；[原始下载入口](https://www.mdpi.com/1424-8220/24/20/6685/pdf)。

<a id="b09"></a>

### B09 — A Federated Learning Framework for Inter-cell Handover Optimization in O-RAN

- **作者/发表**：Batuhan Akdogan, Ibrahim Hokelek, Hakan Ali Cirpan；IEEE ELECO 2025。
- **文献**：[DOI: 10.1109/ELECO69582.2025.11329342](https://doi.org/10.1109/ELECO69582.2025.11329342)；[会议公开 PDF](https://www.eleco.org.tr/ELECO2025/Eleco2025-Papers/75.pdf)。
- **核验位置**：§2—3 的三个 xApp 与预测/执行约束；§4、表 1—2；PDF 第 2—5 页。

**研究工作**：在 O-RAN 软件测试床中构建联邦学习驱动的主动切换控制，同时考虑 UE 运动、无线质量与业务负载。

**采用的方法**：

1. Metrics Collector 采集吞吐、抖动、丢包、RSRP、速度、方向和路径损耗趋势等多维特征。
2. FL Predictor 用 LSTM 训练本地模型，局部目标加入偏离全局权重的二次约束，再用 FedAvg 聚合。
3. 预测器给候选 UE 排序；HO Handler 仅在目标 RSRP 增益、目标 SNR 和切换间隔等约束满足后执行，避免只凭模型输出盲切。

**实验与主要结果**：OAI、Open5GS、FlexRIC，2 gNB、20 个仿真移动 UE、约 1000 s 运行。所核 ELECO 2025 稿报告 HO 成功率超过 94%，时延中位数约 8.1 ms、90 分位约 10.3 ms。

**相关性与适用条件**：方向 B 直接相关，具有软件协议栈控制证据，UE 运动仍由仿真生成。U08 的 WCNC 2026 正文尚未取得，不能把本稿数值当作新版结果。

**已收录原文**：ELECO 2025 会议公开稿，非 WCNC 2026 新版，5 页。包内路径：`02_Proactive_Mobility/B09_2025_Federated_InterCell_ORAN_ELECO.pdf`；[原始下载入口](https://www.eleco.org.tr/ELECO2025/Eleco2025-Papers/75.pdf)。

<a id="b10"></a>

### B10 — ML-Based Handover Prediction Over a Real O-RAN Deployment Using RAN Intelligent Controller

- **作者/发表**：Merim Dzaferagic, Bruno Missi Xavier, Diarmuid Collins, Vince D’Onofrio, Magnos Martinello, Marco Ruffini；IEEE Transactions on Network and Service Management 22(1), 635—647，2025；预印本 2024。
- **文献**：[DOI: 10.1109/TNSM.2024.3468910](https://doi.org/10.1109/TNSM.2024.3468910)；[全文预印本](https://arxiv.org/pdf/2404.19671)；[作者机构发表记录](https://publications.scss.tcd.ie/RSS/publications.php?PME_sys_fl=0&PME_sys_fm=0&PME_sys_qfn=&PME_sys_sfn%5B0%5D=-0&PME_sys_sfn%5B1%5D=0&u=RUFFINM)。
- **核验位置**：实验设置与 OpenIreland 部分、LSTM 事件分类/预测窗、资源租用成本分析；PDF 第 5—11 页。

**研究工作**：利用真实商业 O-RAN 的测量预测切换事件，并根据预测提前配置/租用覆盖资源，降低运营成本。

**采用的方法**：

1. 通过 RIC/E2 采集 OpenIreland 网络 KPI，构造历史窗口和未来 HO/no-HO 标签。
2. LSTM 对未来窗口内是否发生切换进行二分类，分析预测窗和 precision/recall 的变化。
3. 将预测事件用于主动资源获取，利用误报与漏报代价模型选择资源配置方案。

**实验与主要结果**：OpenIreland 含 4 RU、4 DU、1 CU，使用真实商业网络测量；正文将预测指标与资源租用成本关联。文中超过 80% 的收益指给定成本模型下的运营成本节约。

**相关性与适用条件**：方向 B 直接相关于主动资源管理，真实数据证据较强。其核心不是重设计空口 HO 执行，不能把成本下降改写成 HOF 或中断时间下降。

**已收录原文**：arXiv 公开稿（2024），对应 TNSM 2025，12 页。包内路径：`02_Proactive_Mobility/B10_2025_Real_ORAN_Handover_Prediction.pdf`；[原始下载入口](https://arxiv.org/pdf/2404.19671)。

<a id="b11"></a>

### B11 — Next-cell and mobility prediction in new generation cellular systems based on convolutional neural networks and encoding mobility data as images

- **作者/发表**：Peppino Fazio, Miralem Mehic, Miroslav Voznak；Computer Networks 252, 110657，2024。
- **文献**：[DOI: 10.1016/j.comnet.2024.110657](https://doi.org/10.1016/j.comnet.2024.110657)；[机构全文入口](https://iris.unive.it/handle/10278/5076423)。
- **核验位置**：轨迹图像编码/CNN 方法；§4.3、图 21—23；PDF 第 14 页。

**研究工作**：将轨迹预测转化为图像分类，预测下一小区，并提前预留带宽以减少切换到达后的资源不足。

**采用的方法**：

1. 采用 AIR/RIR 等方式将移动历史编码成图像，让空间移动规律能被 CNN 处理。
2. 每个小区配置类似 LeCun CNN 的分类器，输出下一访问小区。
3. 把预测结果接入 I-DPBMA 带宽管理，提前为潜在到达用户预留资源，评价预测错误与 call dropping probability。

**实验与主要结果**：使用城市地图/轨迹与不同小区覆盖模型，多次仿真比较编码方式、预测和带宽预留效果。§4.3、图 21—23 确有资源管理评估，因此超过纯下一小区分类。

**相关性与适用条件**：方向 B 直接相关于主动预留；其 CDP 同时受预测和可用带宽影响，不能等同于 NR 的协议级 HOF。覆盖模型也不等于实测无线覆盖。

**已收录原文**：机构存储的出版正式版，16 页。包内路径：`02_Proactive_Mobility/B11_2024_CNN_Image_NextCell_Prediction.pdf`；[原始下载入口](https://iris.unive.it/retrieve/b0adc4dc-6128-4cbb-b707-fe5876f9e349/1-s2.0-S1389128624004894-main.pdf)。

<a id="b12"></a>

### B12 — A proposed mobility and resource prediction method for seamless handover and service continuity in 5G small cell networks

- **作者/发表**：Khoa Nguyen Dang Dinh, Peppino Fazio, Miroslav Voznak；PLOS One 21(8), e0355372，2026-08-12。
- **文献**：[DOI 与全文](https://doi.org/10.1371/journal.pone.0355372)。
- **核验位置**：§3 AR-RNN、算法 1；§4—5 仿真与表 3；§6 Rome 真实轨迹及 HetNet；§7 编码/开销分析，PDF 第 34—61 页。

**研究工作**：同时考虑将要访问的小区与未来 RB 需求，提前避开 barred 或资源不足的小区，并为可行目标做准备。

**采用的方法**：

1. 用 AR-RNN 架构分别建模 cell ID 序列和 RB 需求序列，比较 LSTM/GRU 等实现；自回归地产生 1—4 步预测。
2. 将未来候选、禁用状态与资源需求结合，提前选择替代小区并请求资源预留。
3. 为减小大量离散 cell/user ID 的编码开销，比较 one-hot 与二进制编码，并按用户组训练模型。

**实验与主要结果**：除新加坡 SUMO 与规则覆盖场景，还在 §6 使用约 316 辆 Rome 出租车的真实 GPS，叠加非均匀 Voronoi HetNet 做验证；无线网络和 barred 事件仍为构造。表 3 中 AR-LSTM 的 95.8% 是一步预测，四步为 81.6%。

**相关性与适用条件**：方向 B 直接相关于候选和资源联合管理。约 5 ms 是文中理想快速准备情形的时延，不能称为真实 5G 实测。真实轨迹验证与真实网络闭环部署应区分。

**已收录原文**：出版正式版，65 页。包内路径：`02_Proactive_Mobility/B12_2026_AR_RNN_Mobility_and_Resources.pdf`；[原始下载入口](https://journals.plos.org/plosone/article/file?id=10.1371/journal.pone.0355372&type=printable)。

<a id="b13"></a>

### B13 — Enhancing Reliability in Federated mmWave Networks: A Practical and Scalable Solution Using Radar-Aided Dynamic Blockage Recognition

- **作者/发表**：Mohammad Al-Quraan, Ahmed Zoha, Anthony Centeno, Haythem Bany Salameh, Sami Muhaidat, Muhammad Ali Imran, Lina Mohjazi；IEEE Transactions on Mobile Computing 23(10), 10146—10160，2024。
- **文献**：[DOI: 10.1109/TMC.2024.3373529](https://doi.org/10.1109/TMC.2024.3373529)；[作者机构 PDF](https://eprints.gla.ac.uk/322152/3/322152.pdf)。
- **核验位置**：§V 的 RaDaR、PHO 时机；§VI、图 10—12；PDF 第 7—14 页（包含机构封页）。

**研究工作**：预知动态遮挡发生的状态与时间，在 mmWave 链路被遮挡之前切换到其他小基站，以减少链路中断。

**采用的方法**：

1. 从 FMCW 雷达形成 range-angle 与 range-velocity 特征图，提取移动遮挡体信息。
2. 用双输出神经网络同时估计遮挡状态与到达时间，并用联邦学习协同训练不同客户端。
3. 将遮挡预测时间与预切换所需时间结合，提前连接替代 SBS，比较反应式与主动方案。

**实验与主要结果**：采用真实 DeepSense Scenario 30 测量训练/验证感知部分，再以第二 SBS 和 Wireless InSite 射线追踪构造切换场景。约 94% 成功率按论文 PHO 定义计算；文中的时延对比依赖过程模型。

**相关性与适用条件**：方向 B 直接相关，适合感知辅助切换。真实雷达数据不等于真实蜂窝网切换实测，双站场景和成功条件应在复现时保留。

**已收录原文**：机构公开作者稿，含机构封页，15 页。包内路径：`02_Proactive_Mobility/B13_2024_Radar_Aided_Federated_mmWave.pdf`；[原始下载入口](https://eprints.gla.ac.uk/322152/3/322152.pdf)。

<a id="b14"></a>

### B14 — Proactive handover optimization via multi-agent deep reinforcement learning in integrated LEO satellite–terrestrial networks for high-mobility terminals

- **作者/发表**：Huiyeon Jang, Junyoung Kim, In-Sop Cho, Minsu Shin, Joon Gyu Ryu, Soyi Jung；ETRI Journal 48(4), 577—589，2026-04-02 在线。
- **文献**：[DOI 与全文](https://doi.org/10.4218/etrij.2025-0240)。
- **核验位置**：§2.2 的 CNN-LSTM；§3.1—3.2 的未来目标/时机规划与 QMIX；§4、图 10—13。

**研究工作**：在星地融合网络中联合规划未来切换目标和时机，使多个高速终端避免频繁、相互冲突的切换。

**采用的方法**：

1. 为 TN 与 NTN 分别构建 CNN 编码器，输入 RSRP、距离、角度和相对速度等历史特征，再用 LSTM 解码器输出未来 RSRP。
2. 每个终端作为一个 agent，动作是保持当前服务，或在指定未来时点切到某候选；局部观测包含预测信号、负载及连接持续时间。
3. 采用 QMIX 的集中训练、分散执行，通过非负混合网络聚合 agent 价值；奖励兼顾数据速率和连续驻留，并惩罚低于最低速率。

**实验与主要结果**：MATLAB 星地系统仿真，比较测量式、预测均值式及独立 Q-learning。默认 2 步前瞻、含当前服务在内 2 个候选，测试 10/20 终端及不同速度；报告吞吐、HO 频率和乒乓改善。

**相关性与适用条件**：方向 B 直接相关。正文表格与段落对时步单位有不一致，复现前需核对；候选和前瞻范围较小，也没有实现 LTM/C-LTM。

**已收录原文**：出版社 PDF 正式版，13 页。包内路径：`02_Proactive_Mobility/B14_2026_QMIX_Proactive_Satellite_Terrestrial.pdf`；[原始下载入口](https://onlinelibrary.wiley.com/doi/pdf/10.4218/etrij.2025-0240)。

<a id="b15"></a>

### B15 — PreHO: Predictive Handover for LEO Satellite Networks

- **作者/状态**：Xingqiu He, Zijie Ying, Chaoqun You, Yue Gao；arXiv:2603.07987，2026，**预印本**。
- **文献**：[记录](https://arxiv.org/abs/2603.07987)；[PDF](https://arxiv.org/pdf/2603.07987)。
- **核验位置**：§IV 机制、§V 交替优化/动态规划、§VI 原型与评估；PDF 第 4—12 页。

**研究工作**：利用卫星轨道可预测性，在切换发生前生成 LEO 连接计划，减少测量报告与随机接入带来的过程开销。

**采用的方法**：

1. 根据星历、终端位置和可见性构建未来链路状态，提前确定候选及切换时点。
2. 设计 MR-less、RACH-less 和基于时间的条件执行流程，使准备与执行解耦。
3. 以吞吐、负载与切换开销构造规划目标，采用交替优化和动态规划求解，再在软件原型中验证流程。

**实验与主要结果**：UERANSIM/Open5GS 原型及 Starlink 星历数据仿真；分别评价过程和计划。准确预测设定下平均中断约 22.5 ms，比 BHO 缩短约 11.6 倍。

**相关性与适用条件**：方向 B 直接相关，且说明主动管理可由几何预测与传统优化实现。它是预印本；较静止终端及准确未来信息是关键设定，对预测误差的完整鲁棒性仍未证明。

**已收录原文**：arXiv 预印本，13 页。包内路径：`02_Proactive_Mobility/B15_2026_PreHO_LEO_Satellite.pdf`；[原始下载入口](https://arxiv.org/pdf/2603.07987)。

<a id="b16"></a>

### B16 — ISAC-Assisted Proactive Handover in mmWave Networks: Value of Foresight and Localization Requirements

- **作者/状态**：Seyed Bagher Hashemi Natanzi, Bo Tang；arXiv:2611.03771，2026-11，**预印本**。
- **文献**：[记录](https://arxiv.org/abs/2611.03771)；[PDF](https://arxiv.org/pdf/2611.03771)。
- **核验位置**：§III—IV 的前瞻价值与规划；§V-D/E 的实验、误差预算与图表；PDF 第 3—5 页。

**研究工作**：量化提前知道未来链路的价值，并检查雷达辅助预测在真实定位误差下是否仍能改善 mmWave 切换。

**采用的方法**：

1. 先构造不依赖具体策略的前瞻价值界，比较无预测、有限前瞻与 oracle。
2. 再通过 ISAC 雷达追踪遮挡体并预测 SNR，用考虑 HO 成本的规划器生成切换决策。
3. 逐项加入 UE/遮挡体定位误差与控制回路延迟，比较完美前瞻、实际追踪及调优 A5。

**实验与主要结果**：28 GHz、两小区街谷、Sionna 仿真。约 0.5 s 完美前瞻有潜力，但实际追踪规划可能落后于 A5，并产生更多 HO/乒乓；误差预算指向更高定位精度要求。

**相关性与适用条件**：方向 B 高相关的近期预印本。它提供有价值的负结果：预测和控制的组合不必然更优。E2 延迟在模型中设定，没有实现真实 E2 服务模型。

**已收录原文**：arXiv 预印本，6 页。包内路径：`02_Proactive_Mobility/B16_2026_ISAC_Value_of_Foresight.pdf`；[原始下载入口](https://arxiv.org/pdf/2611.03771)。

## Mobility Prediction 预测支撑 逐篇说明

<a id="p01"></a>

### P01 — A New Methodology for User Equipment Trajectory Prediction in Cellular Networks

- **作者/发表**：Juan Sánchez-González, Oriol Sallent, Jordi Pérez-Romero；IEEE Transactions on Vehicular Technology 73(9), 13710—13723，2024。
- **文献**：[DOI: 10.1109/TVT.2024.3388554](https://doi.org/10.1109/TVT.2024.3388554)；[作者机构 PDF](https://grcm.tsc.upc.edu/en/research-activities/publications/journals_files/tvt-3388554-pp_2-1.pdf)。
- **核验位置**：§IV 聚类/在线匹配、§V 场景、§VI 预测实验与部署讨论。

**研究工作**：从部分已观测轨迹预测未来位置、下一小区与到达时间，为提前准备提供可解释的移动性输入。

**采用的方法**：

1. 离线在每个小区内对轨迹作统一空间插值，并用 K-means 提取代表性轨迹原型。
2. 在线计算用户已走轨迹与原型的匹配距离，形成候选轨迹的概率/可信度。
3. 根据阈值选择未来轨迹，进一步推断下一 BS 和预计到达时刻，同时评价提前量与准确性的关系。

**实验与主要结果**：Cologne 约 5 万车辆、24 h 轨迹，叠加 245 BS 的 Voronoi 网络；训练约 502 万轨迹片段、测试约 44 万，重点评价预测正确率和可提前多久预测。

**相关性与适用条件**：属于高相关预测支撑。没有用完整 HO 控制 KPI 验证预测收益；Voronoi 覆盖不代表真实传播或协议实现。

**已收录原文**：机构公开作者稿，14 页。包内路径：`03_Mobility_Prediction/P01_2024_UE_Trajectory_Prototype_Prediction.pdf`；[原始下载入口](https://grcm.tsc.upc.edu/en/research-activities/publications/journals_files/tvt-3388554-pp_2-1.pdf)。

<a id="p02"></a>

### P02 — Graph Neural Networks for Open Radio Access Network Mobility Management: A Link Prediction Approach

- **作者/发表**：Ana González Bermúdez, Miquel Farreras, Milan Groshev, José Antonio Trujillo, Isabel de la Bandera, Raquel Barco；IEEE Vehicular Technology Magazine 20(4), 66—74，2025；预印本题名用 “O-RAN”。
- **文献**：[DOI: 10.1109/MVT.2025.3623286](https://doi.org/10.1109/MVT.2025.3623286)；[全文](https://arxiv.org/html/2502.02170)。
- **核验位置**：§III-B 的 rApp/xApp 架构；§IV-A—D 数据、VGAE/SEAL 比较；图 3—5。

**研究工作**：用图学习预测 UE 与小区的连接关系，利用用户/基站邻域结构辅助候选选择，并提出 O-RAN 的部署位置。

**采用的方法**：

1. 将 UE、cell 与关联关系表示为图，把潜在 UE-cell 关系看成链路预测任务。
2. 比较 VGAE 的潜变量重构与 SEAL 的局部子图分类，处理特征和正负样本不均衡。
3. 将模型放入 Non-RT RIC/rApp，并讨论通过 A1 与 Near-RT xApp 协作的架构。

**实验与主要结果**：使用匿名电信图和 EXata 数据，比较 ROC、F1、训练与推理开销；实验主要验证连接分类，正文说明尚未加入时间序列处理。

**相关性与适用条件**：高相关候选预测支撑，但现有连接图补全不自动等于未来时序预测；文中未提供闭环 HO 失败或乒乓改善证据。

**已收录原文**：arXiv 公开稿，对应 VTM 2025，8 页。包内路径：`03_Mobility_Prediction/P02_2025_GNN_ORAN_Link_Prediction.pdf`；[原始下载入口](https://arxiv.org/pdf/2502.02170)。

<a id="p03"></a>

### P03 — Meta-Continual Mobility Forecasting for Proactive Handover Prediction

- **作者/状态**：Sasi Vardhan Reddy Mandapati；arXiv:2512.11841，2025，**预印本**。
- **文献**：[记录](https://arxiv.org/abs/2512.11841)；[PDF](https://arxiv.org/pdf/2512.11841)。
- **核验位置**：§III 预测/HO 标签、§IV 方法、§V 数据构造、§VII 实验，表 I—VI。

**研究工作**：解决用户移动规律变化后预测器失配的问题，用少量新样本持续适应轨迹和派生切换事件。

**采用的方法**：

1. 共享 GRU 表征连接轨迹回归与 HO 标签预测两个输出头。
2. 用 Reptile 元学习寻找易于快速适应的初始化，再以 EWMA 监测预测残差是否发生分布漂移。
3. 漂移触发小批量在线更新，并以 L2 锚定限制遗忘；在跨区域任务和 few-shot 场景测试。

**实验与主要结果**：GeoLife GPS 与 DeepMIMO 信号代理构造的任务，3 步预测。正文报告 ADE/FDE、few-shot 适应及 HO 标签 F1/AUROC，例如 F1 约 0.83。

**相关性与适用条件**：相关在线预测支撑，预印本。HO 标签由 RSRP proxy 的服务小区变化生成，没有真实 RRC/MAC 切换流程；F1=0.83 不能解释成 HO 成功率 83%。

**已收录原文**：arXiv 预印本，6 页。包内路径：`03_Mobility_Prediction/P03_2025_MetaContinual_Mobility_Forecasting.pdf`；[原始下载入口](https://arxiv.org/pdf/2512.11841)。

## AI-enabled Mobility 综述与标准化 逐篇说明

<a id="s01"></a>

### S01 — A survey on AI-enabled mobility and handover management in future wireless networks: key technologies, use cases, and challenges

- **作者/发表**：Yasir Ullah 等；Journal of King Saud University Computer and Information Sciences 37, 47，2025-05-28。
- **文献**：[DOI 与全文](https://doi.org/10.1007/s44443-025-00048-9)。
- **核验位置**：§4—6 的 HO 流程、控制参数与传统/ML 方案；§7—9 场景及研究方向。

**研究工作**：梳理 AI-enabled mobility 与 handover 的技术、应用场景和挑战，建立从传统移动性到智能优化的分类框架。

**采用的方法**：

1. 先分解 HO 流程、控制参数与性能目标，说明 TTT/HOM 等参数的作用。
2. 按传统算法、监督学习、强化学习等方法整理文献，并覆盖 UAV、MEC、RIS 等使用场景。
3. 归纳数据、泛化、计算与部署问题，用其参考文献进一步追踪原始研究。

**实验与主要结果**：属于综述，没有作者提出的新控制器及对应闭环实验。适合写背景、定义与技术分类，方法性能需要回到各原始论文核实。

**相关性与适用条件**：作为综述单列。AI-enabled 范围比 predictive/proactive 更宽，其中很多方法只是反应式参数调整。

**已收录原文**：出版正式版，37 页。包内路径：`04_Surveys_Standardization/S01_2025_AI_Enabled_Mobility_Survey.pdf`；[原始下载入口](https://link.springer.com/content/pdf/10.1007/s44443-025-00048-9.pdf)。

<a id="s02"></a>

### S02 — AI-Driven Mobility Management in 5G and 6G Wireless Networks: A Survey

- **作者/发表**：Hafiz M. Asif, Abdulraqeb Alhammadi, Naser Tarhuni, Mohammed M. Bait-Suwailam；Future Internet 18(8), 425，2026-08-11。
- **文献**：[DOI 与全文](https://doi.org/10.3390/fi18080425)。
- **核验位置**：§3.7 生命周期；§4 主动管理框架；§5 创新与所引方法。

**研究工作**：从 5G/6G 移动性管理全生命周期组织 AI 研究，将切换、参数优化与负载均衡联系起来。

**采用的方法**：

1. 按数据/预测、决策、参数调整、执行、KPI 反馈与更新梳理生命周期。
2. 比较监督学习、深度学习、RL、FL 等方法如何进入不同管理环节。
3. 讨论 O-RAN、可解释性、泛化及实际部署难题，提出进一步研究方向。

**实验与主要结果**：综述性技术比较，没有独立的预测器—控制器闭环复现实验；可用来组织 related work 结构和发现被引文献。

**相关性与适用条件**：综述单列。规范定义和文中转引的性能数值仍需回查 3GPP 或原论文，不能作为所有主动方案都有效的实验证据。

**已收录原文**：出版正式版，47 页。包内路径：`04_Surveys_Standardization/S02_2026_AI_Driven_5G_6G_Mobility_Survey.pdf`；[原始下载入口](https://www.mdpi.com/1999-5903/18/8/425/pdf)。

<a id="s03"></a>

### S03 — AI/ML-Driven Predictive Mobility Management in 3GPP: Technical Insights and Standardization Trends

- **作者/发表**：Wonho Lee, Heeju Chae, Inkyu Bang, Eunkyung Kim, Taehoon Kim, Gosan Noh；IEEE ICTC 2025。
- **文献**：[会议公开全文](https://d2j16w31g89z0j.cloudfront.net/site/ictc2025/abs/B07-3.pdf)。
- **核验位置**：§II RRM measurement prediction、§III measurement event prediction 及后续挑战讨论；PDF 共 6 页。

**研究工作**：解释 3GPP 中 AI/ML 预测移动性管理的技术对象和标准化趋势，区分测量值预测与事件预测。

**采用的方法**：

1. 梳理 RRM measurement prediction：用历史测量预测未来 RSRP 等连续值，作为移动性判断输入。
2. 分别分析 measurement event prediction：直接预测事件是否或何时发生，支持提前准备和决策。
3. 讨论模型管理、输入输出、评估与实际部署中需要解决的标准化问题。

**实验与主要结果**：会议技术综述，正文共 6 页；主要证据是标准化问题分析及已有工作的归纳，没有作者新的闭环 HO 优化算法实验。

**相关性与适用条件**：与六组关键词中的 AI-enabled 和 predictive 高度相关；它描述标准化研究路线，最终协议行为仍以具体版本规范为准。

**已收录原文**：ICTC 2025 会议公开稿，6 页。包内路径：`04_Surveys_Standardization/S03_2025_3GPP_Predictive_Mobility_Trends.pdf`；[原始下载入口](https://d2j16w31g89z0j.cloudfront.net/site/ictc2025/abs/B07-3.pdf)。

<a id="s04"></a>

### S04 — Reactive to Predictive Mobility Management: A Systematic Review of ML-Driven Handover Optimization in 5G and Beyond

- **作者/发表**：Teresia Ankome, Eisuke Hanada；Machine Learning and Knowledge Extraction 8(5), 133，2026。
- **文献**：[DOI 与全文](https://doi.org/10.3390/make8050133)。
- **核验位置**：§3 检索/纳入方法；§4.2—4.5 ML、FL、RL；§5 综合比较。

**研究工作**：系统整理从反应式切换向预测式移动性管理的 ML 研究，并识别联邦学习、强化学习与网络控制的结合方式。

**采用的方法**：

1. 采用 PRISMA 式检索、筛选和纳入流程，报告 49 项覆盖 2010—2025 的研究。
2. 按预测、RL 控制、FL 和 SDN 等技术路线归类，比较输入、目标与性能评价。
3. 归纳可扩展性、隐私、实时性及数据可得性等问题，用于后向追踪原论文。

**实验与主要结果**：系统综述，无作者独立的 HO 实验；较早文献占一定比例，适合补引用网络，不宜直接当作近三年的实验清单。

**相关性与适用条件**：综述单列。本报告对保留研究另行核查正文，没有直接继承其相关性判断或所有性能数值。

**已收录原文**：出版正式版，29 页。包内路径：`04_Surveys_Standardization/S04_2026_Reactive_to_Predictive_Systematic_Review.pdf`；[原始下载入口](https://www.mdpi.com/2504-4990/8/5/133/pdf)。

## 技术补充与降级条目

### T01 — Reducing handover interruption with L1/L2 Triggered Mobility（技术补充，不计论文数）

- **作者/发表**：A. Orsino 等；Ericsson Technology Review，2025-04-22。
- **原文**：[技术文章与流程图](https://www.ericsson.com/en/reports-and-papers/ericsson-technology-review/articles/reducing-handover-interruption-l1l2-triggered-mobility)。
- **核验位置**：“Layer 1/Layer 2 Triggered Mobility — how it works”、图 2—3、“Future evolution”。
- **用途**：准备—早期同步—MAC CE 执行的解释清楚，适合快速理解工程流程。文中约 20—30 ms 的中断讨论与 A01 的 1 ms 理想化仿真假设不同，不应混为同一测量。

**工作与方法补充**：以工程信令时序拆解准备、提前同步和 MAC CE 执行，再讨论 RACH-less、候选配置及未来演进。适合解释机制，不作为独立算法性能论文。

**已收录原文**：厂商技术文章正式 PDF，非学术论文，7 页；`05_Technical_Supplement/T01_2025_Ericsson_LTM_Engineering_Review.pdf`。

### D01 — Intelligent O-RAN-Based Proactive Handover in Vehicular Networks

- **发表**：E. Rastogi, M. K. Maheshwari, J. P. Jeong；ICTC 2023。机构登记年份为 2024，会议年份为 2023。
- **文献**：[DOI: 10.1109/ICTC58733.2023.10392738](https://doi.org/10.1109/ICTC58733.2023.10392738)；[作者稿](https://researchonline.ljmu.ac.uk/id/eprint/24204/7/Intelligent_O_RAN_based_Proactive_Handover_20230516_v1.pdf)。
- **核验**：§III、式 (1)、§IV 与表 I。
- **降级理由**：实际预测的是两辆车之间的 compatibility time/连接持续类别；实验主要是 GNB、KNN、NN 分类准确率。未验证蜂窝小区目标选择、HO 执行或蜂窝 HO KPI。可作 V2V 链路持续时间支撑，不列入高相关蜂窝主动切换主清单。

**工作与方法补充**：根据两车运动和链路特征预测 compatibility time，离散为 5 个持续时间类别，比较 Gaussian Naive Bayes、KNN 与前馈网络。主要实验是分类准确率，没有形成蜂窝小区切换闭环。

**已收录原文**：公开作者稿，蜂窝主动切换相关性降级，6 页；`06_Downgraded_Reference/D01_2023_V2V_Compatibility_ORAN.pdf`。

### D02 — Predictive handover mechanism for seamless mobility in 5G and beyond networks

- **发表**：Thafer H. Sulaiman, Hamed S. Al-Raweshidy；IET Communications 19(1), e12878，2025。
- **文献**：[DOI: 10.1049/cmu2.12878](https://doi.org/10.1049/cmu2.12878)；[机构全文](https://bura.brunel.ac.uk/bitstream/2438/30529/3/FullText.pdf)。
- **核验**：§5 AI 方法介绍、§6—8 的 MATLAB 比较与图 2—3。
- **降级理由**：主题涉及切换，但较大部分为通用 RL/ML 介绍和 5 小区/100 用户的对比图，预测目标、时域、具体训练/控制设计不如 B01—B12 清晰。不推荐将其作为可复现的预测式 HO 核心基线。

**工作与方法补充**：介绍 RL/ML 支持的切换，并给出 MATLAB 的 5 小区、100 用户比较；正文对具体预测目标、训练和动作设计交代不足。完整正文已审读，但本次未取得可打包 PDF，保留其机构公开入口，不纳入主清单。

## 待补正文/确认版本的线索

以下没有计入 29 篇“已核正文”论文，也不据摘要重述详细性能。取得的出版社/机构摘要可确认主题，但不能代替方法与实验核查。

| ID | 论文与年份 | DOI / 原始入口 | 当前状态与后续核验重点 |
|---|---|---|---|
| U01 | L1/L2 Triggered Mobility (LTM) as Baseline for Mobility in 6G，PIMRC 2024，A. Orsino 等 | [10.1109/PIMRC59610.2024.10817289](https://doi.org/10.1109/PIMRC59610.2024.10817289) | 已核书目信息，未取得正文。需检查其独立模型/实验内容，不能用 T01 技术文章替代。 |
| U02 | Enhanced L1/L2-Triggered Mobility Management with Early CSI Acquisition in 5G-Advanced/6G，ICC 2025，D. Lee 等 | [10.1109/ICC52391.2025.11160900](https://doi.org/10.1109/ICC52391.2025.11160900) | 未取得正文。重点查 L1/L2 滤波决策及 early CSI 的具体时序与吞吐评估。 |
| U03 | AI-Augmented L1/L2 Triggered Mobility: Enabling 6G-Native Predictive Mobility，M. Dai 等 | [10.1109/MCOMSTD.2026.3653430](https://doi.org/10.1109/MCOMSTD.2026.3653430) | 未取得正文；索引期号指向 2026-12，早期在线日期未确认。暂不列入截至检索日已完成核验的发表论文。 |
| U04 | Mobility Management Paradigm Shift: From Reactive to Proactive Handover Using AI/ML，IEEE Network 38(2), 18—25，2024，H.-S. Park 等 | [10.1109/MNET.2024.3357108](https://doi.org/10.1109/MNET.2024.3357108)；[ETRI 记录](https://ksp.etri.re.kr/ksp/article/read?id=68802) | 主题高度相关；目前仅核到机构摘要，未取得正文。需查 UE/NW 模型、预测误差与 HO 目标/时机决策。 |
| U05 | AI/ML-Driven Proactive Mobility Management Strategies for 6G Networks，GLOBECOM 2025，Y. Jo 等 | [10.1109/GLOBECOM59602.2025.11432595](https://doi.org/10.1109/GLOBECOM59602.2025.11432595) | 未取得正文。重点查三种 AI 参与程度、FR2 模型与不同预测准确率下的结果。会议年份为 2025，Xplore 收录于 2026，不改记成 2026 会议。 |
| U06 | Incorporating Mobility Prediction in Handover Procedure for Frequent-Handover Mitigation in Small-Cell Networks，IEEE TNSE 12(1), 186—197，2025，S. M. Shahid 等 | [10.1109/TNSE.2024.3487415](https://doi.org/10.1109/TNSE.2024.3487415)；[ETRI 记录](https://ksp.etri.re.kr/ksp/article/read?id=70756) | 未取得正文。摘要指向 TTT 内 RSRP 趋势/运动方向判定；需核实预测含义，不能直接当作学习式轨迹预测。 |
| U07 | Predictive Handover Optimization Using Hybrid Radio Propagation Modeling for 5G and Beyond，WCNC 2026，G. Rakkesh 等 | [10.1109/WCNC65185.2026.11555140](https://doi.org/10.1109/WCNC65185.2026.11555140) | 未取得正文。需核查 radio map、传播模型、提前量和 potential HOF 的定义。 |
| U08 | FLeXHO: A Federated Learning Based Inter-Cell Handover Optimisation for Open 6G RAN，WCNC 2026，B. Akdogan 等 | [10.1109/WCNC65185.2026.11555724](https://doi.org/10.1109/WCNC65185.2026.11555724)；[作者机构记录](https://research.itu.edu.tr/tr/publications/flexho-a-federated-learning-based-inter-cell-handover-optimisatio/) | 2026 版本正文未取得。B09 是已核的 ELECO 2025 公开稿；不把两个版本的实验数字拼接，也不重复计入已核方法数量。 |

## 标准原文补充

### N01 — 3GPP TS 38.300 V19.4.0 / ETSI TS 138 300 V19.4.0，2026-09

[规范 PDF](https://www.etsi.org/deliver/etsi_ts/138300_138399/138300/19.04.00_60/ts_138300v190400p.pdf)

- §9.2.3.5：L1/L2 Triggered Mobility，规范页 108 起。
- §9.2.3.7：Conditional L1/L2 Triggered Mobility，规范页 115 起。
- 核查所得：LTM 的网络切换命令通过 MAC CE；CLTM 的执行由 UE 在预配置 L1/L3 条件满足时触发。两者均不以 AI 预测为定义条件。规范不计入论文数。

**已收录规范**：316 页；`07_3GPP_Standard/N01_2026_3GPP_TS38300_V19_4_0.pdf`。

## 阅读顺序与研究脉络

### 方向 A 单独阅读

1. **A02 → A03**：先建立 Rel-18/19 的流程与限制图谱。
2. **A01**：建立 BHO/CHO/低层移动性的仿真与滤波基线，理解乒乓—响应—预留的交换关系。
3. **A05 → A06**：分别理解未来信息的潜在价值和候选准备/资源分配的联合优化。
4. **A04**：需要 NTN 场景时阅读；其星内/星间混合机制应单独建模。

### 方向 B 单独阅读

1. **B01**：预测事件时间与提前准备的直接连接。
2. **B02**：主动切换与资源分配的联合优化。
3. **B03**：切换类型预测与 TTT/HOM 优化，且有代码入口。
4. **B06 / B07**：分别看未来 RSRP 与未来服务小区预测。
5. **B09 / B10**：看 O-RAN 控制与实际测量的工程证据，注意 B10 的主要目标是主动资源租用。
6. **B13 / B16**：看外部感知提供的前瞻信息及其误差代价；需要星地场景再读 B14/B15。

### 从正文得到的归纳

这些是对已核文献的综合判断，不是某篇论文单独证明的结论：

- **LTM 主线**已从降低单次切换中断，扩展到测量报告、候选配置保留、条件执行、inter-CU、安全/DC 和预留成本。只统计切换次数不足以评估 LTM。
- **主动管理主线**至少包含未来无线测量、未来事件时刻、未来服务小区/轨迹、未来遮挡、以及资源需求/可用性的预测。预测对象不同，控制动作和提前量也不同。
- **证据强弱应看控制链条**：有下一小区分类结果；有预测驱动的规则仿真；有协议栈软件原型；有真实测量。四者不能互相替代。
- **完美未来信息与真实预测器需区分**：A05、B15 的理想设定用于说明潜力；B16 表明现实误差能逆转收益。实验应同时报告预测误差、错误准备、切换开销、失败/中断和最终吞吐或业务成本。
- **候选准备与执行应一起检查**：A05 明确观察到只优化准备阶段效果有限；B02、A06 将资源控制纳入，使相关性强于只预测位置而不改变网络动作的工作。

## 引用与版本注意

- 正式发表年份、预印本首发年份与数据库收录年份分开记录；B04、B07、B10、A01 均存在这一差别。
- A03 的 inter-CU 讨论不自动意味着其所有 CLTM 流程都支持 inter-CU。
- 高铁论文的 L1-RSRP 输入、O-RAN 论文的低层 KPI 输入，都不自动说明实现了 LTM。
- 文献覆盖为公开可检索、可获得正文的高相关集合；受全文可得性限制，不声称穷尽所有数据库。U 表保留了高相关但尚未完成正文核验的线索。

## 原文合集使用说明

- 主清单 29 篇全部有 PDF：方向 A 6 篇、方向 B 16 篇、预测支撑 3 篇、综述/标准化文章 4 篇。
- 补充 T01 技术文章、D01 降级参考、N01 规范各 1 份，合计 32 份原始 PDF。D01 单列是为了保留审读依据，不将其重新计入核心论文。
- U01—U08 的正文尚未取得；D02 已审读完整正文但 PDF 下载未完成。这 9 项只列原始入口与状态，不以摘要或生成文件充当原文。
- 解压后打开 `index.html`，可按编号阅读方法说明并点击本地 PDF；`PDF_manifest.csv` 列出版本、来源、页数和 SHA-256，`Pending_sources.md` 列出未收录项。
- 每篇只收录一个已核版本，正式版与作者稿/预印本在条目中注明。作者稿中的占位 DOI 或模板年份原样保留，引用时采用本报告核实的正式书目信息。
- PDF 字节保持原样，不删除作者、版权页、出版社水印或许可信息；打包不改变各原文的适用许可。
