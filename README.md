<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Molly Web3 OpenSource Framework</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Noto+Sans+SC:wght@400;500;700&family=Noto+Sans+TC:wght@400;500;700&family=Noto+Sans+JP:wght@400;500;700&family=Noto+Sans+Thai:wght@400;500;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/vue@3/dist/vue.global.prod.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/heroicons@2.1.1/css/solid.min.css">

    <style>
        /* Base styles */
        body {
            font-family: 'Inter', 'Noto Sans SC', 'Noto Sans TC', 'Noto Sans JP', 'Noto Sans Thai', sans-serif;
            background-color: #f8fafc; /* slate-50 */
            color: #334155; /* slate-700 */
        }
        .dark body {
            background-color: #0f172a; /* slate-900 */
            color: #cbd5e1; /* slate-300 */
        }
        /* Gradient text */
        .gradient-text {
            background: linear-gradient(to right, #4f46e5, #ec4899);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-fill-color: transparent;
        }

        .card {
            background-color: white;
            border-radius: 0.75rem;
            box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
        }

        .section-title {
            font-size: 2.25rem; /* text-4xl */
            font-weight: 700; /* bold */
            text-align: center;
            margin-bottom: 2rem;
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: linear-gradient(to right, #4f46e5, #ec4899);
            border-radius: 2px;
            margin: 0.5rem auto 0;
        }

        .btn {
            display: inline-block;
            padding: 0.75rem 1.5rem;
            border-radius: 0.5rem;
            font-weight: 600;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .btn-primary {
            background-color: #4f46e5; /* indigo-600 */
            color: white;
        }

        .btn-primary:hover {
            background-color: #4338ca; /* indigo-700 */
        }

        .btn-secondary {
            background-color: #e2e8f0; /* slate-200 */
            color: #475569; /* slate-600 */
        }
        
        .btn-secondary:hover {
             background-color: #cbd5e1; /* slate-300 */
        }

        [v-cloak] {
            display: none;
        }

    </style>
</head>
<body>

    <div id="app" v-cloak>

        <header class="bg-white/80 backdrop-blur-md shadow-sm sticky top-0 z-50">
            <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
                <a href="#" class="flex items-center space-x-3 rtl:space-x-reverse">
                    <img src="https://i.postimg.cc/HLnMN7s6/Chat-GPT-Image-2025-6-9-10-19-48.png" alt="Molly Web3 Logo" class="h-8">
                    <span class="self-center text-2xl font-bold whitespace-nowrap gradient-text">Molly Web3</span>
                </a>

                <div class="flex items-center space-x-4">
                    <div class="relative">
                        <select v-model="currentLanguage" @change="changeLanguage" class="appearance-none bg-transparent border border-slate-300 rounded-md py-2 pl-3 pr-8 text-slate-700 focus:outline-none focus:ring-2 focus:ring-indigo-500">
                            <option value="en">English</option>
                            <option value="zh-CN">中文(简体)</option>
                            <option value="zh-TW">中文(繁體)</option>
                            <option value="ja">日本語</option>
                            <option value="th">ไทย</option>
                        </select>
                        <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-slate-700">
                           <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
                        </div>
                    </div>
                </div>
            </nav>
        </header>
        <!-- 
        <header class="bg-white/80 backdrop-blur-md shadow-sm sticky top-0 z-50">
            <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
                <div class="text-2xl font-bold gradient-text">
                    Molly Web3
                </div>
                <div class="flex items-center space-x-4">
                    <div class="relative">
                        <select v-model="currentLanguage" @change="changeLanguage" class="appearance-none bg-transparent border border-slate-300 rounded-md py-2 pl-3 pr-8 text-slate-700 focus:outline-none focus:ring-2 focus:ring-indigo-500">
                            <option value="en">English</option>
                            <option value="zh-CN">中文(简体)</option>
                            <option value="zh-TW">中文(繁體)</option>
                            <option value="ja">日本語</option>
                            <option value="th">ไทย</option>
                        </select>
                        <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-slate-700">
                           <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
                        </div>
                    </div>
                </div>
            </nav>
        </header>
        -->
        <main class="container mx-auto px-6 py-12">
            <section class="text-center py-20">
                <h1 class="text-4xl md:text-6xl font-extrabold mb-4">
                    {{ t('hero_title_1') }} <span class="gradient-text">Molly</span> {{ t('hero_title_2') }}
                </h1>
                <p class="text-lg md:text-xl text-slate-600 max-w-3xl mx-auto mb-8">
                    {{ t('hero_subtitle') }}
                </p>
                <div class="flex justify-center space-x-4">
                     <a href="#commercial" class="btn btn-primary">{{ t('commercial_use') }}</a>
                     <a href="#contribute" class="btn btn-secondary">{{ t('become_developer') }}</a>
                </div>
            </section>

            <section id="features" class="py-16">
                 <h2 class="section-title">{{ t('main_features') }}</h2>
                <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
                    <div class="card p-6 text-center">
                        <svg class="w-16 h-16 mx-auto mb-4 text-indigo-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
                        <h3 class="text-xl font-semibold mb-2">{{ t('feature_concurrency') }}</h3>
                        <p class="text-slate-600">{{ t('feature_concurrency_desc') }}</p>
                    </div>
                    <div class="card p-6 text-center">
                         <svg class="w-16 h-16 mx-auto mb-4 text-indigo-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.684 13.342C8.886 12.938 9 12.482 9 12s-.114-.938-.316-1.342m0 2.684a3 3 0 110-2.684m0 2.684l6.632 3.316m-6.632-6l6.632-3.316m0 0a3 3 0 105.367-2.684 3 3 0 00-5.367 2.684zm0 9.368a3 3 0 105.367 2.684 3 3 0 00-5.367-2.684z"></path></svg>
                        <h3 class="text-xl font-semibold mb-2">{{ t('feature_multichain') }}</h3>
                        <p class="text-slate-600">{{ t('feature_multichain_desc') }}</p>
                    </div>
                    <div class="card p-6 text-center">
                        <svg class="w-16 h-16 mx-auto mb-4 text-indigo-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"></path></svg>
                        <h3 class="text-xl font-semibold mb-2">{{ t('feature_tech') }}</h3>
                        <p class="text-slate-600">{{ t('feature_tech_desc') }}</p>
                    </div>
                    <div class="card p-6 text-center">
                        <svg class="w-16 h-16 mx-auto mb-4 text-indigo-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                        <h3 class="text-xl font-semibold mb-2">{{ t('feature_progress') }}</h3>
                        <p class="text-slate-600">{{ t('feature_progress_desc') }}</p>
                    </div>
                </div>
            </section>
            
            <section id="modules" class="py-16 bg-slate-100 -mx-6 px-6">
                <h2 class="section-title">{{ t('core_modules') }}</h2>
                <div class="max-w-4xl mx-auto">
                    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 text-center">
                        <div v-for="module in modules" :key="module" class="bg-white p-4 rounded-lg shadow-sm hover:shadow-md transition-shadow">
                            <p class="font-semibold text-slate-700">{{ module }}</p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="architecture" class="py-16">
                <h2 class="section-title">{{ t('tech_architecture') }}</h2>
                <div class="grid md:grid-cols-2 gap-8 items-start">
                    <div class="card p-6">
                        <h3 class="text-2xl font-bold mb-4 gradient-text">{{ t('system_architecture') }}</h3>
                        <p class="mb-4">{{ t('system_architecture_desc') }}</p>
                        <ul class="list-disc list-inside space-y-2 text-slate-600">
                           <li>{{ t('comm_mode') }}: {{ t('comm_mode_desc') }}</li>
                           <li>{{ t('kafka_security') }}: {{ t('kafka_security_desc') }}</li>
                           <li>{{ t('wallet_management') }}: {{ t('wallet_management_desc') }}</li>
                        </ul>
                    </div>
                    <div class="card p-6">
                        <h3 class="text-2xl font-bold mb-4 gradient-text">{{ t('security_mechanisms') }}</h3>
                         <ul class="list-disc list-inside space-y-2 text-slate-600">
                           <li>{{ t('accounting_security') }}: {{ t('accounting_security_desc') }}</li>
                           <li>{{ t('code_security') }}: {{ t('code_security_desc') }}</li>
                           <li>{{ t('system_security') }}: {{ t('system_security_desc') }}</li>
                           <li>{{ t('monitoring_mechanism') }}: {{ t('monitoring_mechanism_desc') }}</li>
                           <li>{{ t('risk_score') }}: {{ t('risk_score_desc') }}</li>
                        </ul>
                    </div>
                </div>
            </section>
            
             <section id="key-functions" class="py-16 bg-slate-100 -mx-6 px-6">
                <h2 class="section-title">{{ t('key_functions') }}</h2>
                <div class="max-w-6xl mx-auto grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <div v-for="func in keyFunctions" class="bg-white p-5 rounded-lg shadow-sm">
                        <h3 class="font-semibold text-lg text-indigo-600 mb-2">{{ t(func.title) }}</h3>
                        <p class="text-sm text-slate-600">{{ t(func.desc) }}</p>
                    </div>
                </div>
            </section>

            <section id="roadmap" class="py-16">
                <h2 class="section-title">{{ t('roadmap') }}</h2>
                <div class="max-w-4xl mx-auto relative">
                    <div class="border-l-4 border-indigo-200 absolute left-4 md:left-1/2 h-full transform md:-translate-x-1/2"></div>
                    <div v-for="(item, index) in roadmap" :key="index" class="mb-8 flex justify-between items-center w-full" :class="{'md:flex-row-reverse': index % 2 !== 0}">
                        <div class="order-1 md:w-5/12"></div>
                        <div class="z-20 flex items-center order-1 bg-indigo-500 shadow-xl w-8 h-8 rounded-full">
                            <h1 class="mx-auto font-semibold text-lg text-white">{{ index + 1 }}</h1>
                        </div>
                        <div class="order-1 bg-white rounded-lg shadow-xl w-full md:w-5/12 px-6 py-4 card">
                            <h3 class="font-bold text-gray-800 text-xl">{{ t(item) }}</h3>
                        </div>
                    </div>
                </div>
            </section>
            
            <section id="commercial" class="py-16 text-center bg-gray-800 text-white -mx-6 px-6">
                <h2 class="section-title text-white">
                    {{ t('commercial_model') }}
                    <span class="block w-20 h-1 bg-white mx-auto mt-2 rounded"></span>
                </h2>

                <div class="max-w-4xl mx-auto grid md:grid-cols-2 gap-8 items-center">
                     <div>
                        <p class="text-lg mb-4">{{ t('commercial_free') }}</p>
                        <p class="text-lg">{{ t('commercial_contact') }}</p>
                    </div>
                    <div>
                        <img src="https://img.picui.cn/free/2025/06/09/684638305198b.jpeg" alt="Telegram QR Code" class="mx-auto rounded-lg shadow-lg">
                    </div>
                </div>
            </section>
            
            <section id="support" class="py-16">
                 <div class="grid md:grid-cols-2 gap-12">
                     <div class="text-center">
                         <h2 class="section-title">{{ t('support_us') }}</h2>
                         <p class="mb-4">{{ t('support_us_desc') }}</p>
                         <div class="card p-6 inline-block">
                             <img src="https://img.picui.cn/free/2025/06/09/68463830538ca.jpeg" alt="Tron USDT QR Code" class="mx-auto rounded-lg mb-4">
                             <p class="font-semibold text-slate-800">USDT (TRON)</p>
                             <p class="text-sm text-slate-500 break-all">
                                UQBliPOVFKln0Jr-3Z8orRQ7rQcnjrmXq1cgxduIPHNryeYY
                             </p>
                         </div>
                     </div>
                     <div id="contribute" class="text-center">
                         <h2 class="section-title">{{ t('contribute') }}</h2>
                         <p class="mb-4">{{ t('contribute_desc') }}</p>
                         <a href="#commercial" class="btn btn-primary">{{ t('contact_us') }}</a>
                     </div>
                 </div>
            </section>
        </main>
        
        <footer class="bg-slate-800 text-slate-400 py-6">
            <div class="container mx-auto px-6 text-center">
                <p>&copy; 2025 Molly Web3 OpenSource Framework. All Rights Reserved.</p>
            </div>
        </footer>

    </div>

    <script>
        const translations = {
            en: {
                hero_title_1: "Build the Future of Web3 with",
                hero_title_2: "Framework",
                hero_subtitle: "A high-performance, modular, and secure open-source framework for building next-generation Web3 applications.",
                commercial_use: "Commercial Use",
                become_developer: "Become a Developer",
                main_features: "Core Features",
                feature_concurrency: "High Concurrency",
                feature_concurrency_desc: "Supports 100K to 1M QPS-level transaction throughput.",
                feature_multichain: "Multi-Chain Support",
                feature_multichain_desc: "Native support for ETH, Tron, Solana, and BTC.",
                feature_tech: "Technical Highlights",
                feature_tech_desc: "High-performance, modular, and security audit-friendly.",
                feature_progress: "Current Progress",
                feature_progress_desc: "Approx. 60% complete, stability and security verified.",
                core_modules: "10 Core Modules",
                tech_architecture: "Technical Architecture",
                system_architecture: "System Architecture",
                system_architecture_desc: "Based on JD Pay's architecture: Frontend + Nginx + Go Microservices + Kafka + Memcached + MySQL Master/Slave + PostgreSQL. Nginx for security validation and VIP user routing.",
                comm_mode: "IPC Mode",
                comm_mode_desc: "Secure inter-process communication mechanism for ETH nodes.",
                kafka_security: "Kafka Security",
                kafka_security_desc: "SASL+SCRAM mechanism for message queue security.",
                wallet_management: "Centralized Wallet Management",
                wallet_management_desc: "Auto wallet generation & key management via AWS-KMS/HSM. Batch creation of 1M wallets. 1 hot & 1 warm wallet per 10k wallets. AWS-KMS secure signing.",
                security_mechanisms: "Security Mechanisms",
                accounting_security: "Ledger Security",
                accounting_security_desc: "Triple-check mechanism (local DB/Log/external DB) with daily automated verification and reconciliation.",
                code_security: "Code Security",
                code_security_desc: "Automated hash verification for all files against an external database.",
                system_security: "System Security",
                system_security_desc: "6 sets of rapid response solutions and automated scripts for common risks.",
                monitoring_mechanism: "Fund Monitoring",
                monitoring_mechanism_desc: "Passive event-based mechanism for monitoring address fund changes, significantly reducing costs compared to polling.",
                risk_score: "Address Risk Score",
                risk_score_desc: "Security checks for deposit and withdrawal addresses to prevent contamination of core wallets and isolate illicit funds.",
                key_functions: "Key Functions",
                'kf_node_title': "Self-hosted Node Support",
                'kf_node_desc': "Supports self-hosting for ETH, Tron, Solana, and Bitcoin nodes.",
                'kf_wallet_title': "Hot/Warm Wallet Management",
                'kf_wallet_desc': "3/5 multi-signature mechanism for enhanced security.",
                'kf_withdrawal_title': "Large-Value Withdrawal Management",
                'kf_withdrawal_desc': "Supports a three-tier authorization system for large withdrawals.",
                'kf_gas_title': "Gas Fee Optimization",
                'kf_gas_desc': "Supports payment optimization for ETH and Tron.",
                'kf_user_security_title': "User Security",
                'kf_user_security_desc': "Email, SMS, Google 2FA, payment password verification, and multi-device login management.",
                'kf_nginx_title': "Nginx Distribution",
                'kf_nginx_desc': "Load balancer with dynamic configuration of Go processes and one-click Docker deployment.",
                'kf_vip_title': "VIP User Mechanism",
                'kf_vip_desc': "Dedicated server channels for VIP users, ensuring access during server attacks.",
                'kf_invite_title': "Invitation Incentive Mechanism",
                'kf_invite_desc': "Supports a reward system for user invitations.",
                'kf_kyc_title': "KYC Framework",
                'kf_kyc_desc': "Includes a framework to support Know Your Customer (KYC) procedures.",
                roadmap: "Development Roadmap",
                'rm_otc': "OTC Demo Scene",
                'rm_exchange': "External Exchange Demo (Binance, OKX)",
                'rm_dex_wallet': "Decentralized Wallet Demo",
                'rm_payment_agg': "Web3 Aggregated Payment Demo",
                'rm_fiat': "Fiat Exchange Demo",
                'rm_offline_payment': "Offline Business Crypto Payment Solution",
                'rm_concurrency_test': "Billion-User Concurrency Experiment",
                'rm_core_exchange': "Kernel-Level Exchange Demo",
                'rm_rwa': "RWA Asset On-chain & Trading Demo",
                'rm_dex': "DEX (Decentralized Exchange) Demo",
                'rm_hardware_wallet': "Hardware Wallet Payment Demo",
                'rm_financial': "Financial Products (Staking, Fixed Deposit)",
                'rm_stock_rwa': "Stock Asset RWA Demo",
                'rm_data_products': "Data-driven Products (Smart Money Tracking)",
                'rm_mixer': "Coin Mixer Demo",
                'rm_more_chains': "Support for More Chains & Tokens...",
                commercial_model: "Commercial Model",
                commercial_free: "Free for non-commercial use.",
                commercial_contact: "For commercial use, please contact us via Telegram.",
                support_us: "Sponsor Us",
                support_us_desc: "If you find this project helpful, consider a small donation.",
                contribute: "Contribute",
                contribute_desc: "We are looking for fellow developers to build the future of Web3 together. Join us!",
                contact_us: "Contact Us"
            },
            'zh-CN': {
                hero_title_1: "与 Molly 一同构建",
                hero_title_2: "Web3的未来",
                hero_subtitle: "一个高性能、模块化、安全可靠的开源框架，用于构建下一代Web3应用。",
                commercial_use: "商业合作",
                become_developer: "成为开发者",
                main_features: "核心功能",
                feature_concurrency: "高并发",
                feature_concurrency_desc: "支持10万至100万QPS级别的交易吞吐量。",
                feature_multichain: "多链支持",
                feature_multichain_desc: "原生支持 ETH / Tron / Solana / BTC。",
                feature_tech: "技术特点",
                feature_tech_desc: "高性能、模块化、安全审计友好。",
                feature_progress: "当前进度",
                feature_progress_desc: "已完成约60%，已完成稳定性与安全性验证。",
                core_modules: "十大核心模块",
                tech_architecture: "技术架构",
                system_architecture: "系统架构",
                system_architecture_desc: "参考京东支付架构：前端 + Nginx + Go 微服务 + Kafka + Memcached + MySQL 主从 + PostgreSQL。Nginx 负责安全校验及VIP用户分流。",
                comm_mode: "进程间通信",
                comm_mode_desc: "ETH节点安全控制的进程间通信机制。",
                kafka_security: "Kafka安全机制",
                kafka_security_desc: "采用SASL+SCRAM确保消息队列安全。",
                wallet_management: "中心化钱包管理",
                wallet_management_desc: "基于AWS-KMS/HSM的钱包自动生成及密钥管理，支持一次性生成百万钱包。每1万钱包对应1热1温钱包。具备AWS-KMS安全签名功能。",
                security_mechanisms: "安全机制",
                accounting_security: "记账安全",
                accounting_security_desc: "本库/Log/外库三重校验，每日自动对账。",
                code_security: "代码安全",
                code_security_desc: "全文件外库Hash自动化校验。",
                system_security: "系统安全",
                system_security_desc: "内置6套常规风险极速解决方案及自动化脚本。",
                monitoring_mechanism: "资金变化监控",
                monitoring_mechanism_desc: "采用被动式Event消息机制，摒弃高消耗轮询，大大降低成本。",
                risk_score: "地址RiskScore检测",
                risk_score_desc: "出入金地址安全检测，避免核心钱包地址污染，有效隔离涉恐涉毒资金。",
                key_functions: "关键功能",
                'kf_node_title': "支持自建节点",
                'kf_node_desc': "支持ETH/Tron/Solana/Bitcoin自建节点。",
                'kf_wallet_title': "热/温钱包管理",
                'kf_wallet_desc': "采用 3/5 多签机制，增强安全性。",
                'kf_withdrawal_title': "大额出金管理",
                'kf_withdrawal_desc': "支持三级授权出金管理。",
                'kf_gas_title': "Gas费用优化",
                'kf_gas_desc': "支持 ETH/Tron 支付优化。",
                'kf_user_security_title': "用户安全",
                'kf_user_security_desc': "邮箱、手机、Google 2FA、支付密码验证，多设备登陆管理。",
                'kf_nginx_title': "Nginx 分发",
                'kf_nginx_desc': "负载均衡，Go Process任意动态配置，Docker一键部署。",
                'kf_vip_title': "VIP用户机制",
                'kf_vip_desc': "独立服务器通道，确保VIP用户在攻击下仍可访问。",
                'kf_invite_title': "邀请激励机制",
                'kf_invite_desc': "支持用户邀请后的激励体系。",
                'kf_kyc_title': "KYC框架",
                'kf_kyc_desc': "内置支持KYC流程的框架。",
                roadmap: "开发路线图",
                'rm_otc': "OTC类Demo场景",
                'rm_exchange': "外接交易所类Demo (Binance, OKX)",
                'rm_dex_wallet': "去中心化钱包Demo",
                'rm_payment_agg': "Web3聚合支付Demo",
                'rm_fiat': "法币兑换类Demo",
                'rm_offline_payment': "线下商业数字货币支付解决方案",
                'rm_concurrency_test': "亿级用户并发实验",
                'rm_core_exchange': "内核级别交易所类Demo",
                'rm_rwa': "RWA资产上链及交易Demo",
                'rm_dex': "DEX (去中心化交易所) Demo",
                'rm_hardware_wallet': "硬件钱包支付Demo",
                'rm_financial': "金融产品计划 (币本位质押、定存)",
                'rm_stock_rwa': "股票资产RWA化Demo",
                'rm_data_products': "数据类资产产品 (聪明钱跟踪)",
                'rm_mixer': "混币器Demo",
                'rm_more_chains': "支持更多链及代币...",
                commercial_model: "商业模式",
                commercial_free: "非商业使用完全免费。",
                commercial_contact: "商业用途请通过 Telegram 联系我们。",
                support_us: "赞助我们",
                support_us_desc: "如果这个项目对您有帮助，可以考虑小额赞助。",
                contribute: "欢迎贡献",
                contribute_desc: "我们正在寻找志同道合的开发者，共同构建Web3的未来。加入我们！",
                contact_us: "联系我们"
            },
            'zh-TW': {
                hero_title_1: "與 Molly 一同構建",
                hero_title_2: "Web3的未來",
                hero_subtitle: "一個高效能、模組化、安全可靠的開源框架，用於構建下一代Web3應用。",
                commercial_use: "商業合作",
                become_developer: "成為開發者",
                main_features: "核心功能",
                feature_concurrency: "高並發",
                feature_concurrency_desc: "支援10萬至100萬QPS級別的交易吞吐量。",
                feature_multichain: "多鏈支援",
                feature_multichain_desc: "原生支援 ETH / Tron / Solana / BTC。",
                feature_tech: "技術特點",
                feature_tech_desc: "高效能、模組化、安全審計友好。",
                feature_progress: "當前進度",
                feature_progress_desc: "已完成約60%，已完成穩定性與安全性驗證。",
                core_modules: "十大核心模組",
                tech_architecture: "技術架構",
                system_architecture: "系統架構",
                system_architecture_desc: "參考京東支付架構：前端 + Nginx + Go 微服務 + Kafka + Memcached + MySQL 主從 + PostgreSQL。Nginx 負責安全校驗及VIP使用者分流。",
                comm_mode: "行程間通信",
                comm_mode_desc: "ETH節點安全控制的行程間通信機制。",
                kafka_security: "Kafka安全機制",
                kafka_security_desc: "採用SASL+SCRAM確保訊息佇列安全。",
                wallet_management: "中心化錢包管理",
                wallet_management_desc: "基於AWS-KMS/HSM的錢包自動生成及金鑰管理，支援一次性生成百萬錢包。每1萬錢包對應1熱1溫錢包。具備AWS-KMS安全簽名功能。",
                security_mechanisms: "安全機制",
                accounting_security: "記帳安全",
                accounting_security_desc: "本庫/Log/外庫三重校驗，每日自動對帳。",
                code_security: "程式碼安全",
                code_security_desc: "全檔案外庫Hash自動化校驗。",
                system_security: "系統安全",
                system_security_desc: "內建6套常規風險極速解決方案及自動化腳本。",
                monitoring_mechanism: "資金變化監控",
                monitoring_mechanism_desc: "採用被動式Event訊息機制，摒棄高消耗輪詢，大大降低成本。",
                risk_score: "地址RiskScore檢測",
                risk_score_desc: "出入金地址安全檢測，避免核心錢包地址污染，有效隔離涉恐涉毒資金。",
                key_functions: "關鍵功能",
                'kf_node_title': "支援自建節點",
                'kf_node_desc': "支援ETH/Tron/Solana/Bitcoin自建節點。",
                'kf_wallet_title': "熱/溫錢包管理",
                'kf_wallet_desc': "採用 3/5 多簽機制，增強安全性。",
                'kf_withdrawal_title': "大額出金管理",
                'kf_withdrawal_desc': "支援三級授權出金管理。",
                'kf_gas_title': "Gas費用優化",
                'kf_gas_desc': "支援 ETH/Tron 支付優化。",
                'kf_user_security_title': "用戶安全",
                'kf_user_security_desc': "信箱、手機、Google 2FA、支付密碼驗證，多裝置登陸管理。",
                'kf_nginx_title': "Nginx 分發",
                'kf_nginx_desc': "負載均衡，Go Process任意動態配置，Docker一鍵部署。",
                'kf_vip_title': "VIP用戶機制",
                'kf_vip_desc': "獨立伺服器通道，確保VIP用戶在攻擊下仍可訪問。",
                'kf_invite_title': "邀請激勵機制",
                'kf_invite_desc': "支援用戶邀請後的激勵體系。",
                'kf_kyc_title': "KYC框架",
                'kf_kyc_desc': "內建支援KYC流程的框架。",
                roadmap: "開發路線圖",
                'rm_otc': "OTC類Demo場景",
                'rm_exchange': "外接交易所類Demo (Binance, OKX)",
                'rm_dex_wallet': "去中心化錢包Demo",
                'rm_payment_agg': "Web3聚合支付Demo",
                'rm_fiat': "法幣兌換類Demo",
                'rm_offline_payment': "線下商業數位貨幣支付解決方案",
                'rm_concurrency_test': "億級用戶並發實驗",
                'rm_core_exchange': "內核級別交易所類Demo",
                'rm_rwa': "RWA資產上鏈及交易Demo",
                'rm_dex': "DEX (去中心化交易所) Demo",
                'rm_hardware_wallet': "硬體錢包支付Demo",
                'rm_financial': "金融產品計劃 (幣本位質押、定存)",
                'rm_stock_rwa': "股票資產RWA化Demo",
                'rm_data_products': "數據類資產產品 (聰明錢追蹤)",
                'rm_mixer': "混幣器Demo",
                'rm_more_chains': "支援更多鏈及代幣...",
                commercial_model: "商業模式",
                commercial_free: "非商業使用完全免費。",
                commercial_contact: "商業用途請透過 Telegram 聯絡我們。",
                support_us: "贊助我們",
                support_us_desc: "如果這個專案對您有幫助，可以考慮小額贊助。",
                contribute: "歡迎貢獻",
                contribute_desc: "我們正在尋找志同道合的開發者，共同構建Web3的未來。加入我們！",
                contact_us: "聯絡我們"
            },
            ja: {
                hero_title_1: "Mollyと共に構築する",
                hero_title_2: "Web3の未来",
                hero_subtitle: "次世代のWeb3アプリケーションを構築するための、高性能、モジュール式、安全なオープンソースフレームワーク。",
                commercial_use: "商用利用",
                become_developer: "開発者になる",
                main_features: "主な特徴",
                feature_concurrency: "高い同時実行性",
                feature_concurrency_desc: "10万〜100万QPSレベルのトランザクションスループットをサポート。",
                feature_multichain: "マルチチェーン対応",
                feature_multichain_desc: "ETH、Tron、Solana、BTCをネイティブサポート。",
                feature_tech: "技術的特徴",
                feature_tech_desc: "高性能、モジュール式、セキュリティ監査に優しい。",
                feature_progress: "現在の進捗",
                feature_progress_desc: "約60%完了、安定性とセキュリティは検証済み。",
                core_modules: "10のコアモジュール",
                tech_architecture: "技術アーキテクチャ",
                system_architecture: "システムアーキテクチャ",
                system_architecture_desc: "JD Payのアーキテクチャを参考に：フロントエンド + Nginx + Goマイクロサービス + Kafka + Memcached + MySQLマスター/スレーブ + PostgreSQL。Nginxはセキュリティ検証とVIPユーザールーティングを担当。",
                comm_mode: "プロセス間通信",
                comm_mode_desc: "ETHノードの安全なプロセス間通信メカニズム。",
                kafka_security: "Kafkaセキュリティ",
                kafka_security_desc: "メッセージキューのセキュリティを確保するSASL+SCRAMメカニズム。",
                wallet_management: "集中型ウォレット管理",
                wallet_management_desc: "AWS-KMS/HSMによるウォレット自動生成と鍵管理。100万ウォレットの一括作成。1万ウォレットごとに1つのホットウォレットと1つのウォームウォレット。AWS-KMSセキュア署名機能。",
                security_mechanisms: "セキュリティメカニズム",
                accounting_security: "台帳セキュリティ",
                accounting_security_desc: "三重チェックメカニズム（ローカルDB/ログ/外部DB）と毎日の自動検証・照合。",
                code_security: "コードセキュリティ",
                code_security_desc: "外部データベースに対する全ファイルの自動ハッシュ検証。",
                system_security: "システムセキュリティ",
                system_security_desc: "一般的なリスクに対する6つの迅速な対応ソリューションと自動化スクリプト。",
                monitoring_mechanism: "資金変動監視",
                monitoring_mechanism_desc: "ポーリングに代わるパッシブなイベントベースのメカニズムで、アドレスの資金変動を監視し、コストを大幅に削減。",
                risk_score: "アドレスリスクスコア",
                risk_score_desc: "入出金アドレスのセキュリティチェックにより、コアウォレットの汚染を防ぎ、不正資金を隔離。",
                key_functions: "主要機能",
                'kf_node_title': "自己ホスト型ノードのサポート",
                'kf_node_desc': "ETH、Tron、Solana、Bitcoinノードの自己ホスティングをサポート。",
                'kf_wallet_title': "ホット/ウォームウォレット管理",
                'kf_wallet_desc': "セキュリティを強化するための3/5マルチシグネチャメカニズム。",
                'kf_withdrawal_title': "高額出金管理",
                'kf_withdrawal_desc': "高額出金のための3段階の承認システムをサポート。",
                'kf_gas_title': "ガス料金の最適化",
                'kf_gas_desc': "ETHとTronの支払い最適化をサポート。",
                'kf_user_security_title': "ユーザーセキュリティ",
                'kf_user_security_desc': "メール、SMS、Google 2FA、支払いパスワード認証、マルチデバイスログイン管理。",
                'kf_nginx_title': "Nginx配信",
                'kf_nginx_desc': "Goプロセスの動的設定とワンクリックDockerデプロイメントを備えたロードバランサー。",
                'kf_vip_title': "VIPユーザーメカニズム",
                'kf_vip_desc': "VIPユーザー専用のサーバーチャネルで、サーバー攻撃時もアクセスを保証。",
                'kf_invite_title': "招待インセンティブメカニズム",
                'kf_invite_desc': "ユーザー招待に対する報酬システムをサポート。",
                'kf_kyc_title': "KYCフレームワーク",
                'kf_kyc_desc': "顧客確認（KYC）手続きをサポートするフレームワークを内蔵。",
                roadmap: "開発ロードマップ",
                'rm_otc': "OTCデモシーン",
                'rm_exchange': "外部取引所デモ (Binance, OKX)",
                'rm_dex_wallet': "分散型ウォレットデモ",
                'rm_payment_agg': "Web3集約決済デモ",
                'rm_fiat': "法定通貨交換デモ",
                'rm_offline_payment': "オフラインビジネス暗号通貨決済ソリューション",
                'rm_concurrency_test': "1億ユーザー同時接続実験",
                'rm_core_exchange': "カーネルレベル取引所デモ",
                'rm_rwa': "RWA資産オンチェーン＆取引デモ",
                'rm_dex': "DEX (分散型取引所) デモ",
                'rm_hardware_wallet': "ハードウェアウォレット決済デモ",
                'rm_financial': "金融商品（ステーキング、定期預金）",
                'rm_stock_rwa': "株式資産RWAデモ",
                'rm_data_products': "データ駆動型商品（スマートマネートラッキング）",
                'rm_mixer': "コインミキサーデモ",
                'rm_more_chains': "さらなるチェーン＆トークンのサポート...",
                commercial_model: "商用モデル",
                commercial_free: "非商用利用は無料です。",
                commercial_contact: "商用利用については、Telegramでお問い合わせください。",
                support_us: "スポンサー",
                support_us_desc: "このプロジェクトが役に立ったと思われましたら、少額の寄付をご検討ください。",
                contribute: "貢献する",
                contribute_desc: "私たちはWeb3の未来を共に築く開発者を募集しています。ぜひご参加ください！",
                contact_us: "お問い合わせ"
            },
            th: {
                hero_title_1: "สร้างอนาคตของ Web3 ด้วย",
                hero_title_2: "เฟรมเวิร์ก",
                hero_subtitle: "เฟรมเวิร์กโอเพนซอร์สที่มีประสิทธิภาพสูง เป็นโมดูล และปลอดภัย สำหรับสร้างแอปพลิเคชัน Web3 ยุคถัดไป",
                commercial_use: "การใช้งานเชิงพาณิชย์",
                become_developer: "ร่วมเป็นนักพัฒนา",
                main_features: "คุณสมบัติหลัก",
                feature_concurrency: "รองรับการทำงานพร้อมกันสูง",
                feature_concurrency_desc: "รองรับปริมาณธุรกรรมระดับ 100K ถึง 1M QPS",
                feature_multichain: "รองรับหลายเชน",
                feature_multichain_desc: "รองรับ ETH, Tron, Solana, และ BTC โดยกำเนิด",
                feature_tech: "จุดเด่นทางเทคนิค",
                feature_tech_desc: "ประสิทธิภาพสูง, เป็นโมดูล, และเป็นมิตรต่อการตรวจสอบความปลอดภัย",
                feature_progress: "ความคืบหน้าปัจจุบัน",
                feature_progress_desc: "เสร็จสิ้นแล้วประมาณ 60%, ผ่านการตรวจสอบความเสถียรและความปลอดภัยแล้ว",
                core_modules: "10 โมดูลหลัก",
                tech_architecture: "สถาปัตยกรรมทางเทคนิค",
                system_architecture: "สถาปัตยกรรมระบบ",
                system_architecture_desc: "อ้างอิงสถาปัตยกรรมของ JD Pay: Frontend + Nginx + Go Microservices + Kafka + Memcached + MySQL Master/Slave + PostgreSQL Nginx สำหรับการตรวจสอบความปลอดภัยและการจัดเส้นทางผู้ใช้ VIP",
                comm_mode: "การสื่อสารระหว่างโพรเซส",
                comm_mode_desc: "กลไกการสื่อสารระหว่างโพรเซสที่ปลอดภัยสำหรับโหนด ETH",
                kafka_security: "ความปลอดภัยของ Kafka",
                kafka_security_desc: "กลไก SASL+SCRAM เพื่อความปลอดภัยของคิวข้อความ",
                wallet_management: "การจัดการวอลเล็ตแบบรวมศูนย์",
                wallet_management_desc: "สร้างวอลเล็ตและจัดการคีย์อัตโนมัติผ่าน AWS-KMS/HSM สร้างวอลเล็ตได้ 1 ล้านใบพร้อมกัน มี 1 hot & 1 warm wallet ต่อ 10k wallets ฟังก์ชันการลงนามที่ปลอดภัยของ AWS-KMS",
                security_mechanisms: "กลไกความปลอดภัย",
                accounting_security: "ความปลอดภัยของบัญชี",
                accounting_security_desc: "กลไกการตรวจสอบสามชั้น (DB ท้องถิ่น/Log/DB ภายนอก) พร้อมการตรวจสอบและกระทบยอดอัตโนมัติรายวัน",
                code_security: "ความปลอดภัยของโค้ด",
                code_security_desc: "การตรวจสอบแฮชของไฟล์ทั้งหมดกับฐานข้อมูลภายนอกโดยอัตโนมัติ",
                system_security: "ความปลอดภัยของระบบ",
                system_security_desc: "โซลูชันและสคริปต์อัตโนมัติ 6 ชุดสำหรับการตอบสนองต่อความเสี่ยงทั่วไปอย่างรวดเร็ว",
                monitoring_mechanism: "การตรวจสอบความเคลื่อนไหวของเงินทุน",
                monitoring_mechanism_desc: "ใช้กลไก Event-based แบบพาสซีฟเพื่อตรวจสอบการเปลี่ยนแปลงเงินทุนของที่อยู่ ช่วยลดต้นทุนได้อย่างมากเมื่อเทียบกับการ polling",
                risk_score: "การตรวจจับ Risk Score ของที่อยู่",
                risk_score_desc: "การตรวจสอบความปลอดภัยของที่อยู่สำหรับการฝากและถอนเพื่อป้องกันการปนเปื้อนของวอลเล็ตหลักและแยกเงินทุนที่ผิดกฎหมาย",
                key_functions: "ฟังก์ชันสำคัญ",
                'kf_node_title': "รองรับการตั้งโหนดเอง",
                'kf_node_desc': "รองรับการโฮสต์โหนด ETH, Tron, Solana, และ Bitcoin ด้วยตนเอง",
                'kf_wallet_title': "การจัดการ Hot/Warm Wallet",
                'kf_wallet_desc': "กลไก multi-signature แบบ 3/5 เพื่อความปลอดภัยที่สูงขึ้น",
                'kf_withdrawal_title': "การจัดการการถอนเงินจำนวนมาก",
                'kf_withdrawal_desc': "รองรับระบบการอนุมัติสามระดับสำหรับการถอนเงินจำนวนมาก",
                'kf_gas_title': "การปรับค่า Gas ให้เหมาะสม",
                'kf_gas_desc': "รองรับการปรับการชำระเงินสำหรับ ETH และ Tron ให้เหมาะสม",
                'kf_user_security_title': "ความปลอดภัยของผู้ใช้",
                'kf_user_security_desc': "การยืนยันผ่านอีเมล, SMS, Google 2FA, รหัสผ่านการชำระเงิน และการจัดการการเข้าสู่ระบบหลายอุปกรณ์",
                'kf_nginx_title': "การกระจายด้วย Nginx",
                'kf_nginx_desc': "Load balancer พร้อมการกำหนดค่า Go processes แบบไดนามิก และการปรับใช้ Docker เพียงคลิกเดียว",
                'kf_vip_title': "กลไกผู้ใช้ VIP",
                'kf_vip_desc': "ช่องทางเซิร์ฟเวอร์เฉพาะสำหรับผู้ใช้ VIP เพื่อให้แน่ใจว่าสามารถเข้าถึงได้ระหว่างการโจมตีเซิร์ฟเวอร์",
                'kf_invite_title': "กลไกการจูงใจด้วยการเชิญ",
                'kf_invite_desc': "รองรับระบบรางวัลสำหรับการเชิญผู้ใช้",
                'kf_kyc_title': "เฟรมเวิร์ก KYC",
                'kf_kyc_desc': "มีเฟรมเวิร์กเพื่อรองรับกระบวนการ Know Your Customer (KYC)",
                roadmap: "แผนการพัฒนา",
                'rm_otc': "สถานการณ์สาธิต OTC",
                'rm_exchange': "สถานการณ์สาธิตการแลกเปลี่ยนภายนอก (Binance, OKX)",
                'rm_dex_wallet': "สถานการณ์สาธิตวอลเล็ตแบบกระจายอำนาจ",
                'rm_payment_agg': "สถานการณ์สาธิตการชำระเงินแบบรวมของ Web3",
                'rm_fiat': "สถานการณ์สาธิตการแลกเปลี่ยนเงินเฟียต",
                'rm_offline_payment': "โซลูชันการชำระเงินด้วยสกุลเงินดิจิทัลสำหรับธุรกิจออฟไลน์",
                'rm_concurrency_test': "การทดลองการทำงานพร้อมกันของผู้ใช้ระดับพันล้านคน",
                'rm_core_exchange': "สถานการณ์สาธิตการแลกเปลี่ยนระดับเคอร์เนล",
                'rm_rwa': "สถานการณ์สาธิตการนำสินทรัพย์ RWA ขึ้นเชนและการซื้อขาย",
                'rm_dex': "สถานการณ์สาธิต DEX (การแลกเปลี่ยนแบบกระจายอำนาจ)",
                'rm_hardware_wallet': "สถานการณ์สาธิตการชำระเงินด้วยฮาร์ดแวร์วอลเล็ต",
                'rm_financial': "ผลิตภัณฑ์ทางการเงิน (Staking, เงินฝากประจำ)",
                'rm_stock_rwa': "สถานการณ์สาธิตสินทรัพย์หุ้นแบบ RWA",
                'rm_data_products': "ผลิตภัณฑ์ข้อมูล (การติดตาม Smart Money)",
                'rm_mixer': "สถานการณ์สาธิต Coin Mixer",
                'rm_more_chains': "รองรับเชนและโทเค็นเพิ่มเติม...",
                commercial_model: "รูปแบบเชิงพาณิชย์",
                commercial_free: "ใช้งานฟรีสำหรับการใช้งานที่ไม่ใช่เชิงพาณิชย์",
                commercial_contact: "สำหรับการใช้งานเชิงพาณิชย์ โปรดติดต่อเราผ่าน Telegram",
                support_us: "สนับสนุนเรา",
                support_us_desc: "หากคุณพบว่าโครงการนี้มีประโยชน์ โปรดพิจารณาการบริจาคเล็กน้อย",
                contribute: "ร่วมสนับสนุน",
                contribute_desc: "เรากำลังมองหานักพัฒนาที่มีอุดมการณ์เดียวกันเพื่อสร้างอนาคตของ Web3 ไปด้วยกัน เข้าร่วมกับเรา!",
                contact_us: "ติดต่อเรา"
            }
        };

        const { createApp, ref, onMounted } = Vue;

        createApp({
            setup() {
                const currentLanguage = ref('en');

                const modules = ref([
                    'user-service', 'billing-service', 'moneyin-service', 'moneyout-service', 'kms-service', 
                    'admin-service', 'arch-service', 'system-doctor', 'system-security', 'log-service'
                ]);

                const keyFunctions = ref([
                    { title: 'kf_node_title', desc: 'kf_node_desc' },
                    { title: 'kf_wallet_title', desc: 'kf_wallet_desc' },
                    { title: 'kf_withdrawal_title', desc: 'kf_withdrawal_desc' },
                    { title: 'kf_gas_title', desc: 'kf_gas_desc' },
                    { title: 'kf_user_security_title', desc: 'kf_user_security_desc' },
                    { title: 'kf_nginx_title', desc: 'kf_nginx_desc' },
                    { title: 'kf_vip_title', desc: 'kf_vip_desc' },
                    { title: 'kf_invite_title', desc: 'kf_invite_desc' },
                    { title: 'kf_kyc_title', desc: 'kf_kyc_desc' },
                ]);
                
                const roadmap = ref([
                   'rm_otc', 'rm_exchange', 'rm_dex_wallet', 'rm_payment_agg', 'rm_fiat',
                   'rm_offline_payment', 'rm_concurrency_test', 'rm_core_exchange', 'rm_rwa', 'rm_dex',
                   'rm_hardware_wallet', 'rm_financial', 'rm_stock_rwa', 'rm_data_products', 'rm_mixer', 'rm_more_chains'
                ]);

                const t = (key) => {
                    return translations[currentLanguage.value][key] || key;
                };

                const changeLanguage = () => {
                    document.documentElement.lang = currentLanguage.value.split('-')[0];
                };

                onMounted(() => {
                    // Set initial language from browser or default to English
                    const browserLang = navigator.language || navigator.userLanguage;
                    if (translations[browserLang]) {
                        currentLanguage.value = browserLang;
                    } else if (translations[browserLang.split('-')[0]]) {
                        currentLanguage.value = browserLang.split('-')[0];
                    } else {
                        currentLanguage.value = 'en';
                    }
                    changeLanguage();
                });

                return {
                    currentLanguage,
                    t,
                    changeLanguage,
                    modules,
                    keyFunctions,
                    roadmap
                };
            }
        }).mount('#app');
    </script>

</body>
</html>
