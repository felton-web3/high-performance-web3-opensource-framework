# Orion-Pay: High-Performance Multi-Chain Crypto Payment Gateway

<p align="center">
  <img src="https://img.shields.io/badge/status-60%25%20complete-brightgreen" alt="Status">
  <img src="https://img.shields.io/badge/QPS-100K%2B-blue" alt="QPS">
  <img src="https://img.shields.io/badge/license-MIT-lightgrey" alt="License">
</p>

<p align="center">
  <b>English</b> | <a href="#zh-cn">简体中文</a> | <a href="#zh-tw">繁體中文</a> | <a href="#ja">日本語</a>
</p>

---

## 🇬🇧 English

A high-performance, modular, and secure multi-chain crypto payment gateway designed for enterprise-level transaction throughput.

### ✨ Key Features

* **High Concurrency**: Supports transaction throughput from 100,000 to 1,000,000 QPS.
* **Multi-Chain Support**: Native support for ETH, Tron, Solana, and BTC.
* **Technical Excellence**: High-performance, modular design, and friendly for security audits.
* **Current Status**: Approximately 60% complete, with stability and security already validated.

### 🏛️ System Architecture

Inspired by JD.com's payment architecture, the system is structured as follows:
**Frontend** -> **Nginx** -> **Go Microservices** -> **Kafka** -> **Memcached** -> **MySQL (Master/Slave)** -> **PostgreSQL**
* **Nginx**: Handles security validation and traffic routing for VIP users.

### 🔐 Security Highlights

* **Inter-Process Communication**: Secure IPC mechanism for controlling ETH nodes.
* **Kafka Security**: Utilizes SASL/SCRAM for message queue authentication.
* **Wallet Security**: Automated wallet generation and key management based on **AWS-KMS** or HSM. Features a 3/5 multi-sig mechanism for hot/warm wallets.
* **Accounting Integrity**: Triple-check accounting system (local DB, logs, external DB) with automated daily reconciliation.
* **Code Integrity**: Automated Hash verification for all critical files against an external database.
* **System Defense**: Includes 6 pre-built rapid response solutions and automated scripts for common risks.
* **Address Risk Scoring**: Security checks for both incoming and outgoing addresses to prevent contamination of core wallets and isolate funds from illicit sources.
* **Large Withdrawals**: Three-level authorization management for large-amount withdrawals.
* **User Security**: Comprehensive security measures including Email, SMS, Google 2FA, payment passwords, and multi-device login management.

### 核心模块 (Core Modules)

The system is composed of 10 core microservices:

user-service
billing-service
moneyin-service
moneyout-service
kms-service
admin-service
arch-service
system-doctor
system-security
log-service

### 🚀 Other Advanced Features

* **Node Support**: Supports self-hosting nodes for ETH, Tron, Solana, and Bitcoin.
* **Wallet Management**: Efficiently generates 1 million wallets at once. For every 10,000 wallets, one hot wallet and one warm wallet are assigned.
* **Event-Driven Monitoring**: Uses a passive event-based mechanism to monitor wallet balance changes, significantly reducing costs compared to high-consumption polling methods.
* **Gas Fee Optimization**: Supports gas fee optimization for ETH and Tron transactions.
* **Dynamic Deployment**: Nginx load balancer with dynamic Go process configuration and one-click Docker deployment.
* **VIP System**: Dedicated server channels for VIP users to ensure service availability during cyber-attacks.
* **Referral Program**: Supports an incentive system for user referrals.
* **KYC Framework**: Includes a ready-to-integrate KYC framework.
* **Language Support**: Chinese, Japanese, English, Dutch.

---

### 🗺️ Next Steps & Roadmap

* **Demo Scenarios**:
    * OTC Demo (e.g., in-store clerk systems, physical vs. digital asset validation).
    * Exchange Integration Demo (Binance, OKX, Coinbase).
    * Decentralized Wallet Demo.
    * Web3 Aggregated Payment Demo.
    * Fiat Exchange Demo.
    * Offline Merchant Crypto Payment Solution.
    * Kernel-level Exchange Demo.
    * RWA (Real World Asset) on-chain and trading demo (with automated profit sharing via smart contracts).
    * DEX (Decentralized Exchange) Demo.
    * Hardware Wallet Payment Demo.
    * Coin Mixer Demo.
* **Financial Products**:
    * Crypto-based collateralized lending and fixed-term deposit scenarios.
    * Stock asset RWA tokenization demo.
    * Data-driven products (e.g., "Smart Money" tracking, payment flow analysis).
* **System Scaling**:
    * Experiment with concurrency for 100 million+ users.
* **Chain & Token Support**:
    * Integrate more chains and tokens.


---
---

<div id="zh-cn"></div>

## 🇨🇳 简体中文

一款高性能、模块化、安全为核心的多链加密货币支付网关，为企业级交易吞吐量而设计。

### ✨ 项目功能特点

* **高并发**: 支持 10 万至 100 万 QPS 级别的交易吞吐。
* **多链支持**: 原生支持 ETH / Tron / Solana / BTC。
* **技术特点**: 高性能、模块化、对安全审计友好。
* **当前进度**: 已完成约 60%，并已完成稳定性和安全性的初步验证。

### 🏛️ 系统架构

参考京东支付架构设计，系统流程如下：
**前端** -> **Nginx** -> **Go 微服务** -> **Kafka** -> **Memcached** -> **MySQL (主从)** -> **PostgreSQL**
* **Nginx**: 负责安全校验及 VIP 用户的流量分发。

### 🔐 安全机制亮点

* **进程间通信**: 为 ETH 节点设计的安全控制进程间通信机制。
* **Kafka 安全**: 使用 SASL+SCRAM 确保消息队列的访问安全。
* **钱包安全**: 基于 **AWS-KMS** 或 HSM 的钱包自动生成及密钥管理，支持 **3/5 多签机制**管理热钱包和暖钱包。
* **记账系统安全**: 三重校验机制（本库/Log/外库），支持每日自动对账。
* **代码安全**: 核心文件外库 Hash 自动化校验，防止代码被篡改。
* **系统安全**: 内置 6 套针对常规风险的极速解决方案及自动化脚本。
* **地址风险检测**: 对出入金地址进行安全检测，避免污染核心钱包，隔离涉恐、涉毒资金。
* **大额出金管理**: 支持三级授权出金管理。
* **用户安全**: 支持邮箱、手机、Google 2FA、支付密码等多重验证和多设备登陆管理。

### 核心模块 (Core Modules)

系统由 10 大核心微服务构成：

user-service (用户服务)
billing-service (计费服务)
moneyin-service (入金服务)
moneyout-service (出金服务)
kms-service (密钥管理服务)
admin-service (后台管理服务)
arch-service (架构服务)
system-doctor (系统诊断)
system-security (系统安全)
log-service (日志服务)

### 🚀 其他高级功能

* **节点支持**: 支持自建 ETH / Tron / Solana / Bitcoin 节点。
* **钱包管理**: 支持一次性生成 100 万个钱包，并按照 1 万个钱包配置 1 个热钱包和 1 个温钱包的比例进行管理。
* **资金变化监控**: 采用被动式 Event 消息机制，摒弃高消耗的轮询方式，极大降低系统成本。
* **Gas 费用优化**: 支持 ETH / Tron 的 Gas 费支付优化。
* **动态部署**: Nginx 负载均衡器，支持 Go Process 任意动态梳理配置，Docker 一键部署。
* **VIP 机制**: 支持 VIP 机制，为 VIP 用户提供独立服务器通道，在服务器受攻击时不影响其访问。
* **邀请激励**: 支持用户邀请激励体系。
* **KYC 框架**: 内置 KYC 框架，方便集成。
* **语言支持**: 中文、日文、英文、荷兰语。

---

### 🗺️ 下一步开发计划

* **Demo 场景开发**:
    * OTC 类 Demo (如店员系统、实物资产与线上数据校验)。
    * 交易所对接类 Demo (Binance, OKX, Coinbase)。
    * 去中心化钱包 Demo。
    * Web3 聚合支付 Demo。
    * 法币兑换类 Demo。
    * 线下商业数字货币支付解决方案。
    * 内核级别交易所类 Demo。
    * RWA 资产上链及交易 Demo (含智能合约自动分润)。
    * DEX (去中心化交易所) Demo。
    * 硬件钱包支付 Demo。
    * 混币器 Demo。
* **金融产品规划**:
    * 币本位质押、定存等金融产品场景。
    * 股票资产 RWA 化 Demo。
    * 数据类资产产品 (如聪明钱跟踪、支付链路分析)。
* **性能与扩展**:
    * 进行亿级用户并发实验。
    * 支持更多公链及代币。


---
---

<div id="zh-tw"></div>

## 🇹🇼 繁體中文

一款高效能、模組化、以安全為核心的多鏈加密貨幣支付網關，為企業級交易吞吐量而設計。

### ✨ 專案功能特點

* **高並發**: 支援 10 萬至 100 萬 QPS 級別的交易吞吐。
* **多鏈支援**: 原生支援 ETH / Tron / Solana / BTC。
* **技術特點**: 高效能、模組化、對安全審計友好。
* **當前進度**: 已完成約 60%，並已完成穩定性與安全性的初步驗證。

### 🏛️ 系統架構

參考京東支付架構設計，系統流程如下：
**前端** -> **Nginx** -> **Go 微服務** -> **Kafka** -> **Memcached** -> **MySQL (主從)** -> **PostgreSQL**
* **Nginx**: 負責安全校驗及 VIP 用戶的流量分發。

### 🔐 安全機制亮點

* **行程間通訊**: 為 ETH 節點設計的安全控制行程間通訊機制。
* **Kafka 安全**: 使用 SASL+SCRAM 確保訊息佇列的存取安全。
* **錢包安全**: 基於 **AWS-KMS** 或 HSM 的錢包自動生成及金鑰管理，支援 **3/5 多簽機制**管理熱錢包和溫錢包。
* **記帳系統安全**: 三重校驗機制（本庫/Log/外庫），支援每日自動對帳。
* **程式碼安全**: 核心檔案外庫 Hash 自動化校驗，防止程式碼被篡改。
* **系統安全**: 內建 6 套針對常規風險的極速解決方案及自動化腳本。
* **地址風險檢測**: 對出入金地址進行安全檢測，避免污染核心錢包，隔離涉恐、涉毒資金。
* **大額出金管理**: 支援三級授權出金管理。
* **用戶安全**: 支援信箱、手機、Google 2FA、支付密碼等多重驗證和多裝置登入管理。

### 核心模塊 (Core Modules)

系統由 10 大核心微服務構成：

user-service (用戶服務)
billing-service (計費服務)
moneyin-service (入金服務)
moneyout-service (出金服務)
kms-service (金鑰管理服務)
admin-service (後台管理服務)
arch-service (架構服務)
system-doctor (系統診斷)
system-security (系統安全)
log-service (日誌服務)

### 🚀 其他進階功能

* **節點支援**: 支援自建 ETH / Tron / Solana / Bitcoin 節點。
* **錢包管理**: 支援一次性生成 100 萬個錢包，並按照 1 萬個錢包配置 1 個熱錢包和 1 個溫錢包的比例進行管理。
* **資金變化監控**: 採用被動式 Event 訊息機制，摒棄高消耗的輪詢方式，極大降低系統成本。
* **Gas 費用優化**: 支援 ETH / Tron 的 Gas 費支付優化。
* **動態部署**: Nginx 負載均衡器，支援 Go Process 任意動態梳理配置，Docker 一鍵部署。
* **VIP 機制**: 支援 VIP 機制，為 VIP 用戶提供獨立伺服器通道，在伺服器受攻擊時不影響其訪問。
* **邀請激勵**: 支援用戶邀請激勵體系。
* **KYC 框架**: 內建 KYC 框架，方便整合。
* **語言支援**: 中文、日文、英文、荷蘭語。

---

### 🗺️ 下一步開發計畫

* **Demo 場景開發**:
    * OTC 類 Demo (如店員系統、實物資產與線上數據校驗)。
    * 交易所對接類 Demo (Binance, OKX, Coinbase)。
    * 去中心化錢包 Demo。
    * Web3 聚合支付 Demo。
    * 法幣兌換類 Demo。
    * 線下商業數字貨幣支付解決方案。
    * 內核級別交易所類 Demo。
    * RWA 資產上鏈及交易 Demo (含智能合約自動分潤)。
    * DEX (去中心化交易所) Demo。
    * 硬體錢包支付 Demo。
    * 混幣器 Demo。
* **金融產品規劃**:
    * 幣本位質押、定存等金融產品場景。
    * 股票資產 RWA 化 Demo。
    * 數據類資產產品 (如聰明錢跟蹤、支付鏈路分析)。
* **性能與擴展**:
    * 進行億級用戶並發實驗。
    * 支援更多公鏈及代幣。

---
---

<div id="ja"></div>

## 🇯🇵 日本語

エンタープライズレベルのトランザクションスループットを実現するために設計された、高性能、モジュール式、セキュアなマルチチェーン暗号資産決済ゲートウェイです。

### ✨ 主な特徴

* **高い並行処理能力**: 10万〜100万QPSレベルのトランザクションスループットをサポート。
* **マルチチェーン対応**: ETH / Tron / Solana / BTC をネイティブでサポート。
* **技術的特徴**: 高性能、モジュール設計、セキュリティ監査にフレンドリー。
* **現在の進捗**: 約60%完了し、安定性とセキュリティの検証済み。

### 🏛️ システムアーキテクチャ

京東（JD.com）の決済アーキテクチャを参考に設計されており、システムの構成は以下の通りです：
**フロントエンド** -> **Nginx** -> **Goマイクロサービス** -> **Kafka** -> **Memcached** -> **MySQL (Master/Slave)** -> **PostgreSQL**
* **Nginx**: セキュリティ検証とVIPユーザーのトラフィックルーティングを担当。

### 🔐 セキュリティハイライト

* **プロセス間通信**: ETHノードを制御するためのセキュアなIPCメカニズム。
* **Kafkaセキュリティ**: SASL+SCRAMを利用し、メッセージキューの認証を確保。
* **ウォレットセキュリティ**: **AWS-KMS**またはHSMに基づいた自動ウォレット生成と鍵管理。ホット/ウォームウォレットには**3/5マルチシグ**メカニズムを採用。
* **会計整合性**: 三重チェック会計システム（ローカルDB、ログ、外部DB）と、毎日の自動照合機能。
* **コード整合性**: 重要なファイルすべてに対し、外部データベースを用いた自動ハッシュ検証を実施。
* **システム防御**: 一般的なリスクに対応する6つの即時対応ソリューションと自動化スクリプトを内蔵。
* **アドレスリスクスコアリング**: 入出金アドレスのセキュリティチェック機能により、コアウォレットの汚染を防ぎ、不正資金を隔離。
* **高額出金管理**: 高額出金のための三段階承認管理をサポート。
* **ユーザーセキュリティ**: メール、SMS、Google 2FA、決済パスワード、複数デバイスログイン管理など、包括的なセキュリティ対策。

### コアモジュール (Core Modules)

システムは10のコアマイクロサービスで構成されています：

user-service (ユーザーサービス)
billing-service (請求サービス)
moneyin-service (入金サービス)
moneyout-service (出金サービス)
kms-service (鍵管理サービス)
admin-service (管理者サービス)
arch-service (アーキテクチャサービス)
system-doctor (システム診断)
system-security (システムセキュリティ)
log-service (ログサービス)

### 🚀 その他の高度な機能

* **ノードサポート**: ETH / Tron / Solana / Bitcoinの自己ホスティングノードをサポート。
* **ウォレット管理**: 一度に100万のウォレットを効率的に生成。1万ウォレットごとに1つのホットウォレットと1つのウォームウォレットを割り当て。
* **イベント駆動型監視**: ウォレット残高の変動を監視するためにパッシブなイベントベースのメカニズムを採用し、高負荷なポーリング方式に比べてコストを大幅に削減。
* **ガス代最適化**: ETHおよびTronトランザクションのガス代最適化をサポート。
* **動的デプロイメント**: 動的なGoプロセス構成とワンクリックでのDockerデプロイメントが可能なNginxロードバランサー。
* **VIPシステム**: サイバー攻撃時にもVIPユーザーのサービス利用を確保するための専用サーバーチャネル。
* **紹介プログラム**: ユーザー紹介に対するインセンティブシステムをサポート。
* **KYCフレームワーク**: 統合しやすいKYCフレームワークを内蔵。
* **言語サポート**: 中国語、日本語、英語、オランダ語。

---

### 🗺️ 次のステップとロードマップ

* **デモシナリオ**:
    * OTCデモ（例：店舗店員システム、物理資産とデジタル資産の検証）。
    * 取引所連携デモ（Binance、OKX、Coinbase）。
    * 分散型ウォレットデモ。
    * Web3集約決済デモ。
    * 法定通貨交換デモ。
    * オフライン事業者向け暗号資産決済ソリューション。
    * カーネルレベル取引所デモ。
    * RWA（現実世界資産）のオンチェーン化と取引デモ（スマートコントラクトによる利益分配を含む）。
    * DEX（分散型取引所）デモ。
    * ハードウェアウォレット決済デモ。
    * コインミキサーデモ。
* **金融商品**:
    * 暗号資産担保ローンや定期預金シナリオ。
    * 株式資産のRWAトークン化デモ。
    * データ駆動型商品（例：「スマートマネー」追跡、決済フロー分析）。
* **システムスケーリング**:
    * 1億人以上のユーザー並行処理実験。
* **チェーン＆トークンサポート**:
    * さらなるチェーンとトークンの統合。
