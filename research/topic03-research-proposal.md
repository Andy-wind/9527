# 选题03 深度研究与开题方案（阶段性版本）
日期：2026-10-23
研究状态：文献查重完成初步范围检索；正式系统综述未完成；未采集实证数据；所有假设未经验证。

## 关键决策：原题必须修改
原题《人工智能战略披露与企业实质性创新——言行一致性及管理者短期主义的影响》与黄天鉴、王亮（2026）《人工智能漂洗如何抑制企业创新？》（证券市场导报，2026年第8期）高度重合。既有研究使用A股年报AI披露和AI专利构造漂洗指标，解释创新数量、质量以及资源配置机制。详见 https://zqscdb.szse.cn/article/id/c09fcef0-f3ac-4acd-b406-cedc8bfeb136 。
另外：Sun等（2026）研究AI washing与技术差距；Yin与Che（2026年5月SSRN预印本）研究AI战略脱钩与突破式创新数量/质量；He与Wang（2026年9月SSRN预印本）研究AI washing与突破式绿色创新。
不得把“AI漂洗减少企业创新”标注为本项目原创发现。

## 修订候选题
《人工智能战略承诺的兑现速度与企业跨领域知识重组——基于A股年报及专利的纵向研究》
研究对象：中国A股非金融企业；建议基期2015—2021年、专利追踪至2024年，视可获取性调整。
性质：观察性纵向关联研究；不是自然实验，也不能仅凭固定效应认定因果。

### 理论机制与对立假设
理论：信号理论、注意力基础观、知识基础观、动态能力。
H1（候选）：企业AI战略承诺兑现速度越快，其后续非AI跨领域知识重组越强。
H2（候选）：在知识基础多样性较高的企业，H1关系更强。
H3（竞争解释）：AI承诺可能代表趋势性宣传；AI专利快兑现可能仅源于原有技术优势，控制基期AI专利存量、预趋势后H1可能消失。
H4（竞争解释）：AI投资可能挤占其他技术创新，存在负向关系；不能预设所有结果均为正。

### 可复现变量（须在试点后锁定）
AIDisclose_it = 10000 * (经人工审核的年报AI战略相关句子数 / 年报总句子数)，按报告所属年度t。
AIPatent_it = 企业在t年申请、属于事前冻结的AI IPC/CPC/关键词联合分类器的发明专利数；核对申请人名称、集团子公司映射。
Commit_it = 1[AIDisclose_it位于当年同行业前25%，且t-2至t-1 AI专利存量低于行业中位数]，阈值为预先方案，敏感性另设。
Fulfill2_it = 1[Commit_it=1 且 t+1至t+2 AI专利申请达到基期+预定阈值]。**谨防后视偏差，兑现是t之后才可观察的结果，不可直接当作t期外生处理。**
TimeToFulfill_i,t = 从首次满足Commit到首次出现达到预设AI投入/专利验证门槛的间隔；右删失用生存分析，零专利不等于无真实应用。
RecombNonAI_i,t+3 = t+3非AI发明专利中包含企业过往未共同出现的IPC四位码组合的件数；作ln(1+count)；必须排除被归类为AI的专利，防止机械关系。
AltOutcome = t+3非AI专利新组合占比（分母为非AI发明专利数，零分母单独处理）。
Controls: ln资产、ROA、杠杆、企业年龄、研发强度、基期创新、AI专利存量、产权、行业竞争及城市/年度效应；基于公开年报手工/程序化提取。

### 识别设计（由弱到强）
描述：先考察年报承诺、AI专利兑现的时间分布和分组差异；绝不以事后兑现分组直接声称因果。
基准关联模型： RecombNonAI_{i,t+3} = α + β AIDisclose_{i,t} + γ AIPatentStock_{i,t-1} + θX_{i,t-1} + μ_i + λ_{industry×t} + ε_it。
另研究 AI 披露和后续兑现的交互关系时须明确这是预测/分层关系，可能受后处理偏误影响。
兑现速度：离散时间风险模型或Cox模型研究何种企业更快兑现；在t起固定协变量，右删失，避免不死时间偏误。
稳健性：年报分母改为全文字数、AI词典/句子分类替代、阈值20%/30%、非AI专利分类宽窄口径、不同时间窗、加入企业趋势、专利申请与授权口径对照、剔除ICT主业、滞后控制、企业聚类标准误。
内生性：先用预趋势、基期技术能力、企业与行业×年固定效应处理部分共同冲击；如无可信外生工具或政策冲击，只报告关联，不作强因果结论。切忌将滞后变量或未经论证的区域AI政策直接当工具变量。
统计挑战：首发“AI承诺”可能很少，专利滞后及公开延迟、样本右删失、AI专利并不完全等于AI实际应用、低质量文本和集团专利归属误差。

### 免费数据路径与试点
年报：巨潮资讯 https://www.cninfo.com.cn/ （公开下载，批量获取速度、协议限制和OCR需核对）。
专利：国家知识产权局 https://pss-system.cponline.cnipa.gov.cn/ （实名注册；2026-06-09官方明确可加入批量下载库并导出Excel：https://www.cnipa.gov.cn/jact/front/mailpubdetail.do?sysid=12&transactId=535773 ）。
财务控制变量：公开年报/交易所公告自行提取；不得默认可免费获取CSMAR/Wind。
试点建议：按行业和规模抽取50家A股企业、2018—2021基期年报，并匹配至2024年专利；逐项记录有效样本、匹配率、文本错判率、专利追踪窗口及缺失率。此处仅为建议，没有下载或测试。
数据要求：取得网站授权范围内的数据，遵守服务条款和访问频率；敏感数据不得提交公共GitHub。
Go/no-go：AI披露样本覆盖、非AI专利知识重组存在足够变异、可观察至少2年兑现窗口、关键财务控制可从公开来源获得；不通过则改为更窄的行业样本或放弃该方案。

### 相关研究及核查
- 黄天鉴、王亮（2026），《人工智能漂洗如何抑制企业创新？》，《证券市场导报》2026年第8期。https://zqscdb.szse.cn/article/id/c09fcef0-f3ac-4acd-b406-cedc8bfeb136
- Sun, Z. et al. (2026), Unveiling AI washing: Bridging corporate technological gaps through a cognitive dissonance lens, Technological Forecasting and Social Change. https://doi.org/10.1016/j.techfore.2025.124511
- Yin, Z. & Che, J. (2026), When AI Narratives Outpace AI Investment: Strategic Decoupling and the Quantity–Quality Tradeoff in Firm Innovation, SSRN preprint, posted May 5, 2026. https://papers.ssrn.com/sol3/Delivery.cfm/0eda8718-01c3-43a1-9aae-df2c52380631-MECA.pdf?abstractid=6715522
- He, L.-Y. & Wang, L. (2026), All Talk, No Green Breakthrough? AI Washing and Breakthrough Green Innovation, SSRN preprint posted Sep 8 2026. https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7435213
- Song, X. et al. (2026), AI washing: Strategic disclosure and backlash, Finance Research Letters 95, 109684. https://doi.org/10.1016/j.frl.2026.109684
- Xia, Y. et al. (2026), Beyond AI Narratives: AI Washing and Organizational Resilience, Systems 14(7),853. https://doi.org/10.3390/systems14070853
- 国家知识产权局（2024），《人工智能相关发明专利申请指引（试行）》 https://www.cnipa.gov.cn/art/2024/12/31/art_66_196988.html
本检索是跨搜索引擎的目标性查重，不是已完成数据库全量检索、人工标题摘要筛选或PRISMA系统综述。正式系统综述须补充CNKI/万方/Scopus/WoS/OpenAlex等可用来源并记录日期、式子、结果数、去重数，必要时通过学校授权使用。零个未找到不证明不存在。

### 里程碑
M1 查重与方向修订：本文件，待用户批准。
M2 公开数据试点：审批后开始，保存字典、样例和质量报告。
M3 研究模型冻结：试点结果及新的文献证据足够后开始。
M4 全样本收集与实证：仅获批准后。
M5 写作与审稿：仅基于真实结果。
