# 业务资料约定

原料和产出单位kg，成本CNY，price为原币每kg净价，rate为每单位原币对应CNY。input_kg与联产品产出差表示已登记过程损耗；未销售产出保留库存。internal销售是合并范围内转供。

每行id在该表内唯一，文件顺序不代表业务事件顺序。清单schema=1，各表登记文件名、字节长度、SHA256、行数及完整字段集合，未知版本或内容变化应重新登记。金额及测量数值均为独立资料，不代表任何现实机构的经营数据。

- production：id、month、input_kg、raw_cost、joint_cost。
- outputs：id、batch、product、kg。
- sales：id、month、batch、product、kg、price、currency、internal。
- fx：id、month、currency、rate。

normal与boundary是相互独立的资料包，不能直接拼接重复id。引用字段按本项目domain.py的REFERENCES登记。读取检查只检查完整性、身份及这些直接引用，不替代领域分析中的可识别性、时点可见性或可行性判断。
