# System Level Tools Comparison

## 主流工具或研究
| 廠商/來源 | 工具/流程 | 抽象層級 | 主要能力 | 備註  |
| --- | --- | --- | --- | --- |
| Synopsys | Platform Architect | SystemC TLM SoC 層 | SoC 架構、匯流排/NoC/記憶體階層、HW/SW 分割、系統級 throughput/latency/power 估算 | 商業 SoC 架構 DSE [synopsys](https://www.synopsys.com/verification/virtual-prototyping/platform-architect.html)​ |
| Cadence | Stratus HLS + Genus/Joules | 硬體區塊/子系統（HLS→RTL） | 從 SystemC/C++ 自動產生 RTL，多版本微架構探索，PPA 估算與優化 | 硬體區塊層級 PPA DSE，可接 SoC flow [cadence](https://www.cadence.com/zh_TW/home/resources/datasheets/stratus-high-level-synthesis-ds.html)​ |
| Siemens | Catapult HLS | 硬體區塊/子系統（C++/SystemC→RTL） | C++/SystemC HLS，自動 architecture exploration，PowerPro 功耗估算，低功耗優化 | HLS 層級 PPA 探索，ASIC/FPGA 硬體區塊優化 [eda.siemens](https://eda.sw.siemens.com/en-US/ic/catapult-high-level-synthesis/low-power/) |
| 學術研究（哈佛大學） | FARSI | System‑level DSSoC | 針對 AR/ML 特定應用，提供快速系統模擬、啟發式DSE、優化通訊/計算/工作負載/設計等 | 用 Synopsys Platform Architect 當比較對象，開源性質適合自建/研究 [devashreetrip.github](https://devashreetrip.github.io/publication/FARSI_TECS_CameraReady.pdf) |

## 技術差異
| 面向       | Synopsys Platform Architect         | Cadence Stratus HLS + Genus/Joules | Siemens Catapult HLS                       |
| -------- | ----------------------------------- | ---------------------------------- | ------------------------------------------ |
| 抽象層級     | SoC 系統整體：模擬 CPU、匯流排、記憶體等互動​ | 單一硬體區塊：演算法轉硬體描述​           | 單一硬體區塊：演算法轉硬體描述，強調低功耗優化          |
| 核心技術     | TLM 模擬，快速看系統效能                       | 演算法優化 + 綜合 + 功耗分析，給精準硬體區塊數據          | 演算法優化 + 功耗估算及優化 |
| PPA 估算   | 系統粗估：整體功耗/速度/面積，誤差較大但快              | 硬體區塊精準：接近實際硬體的功耗/速度/面積               | 硬體區塊精準：強調低功耗，內建低功耗優化機制              |
| 設計空間探索     | 整體拓樸：核心數、匯流排型式、記憶體配置                | 硬體區塊內部：管線深度、資源共享、迴圈展開                | 硬體區塊內部：管線深度、低耗分析       |
| 速度 vs 精確度 | 超快、低精確度（秒級系統評估）                      | 中等、高精確度（分鐘級硬體區塊分析）                    | 中等、高精確度（功耗優化最佳）            |

## 市占比較
- 商業 SoC TLM DSE 領域：Synopsys 優於 Siemens 及 Cadence 相關產品，產業報告顯示 Synopsys 在 verification/simulation 佔 30–35%，Platform Architect 是該類產品標準，其他商業替代少見直接競爭。 
- HLS 層級 PPA：在 HLS 市場中 Catapult（Siemens）/Stratus（Cadence）更加普及，Siemens/Cadence 各佔優勢，且是該領域成長最快的解決方案。 

## 技術名詞註釋
TLM: Transaction Level Modeling

DSE: Design Space Exploration 

HLS: High Level Synthesis 

PPA: Power, Performance, Area 
