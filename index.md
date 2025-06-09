# 项目功能特点

•	并发：支持 10~100 万 QPS 级交易吞吐
•	多链：原生支持 ETH / Tron / Solana / BTC
•	技术特点：高性能、模块化、安全审计友好
•	当前进度：已完成约 60%，已验证稳定性与安全性
•	10大核心核心模块：user-service、billing- service、moneyin-service、moneyout- service、kms-service、admin-service、arch-service、system-doctor、system- security、log-service
•	进程间通信模式：ETH 节点安全控制进程间通信机制
•	Kafka消息队列安全机制：SASL+SCRAM
•	系统架构：参考京东支付架构，前端 + Nginx + Go 微服务 + Kafka + Memcached + MySQL Master/Slave+ PostgreSQL，Nginx 做 安全校验及 VIP用户分流
•	中心化钱包管理体系：基于AWS-KMS 或者 HSM的 钱包自动生成及密钥管理机制，一次性100万钱包生成及密钥管理机制，1万个钱包对应1个热钱包及一个温钱包。AWS-KMS 安全签名功能
•	记账系统安全机制：三重校验，本库/Log/外库，每日自动校验及对账单功能
•	代码安全机制：全文件外库Hash自动化校验
•	系统安全机制：6套常规风险极速解决方案及自动化脚本支持
•	钱包地址资金变化监控机制：Event消息机制，摒弃高消耗轮询方法，采用被动式Event，大大降低成本
•	地址RiskScore检测：入金 和 出金的 地址安全检测功能，避免污染核心钱包地址，对涉毒、涉恐资金起到安全隔离作用
•	支持自建节点：ETH/Tron/Solana/Bitcoin
•	热钱包暖钱包管理：3/5 多签机制
•	大额出金管理：支持 三级授权出金管理
•	Gas费用优化：支持 ETH/Tron 支付优化
•	用户安全：邮箱验证、手机号码验证、Google 2FA验证、支付密码验证、多设备登陆管理
•	Nginx 分发：负载均衡器，Go Process 任意动态梳理配置，Docker一键部署
•	VIP用户机制：支持VIP机制，独立服务器通道，在经历服务器攻击后，不影响VIP用户访问
•	邀请激励机制：支持用户邀请后激励体系
•	KYC框架：支持KYC框架
•	语言支持：中文/日文/英文/荷兰语
