# Context Map — `avnit` GitHub Repositories

Master architecture & deployment context map across all cloned repositories at `C:\Users\abamb\repos`. For each repository this documents **(1)** the core application, **(2)** container / cloud applications it can run as, and **(3)** database connections required.

**Totals:** 125 repositories mapped — 57 original, 68 forks. Generated 2026-08-13.

## Legend

- **Type:** `orig` = original repo, `fork` = fork of an upstream project.
- **Cloud/Deploy:** detected target platforms and packaging.
- **Databases:** detected datastore drivers / connection strings.

## Portfolio themes

- **Google Cloud AI agents (ADK / Vertex AI / Gemini):** `adk-samples`, `adk-samples2`, `agent-identity`, `agent-identity-3`, `agents-starter`, `ai-agent`, `ai-agent-deploy-ae`, `antigravity-adk-examples`, `demo-agent-gateway-agent-id`, `geminiCoder`, `geminipoc`, `generative-ai`, `hermes-agent-playlist`, `my-chat-agent`, `new-agent`, `openclaw-trading-agent`, `TradingAgents`
- **Identity & access (workforce/workload identity, vault):** `auto-identity-remove`, `evilginx2`, `mediastack`, `python-flask-ext-api-example`, `terraform-google-workload-identity-federation`, `vault`, `vault-kms`, `vault-kubernetes`, `vault-storage`, `vault-storage-1`, `workforceidentity`
- **Homelab / IaC / self-hosting:** `arrstack`, `cheat-sheets`, `chef-certification-study-guides`, `ckg-app-main`, `claude-new-repo`, `Docker-Templates-Unraid`, `homelab1`, `homelab2`, `infra`, `jenkins-course`, `JimsGarage`, `Mastering-Ubuntu-Server-Fourth-Edition`, `n8n-pi`, `nvm`, `pihole-ha-dns`, `pimox7`, `scc-iac-scanning`, `terraform-docs-samples`, `terraform-google-influx`, `Terraforms`, `trustworthyml-ai.github.io`, `VPC-SC-Demo-Terraform`
- **Finance & trading tools:** `ContractWork`, `optionPricing`, `PricingConsole`, `Project`, `python-collections-budget`, `stock-trading-assistance`, `StockSelector`
- **Web / frontend / static sites:** `antigravity-playlist`, `asb-gear-storefront`, `boilerplates`, `create-html5-boilerplate`, `EGroovy`, `flame`, `frontend`, `google-cloud-ai-demos`, `homepage`, `html5-boilerplate`, `reactjs-webpage`, `reactjsWebs`, `salespage`
- **Security & pentest tooling:** `gophish`, `Mastering-Kali-Linux-for-Advanced-Penetration-Testing-4E`, `pico-ducky`, `project-keyword-spotter`, `USB-Uncensored-LLM`
- **Learning / course / book material:** `Developing-IoT-Projects-with-ESP32-2nd-edition`, `General_Handouts`, `handson-mlp`, `Making-Java-Groovy`, `Mastering-Embedded-Linux-Development`, `python-4-everyone-hw-2252026`, `Python-for-everyone`, `python-scraping`, `XCS224N-A4`, `XCS224N-Handouts`
- **Other:** `AdvancedGroovy`, `Angular-demo-repo`, `ansible-for-devops`, `antigravity-hidden-features`, `arduino4everyone`, `asb-gear-ops`, `askhr`, `casaos-scripts`, `cloud-run-app`, `esp-idf`, `ESP32-A2DP`, `esphome`, `fastapi`, `financial-app`, `geopm`, `GLSC`, `griffon-eclipse-support-plugin`, `Groovy`, `groovy-core`, `hackathon`, `https---github.com-avnit-ContractWork`, `integration`, `IPTV-Player-sample`, `it-tools`, `mojo`, `nodejs`, `openwrt`, `opnsense-config`, `pop-kustomize`, `pve-moosefs`, `pytube`, `SampleCodeStar`, `signal-rgb`, `SwiftCalc`, `swot`, `user-security`, `webretro`, `wizlights-mcp-server`, `WLED`, `xonora-ios`

## Repository summary

| Repository | Type | Lang | Core application | Cloud / Deploy | Databases |
|---|---|---|---|---|---|
| `adk-samples` | fork | Python | A collection of sample agents built with Agent Development (ADK) | Vertex AI/Cloudflare Workers | — |
| `adk-samples2` | orig | Python | Agent Development Kit (ADK) Samples | Vertex AI/Google Cloud Run/GKE | — |
| `AdvancedGroovy` | fork | Groovy | Examples for my NFJS Advanced Groovy: Tips and Tricks talk | — | — |
| `agent-identity` | orig | Jupyter Notebook | Policy Agent — ADK + Agent Identity + Gemini Enterprise | Vertex AI/BigQuery | BigQuery |
| `agent-identity-3` | orig·priv | Python | ADK agent using Vertex AI Agent Engine Agent Identity to fetch policy docs from GCS; deplo | Vertex AI | — |
| `agents-starter` | fork | TypeScript | A starter kit for building ai agents on Cloudflare | Cloudflare Workers/Vercel | SQLite |
| `ai-agent` | orig | Python | ai-agent-testing | Vertex AI/Google Cloud Run | SQLite |
| `ai-agent-deploy-ae` | orig | Jupyter Notebook | A collection of production-ready Generative AI Agent templates built for Google Cloud. It  | Vertex AI/Google Cloud Run/Firebase/BigQuery | PostgreSQL/BigQuery |
| `Angular-demo-repo` | orig | - | Angular-demo-repo | — | — |
| `ansible-for-devops` | fork | Python | Ansible for DevOps examples. | GKE/AWS/Ansible/Heroku | MySQL/SQLite/Elasticsearch |
| `antigravity-adk-examples` | orig | Python | ADK examples by hermes Agent for Antigravity cli | Vertex AI/Google Cloud Run | — |
| `antigravity-hidden-features` | orig | - | YouTube video: 8 Hidden Google Antigravity Features Nobody Talked About — script, thumbnai | Vertex AI | — |
| `antigravity-playlist` | orig | HTML | Curated YouTube playlist of 20 best Google Antigravity & Antigravity CLI videos | GitHub Pages | — |
| `arduino4everyone` | orig | Python | arduino4everyone | — | — |
| `arrstack` | orig | HCL | Project Documentation | Azure/Cloudflare Workers/Terraform | — |
| `asb-gear-ops` | orig·priv | Python | Private: ASB Gear sourcing RFQs, supplier vetting, and Amazon launch compliance docs | Ansible | — |
| `asb-gear-storefront` | orig | HTML | ASB Gear — pre-launch storefront for the ASB Solutions Group hardware line (USB-C dock + m | Cloudflare Workers/Netlify/GitHub Pages | — |
| `askhr` | orig | - | — | — | — |
| `auto-identity-remove` | fork | JavaScript | Automated data broker opt-out runner — removes your personal info from 30+ people-search s | Cloudflare Workers | — |
| `boilerplates` | fork | Python | This is my personal template collection. Here you'll find templates, and configurations fo | GKE/Cloudflare Workers/Terraform/Ansible | PostgreSQL/MySQL/InfluxDB |
| `casaos-scripts` | fork | Shell | These are scripts that are created for the BigBearYouTube Channel | — | SQLite/Vector |
| `cheat-sheets` | fork | - | This is my personal knowledge-base. Here you'll find code-snippets, technical documentatio | GKE/Ansible | — |
| `chef-certification-study-guides` | fork | - | So you want to get Chef Certified. Well, I'm here to help. | AWS/Azure/Terraform | — |
| `ckg-app-main` | orig·priv | Go Template | — | GKE/Terraform | MySQL/Cassandra/Elasticsearch |
| `claude-new-repo` | orig | - | claude-new-repo | Google Cloud Run/Terraform | — |
| `cloud-run-app` | orig·priv | Shell | cloud-run-app | Google Cloud Run | — |
| `ContractWork` | orig | Python | Class material for python finance 101 | — | Redis/SQLite |
| `create-html5-boilerplate` | fork | JavaScript | npx quick start for html5-boilerplate | — | — |
| `demo-agent-gateway-agent-id` | orig | Jupyter Notebook | demo-agent-gateway-agent-id | Vertex AI/Azure/Terraform | — |
| `Developing-IoT-Projects-with-ESP32-2nd-edition` | fork | C | Developing IoT Projects with ESP32, 2nd edition - Published by Packt | AWS/Terraform | — |
| `Docker-Templates-Unraid` | fork | - | Unraid docker templates | — | PostgreSQL/MySQL |
| `EGroovy` | orig | Ruby | Features, usage and installation instructions are [summarized on the homepage][home]. | AWS | PostgreSQL/MySQL/SQLite/Cassandra |
| `esp-idf` | fork | C | Espressif IoT Development Framework. Official development framework for Espressif SoCs. | — | Redis |
| `ESP32-A2DP` | fork | C++ | A Simple ESP32 Bluetooth A2DP Library (to implement a Music Receiver or Sender) that suppo | — | — |
| `esphome` | fork | - | ESPHome | — | — |
| `evilginx2` | fork | Go | Standalone man-in-the-middle attack framework used for phishing login credentials along wi | Azure/Cloudflare Workers/Firebase/BigQuery | SQLite/Firestore/BigQuery |
| `fastapi` | fork | Python | FastAPI framework, high performance, easy to learn, fast to code, ready for production | Cloudflare Workers | PostgreSQL/Redis/SQLite/Supabase |
| `financial-app` | orig | Python | financial-app | — | — |
| `flame` | fork | TypeScript | Flame is self-hosted startpage for your server. Easily manage your apps and bookmarks with | GKE | SQLite |
| `frontend` | fork | TypeScript | :lollipop: Frontend for Home Assistant | Cloudflare Workers/Netlify | — |
| `geminiCoder` | fork | TypeScript | Create apps with Gemini | Vertex AI/Vercel | — |
| `geminipoc` | orig | HCL | db                                88 | Vertex AI/Google Cloud Run/GKE/Firebase | PostgreSQL/MySQL/Cassandra/Firestore |
| `General_Handouts` | fork | TeX | Course Handouts | — | — |
| `generative-ai` | fork | Jupyter Notebook | Sample code and notebooks for Generative AI on Google Cloud, with Gemini on Vertex AI | Vertex AI/Google Cloud Run/GKE/Firebase | SQLite/BigQuery |
| `geopm` | fork | C++ | Global Extensible Open Power Manager | GKE | SQLite |
| `GLSC` | orig | - | — | — | — |
| `google-cloud-ai-demos` | fork | TypeScript | This repository contains the frontend and backend code for the "AI Demos" demos. | Vertex AI/Google Cloud Run/BigQuery | Redis/BigQuery |
| `gophish` | fork | Go | Open-Source Phishing Toolkit | Vertex AI/GKE/AWS/Azure | MySQL/MongoDB/Redis/SQLite |
| `griffon-eclipse-support-plugin` | fork | Groovy | Keeps Eclipse files up to date | — | — |
| `Groovy` | orig | JavaScript | The purpose of this project is to call the google API and return a valid results. I only n | — | — |
| `groovy-core` | fork | Java | Groovy language Git repository | GKE | MySQL |
| `hackathon` | orig | Python | — | Vertex AI/Google Cloud Run/GKE/Terraform | SQLite |
| `handson-mlp` | fork | Jupyter Notebook | A series of Jupyter notebooks that walk you through the fundamentals of Machine Learning a | GKE | Neo4j/Vector |
| `hermes-agent-playlist` | orig | HTML | test | GitHub Pages | — |
| `homelab1` | orig | HTML | homelab-selfhosted-stack | Cloudflare Workers/Terraform/Vercel/Netlify | — |
| `homelab2` | fork | HCL | This is my entire homelab documentation files. Here you'll find notes, setups, and configu | GKE/Azure/Cloudflare Workers/Terraform | PostgreSQL/MySQL/InfluxDB |
| `homepage` | fork | JavaScript | A highly customizable homepage (or startpage / application dashboard) with Docker and serv | GKE/AWS/Azure/Cloudflare Workers | InfluxDB |
| `html5-boilerplate` | fork | JavaScript | A professional front-end template for building fast, robust, and adaptable web apps or sit | — | — |
| `https---github.com-avnit-ContractWork` | orig | Jupyter Notebook | — | — | — |
| `infra` | orig | HCL | Infra repo | GKE/Terraform | — |
| `integration` | fork | Python | HACS gives you a powerful UI to handle downloads of all your custom needs. | AWS/Azure/Cloudflare Workers | Redis/Elasticsearch/InfluxDB |
| `IPTV-Player-sample` | fork | JavaScript | 📺 Watch 8000+ publicly available IPTV channels within your browser | GKE/Firebase | Firestore |
| `it-tools` | fork | Vue | Collection of handy online tools for developers, with great UX. | BigQuery/Vercel/Netlify | BigQuery |
| `jenkins-course` | fork | Shell | This is the repository with all the resources for the Jenkins training on Udemy | — | PostgreSQL |
| `JimsGarage` | fork | Shell | Homelab Goodies | GKE/Cloudflare Workers/Ansible | PostgreSQL/MySQL/MongoDB/Redis |
| `Making-Java-Groovy` | fork | Groovy | Source code for Manning book "Making Java Groovy" | — | — |
| `Mastering-Embedded-Linux-Development` | fork | C | Mastering Embedded Linux Development Fourth Edition, published by Packt | — | — |
| `Mastering-Kali-Linux-for-Advanced-Penetration-Testing-4E` | fork | Python | Mastering Kali Linux for Advanced Penetration Testing 4E published by Packt | — | — |
| `Mastering-Ubuntu-Server-Fourth-Edition` | fork | HCL | Mastering Ubuntu Server, Fourth Edition, Published by Packt | GKE/AWS/Terraform | — |
| `mediastack` | fork | Shell | The ultimate Docker Compose files and configs to build your desired media stack, quickly a | GKE/Cloudflare Workers/Terraform | PostgreSQL |
| `mojo` | fork | Perl | Mojolicious - Perl real-time web framework | — | — |
| `my-chat-agent` | orig | TypeScript | 🤖 Chat Agent Starter Kit | Cloudflare Workers/Terraform/Vercel | — |
| `n8n-pi` | fork | Shell | Tools and Images to Build a Raspberry Pi n8n server | GKE | — |
| `new-agent` | orig·priv | Python | Simple ReAct agent | Vertex AI/Google Cloud Run/BigQuery/Terraform | BigQuery |
| `nodejs` | orig | JavaScript | — | — | — |
| `nvm` | fork | Shell | Node Version Manager - Simple bash script to manage multiple active node.js versions | Ansible | — |
| `openclaw-trading-agent` | orig | - | AI trading agent for OpenClaw using Claude Agent SDK — market data, portfolio management,  | — | — |
| `openwrt` | fork | C | This repository is a mirror of https://git.openwrt.org/openwrt/openwrt.git It is for refer | — | — |
| `opnsense-config` | orig | - | configuration for opnsense router | — | — |
| `optionPricing` | orig | CSS | The option price calculator | Azure/Vercel | — |
| `pico-ducky` | fork | Python | Create a USB Rubber Ducky like device using a Raspberry PI Pico | Vertex AI/GKE/AWS/Azure | PostgreSQL/MySQL/MongoDB/Redis |
| `pihole-ha-dns` | orig·priv | Shell | Highly-available Pi-hole DNS via VRRP (keepalived) + DNS-over-TLS (Stubby). One Ansible pl | Cloudflare Workers/Ansible | — |
| `pimox7` | fork | Shell | Proxmox V7 for Raspberry Pi | — | — |
| `pop-kustomize` | fork | Python | End-to-End Google Cloud CI/CD example repo and tutorial | Google Cloud Run/GKE | — |
| `PricingConsole` | orig | C# | PricingConsole | Azure | — |
| `Project` | orig | R | SG 40 FINC 621 Trading project | — | — |
| `project-keyword-spotter` | fork | Python | Audio Keyphrase Detector | — | — |
| `pve-moosefs` | fork | Perl | MooseFS Storage Plugin for Proxmox Virtual Environment (PVE) | — | — |
| `python-4-everyone-hw-2252026` | orig | - | Python HW and Project | — | — |
| `python-collections-budget` | fork | Python | In this project we’ll process spending data into different types of Python collections. Th | — | — |
| `python-flask-ext-api-example` | fork | Python | A simple Flask front-end web app accessing the Airthings ext-api using the requests_oauthl | — | — |
| `Python-for-everyone` | orig | Jupyter Notebook | This is for the class | Terraform | SQLite |
| `python-scraping` | fork | Jupyter Notebook | Code samples from the book Web Scraping with Python http://shop.oreilly.com/product/063692 | — | — |
| `pytube` | fork | Python | A lightweight, dependency-free Python library (and command-line utility) for downloading Y | — | — |
| `reactjs-webpage` | orig | JavaScript | reactjs-webpage | AWS | — |
| `reactjsWebs` | orig | CSS | Sample website with React Js and bootstrap | AWS | — |
| `salespage` | orig | Groovy | Salespage | — | — |
| `SampleCodeStar` | orig | Java | GitHub repository for AWS CodeStar Java Spring web service | AWS/Azure | — |
| `scc-iac-scanning` | fork | HCL | This shows how to validate your infrastructure as code (IaC) against the organization poli | Google Cloud Run/GKE/BigQuery/Terraform | BigQuery |
| `signal-rgb` | orig | PowerShell | Control SignalRGB from Claude via MCP - version-resolving wrapper, CLI helper, and setup d | — | — |
| `stock-trading-assistance` | orig | Python | argo — Stock Research & Trading Assistant (Phase 1) | Google Cloud Run | SQLite |
| `StockSelector` | orig | Groovy | This project will work on the principle of EMH .[ EFFICIENT MARKET HYPOTHESIS - EMH ] . | Azure | — |
| `SwiftCalc` | orig | C# | IOS calculator for Mtg | — | — |
| `swot` | fork | Kotlin | Identify email addresses or domains names that belong to colleges or universities. Help au | — | — |
| `terraform-docs-samples` | fork | HCL | Terraform samples intended for inclusion in cloud.google.com | Vertex AI/GKE/BigQuery/Terraform | BigQuery |
| `terraform-google-influx` | fork | HCL | Reusable infrastructure modules for running TICK stack on GCP | GKE/Terraform | InfluxDB |
| `terraform-google-workload-identity-federation` | fork | HCL | terraform-google-workload-identity-federation | Google Cloud Run/Terraform | — |
| `Terraforms` | orig·priv | HCL | This is a readme file for terraform project | Google Cloud Run/GKE/AWS/BigQuery | BigQuery |
| `TradingAgents` | fork | Python | TradingAgents: Multi-Agents LLM Financial Trading Framework | Vertex AI/AWS/Azure | SQLite |
| `trustworthyml-ai.github.io` | fork | HTML | Trustworthy Machine Learning Resource Hub | GKE/Azure/GitHub Pages | — |
| `USB-Uncensored-LLM` | fork | HTML | The ultimate zero-install, portable local AI environment. Run high-quality, uncensored LLM | — | — |
| `user-security` | orig | Java | user-security | Firebase | PostgreSQL/Firestore |
| `vault` | orig·priv | - | — | GKE | — |
| `vault-kms` | orig·priv | HCL | — | GKE/Terraform | — |
| `vault-kubernetes` | orig·priv | HCL | \| Name \| Version \| | GKE/Terraform | — |
| `vault-storage` | orig·priv | - | — | — | — |
| `vault-storage-1` | orig·priv | Smarty | <<<<<<< Updated upstream | GKE/AWS/Terraform | Redis |
| `VPC-SC-Demo-Terraform` | fork | HCL | GCP VPC Service Controls | Terraform | — |
| `webretro` | fork | GLSL | RetroArch in your browser | — | — |
| `wizlights-mcp-server` | fork | Python | Model Context Protocol (MCP) server to allow LLMs to controls WiZ devices. | — | — |
| `WLED` | fork | C++ | Control WS2812B and many more types of digital RGB LEDs with an ESP32 over WiFi! | — | — |
| `workforceidentity` | orig | - | — | — | — |
| `XCS224N-A4` | orig | Python | Training the model for the class | — | — |
| `XCS224N-Handouts` | fork | TeX | Contains Lecture Notes and Suggested Readings for XCS224N | — | — |
| `xonora-ios` | fork | Swift | Xonora: Music Assistant Player for iOS, watchOS & CarPlay | — | — |

## Repository details

### `adk-samples`

_fork · public · Python · 134 files · pushed 2026-07-18_

A collection of sample agents built with Agent Development (ADK)

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Vertex AI / Gemini (GCP), Cloudflare Workers — 2 container file(s)
- **Databases:** _none detected_

### `adk-samples2`

_original · public · Python · 116 files · pushed 2026-04-21_

Agent Development Kit (ADK) Samples

- **Core / frameworks:** FastAPI + Uvicorn
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run, GKE / Kubernetes — 2 container file(s)
- **Databases:** _none detected_
- **Security:** Dependabot 5H/3M
- **Per-repo map:** [`adk-samples2/docs/context-map.md`](../../adk-samples2/docs/context-map.md)

### `AdvancedGroovy`

_fork · public · Groovy · 87 files · pushed 2026-06-03_

Examples for my NFJS Advanced Groovy: Tips and Tricks talk

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `agent-identity`

_original · public · Jupyter Notebook · 28 files · pushed 2026-07-21_

Policy Agent — ADK + Agent Identity + Gemini Enterprise

- **Core / frameworks:** FastAPI + Uvicorn, Express / Node, Jupyter notebooks
- **Containers / cloud:** Vertex AI / Gemini (GCP), BigQuery
- **Databases:** BigQuery (analytics)
- **Security:** scan 32H/2M
- **Per-repo map:** [`agent-identity/docs/context-map.md`](../../agent-identity/docs/context-map.md)

### `agent-identity-3`

_original · private · Python · 18 files · pushed 2026-04-22_

ADK agent using Vertex AI Agent Engine Agent Identity to fetch policy docs from GCS; deployable as a Gemini Enterprise add-on agent.

- **Core / frameworks:** FastAPI + Uvicorn, Express / Node
- **Containers / cloud:** Vertex AI / Gemini (GCP)
- **Databases:** _none detected_
- **Per-repo map:** [`agent-identity-3/docs/context-map.md`](../../agent-identity-3/docs/context-map.md)

### `agents-starter`

_fork · public · TypeScript · 20 files · pushed 2026-07-15_

A starter kit for building ai agents on Cloudflare

- **Core / frameworks:** Express / Node, React
- **Containers / cloud:** Cloudflare Workers, Vercel — 1 cloud-deploy manifest(s)
- **Databases:** SQLite

### `ai-agent`

_original · public · Python · 13 files · pushed 2025-10-22_

ai-agent-testing

- **Core / frameworks:** FastAPI + Uvicorn
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run — 1 container file(s)
- **Databases:** SQLite
- **Security:** scan 2L
- **Per-repo map:** [`ai-agent/docs/context-map.md`](../../ai-agent/docs/context-map.md)

### `ai-agent-deploy-ae`

_original · public · Jupyter Notebook · 44 files · pushed 2026-08-04_

A collection of production-ready Generative AI Agent templates built for Google Cloud. It accelerates development by providing a holistic, production-ready solution, addressing common challenges (Deployment & Operations, Evaluation, Customization, Observability) in building and deploying GenAI agents.

- **Core / frameworks:** FastAPI + Uvicorn, Jupyter notebooks
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run, Firebase / Firestore, BigQuery, Terraform
- **Databases:** PostgreSQL / AlloyDB, BigQuery (analytics)
- **Per-repo map:** [`ai-agent-deploy-ae/docs/context-map.md`](../../ai-agent-deploy-ae/docs/context-map.md)

### `Angular-demo-repo`

_original · public · - · 1 files · pushed 2022-05-11_

Angular-demo-repo

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `ansible-for-devops`

_fork · public · Python · 237 files · pushed 2026-06-04_

Ansible for DevOps examples.

- **Core / frameworks:** Flask, Express / Node
- **Containers / cloud:** GKE / Kubernetes, AWS, Ansible, Heroku — 4 container file(s), 11 k8s/helm file(s), 36 IaC file(s)
- **Databases:** MySQL / MariaDB, SQLite, Elasticsearch
- **Security:** scan 2C/6H/2M/1L

### `antigravity-adk-examples`

_original · public · Python · 25 files · pushed 2026-08-05_

ADK examples by hermes Agent for Antigravity cli

- **Core / frameworks:** Express / Node, React
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run
- **Databases:** _none detected_
- **Security:** scan 1H
- **Per-repo map:** [`antigravity-adk-examples/docs/context-map.md`](../../antigravity-adk-examples/docs/context-map.md)

### `antigravity-hidden-features`

_original · public · - · 4 files · pushed 2026-08-03_

YouTube video: 8 Hidden Google Antigravity Features Nobody Talked About — script, thumbnail, gap analysis

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Vertex AI / Gemini (GCP)
- **Databases:** _none detected_
- **Per-repo map:** [`antigravity-hidden-features/docs/context-map.md`](../../antigravity-hidden-features/docs/context-map.md)

### `antigravity-playlist`

_original · public · HTML · 4 files · pushed 2026-08-03_

Curated YouTube playlist of 20 best Google Antigravity & Antigravity CLI videos

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GitHub Pages
- **Databases:** _none detected_
- **Per-repo map:** [`antigravity-playlist/docs/context-map.md`](../../antigravity-playlist/docs/context-map.md)

### `arduino4everyone`

_original · public · Python · 593 files · pushed 2026-04-11_

arduino4everyone

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 1H
- **Per-repo map:** [`arduino4everyone/docs/context-map.md`](../../arduino4everyone/docs/context-map.md)

### `arrstack`

_original · public · HCL · 29 files · pushed 2025-08-27_

Project Documentation

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Azure, Cloudflare Workers, Terraform — 2 container file(s), 3 IaC file(s)
- **Databases:** _none detected_
- **Security:** scan 1C/1H/1M
- **Per-repo map:** [`arrstack/docs/context-map.md`](../../arrstack/docs/context-map.md)

### `asb-gear-ops`

_original · private · Python · 20 files · pushed 2026-08-01_

Private: ASB Gear sourcing RFQs, supplier vetting, and Amazon launch compliance docs

- **Core / frameworks:** Express / Node
- **Containers / cloud:** Ansible
- **Databases:** _none detected_
- **Per-repo map:** [`asb-gear-ops/docs/context-map.md`](../../asb-gear-ops/docs/context-map.md)

### `asb-gear-storefront`

_original · public · HTML · 25 files · pushed 2026-07-25_

ASB Gear — pre-launch storefront for the ASB Solutions Group hardware line (USB-C dock + magnetic car charger mount)

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Cloudflare Workers, Netlify, GitHub Pages
- **Databases:** _none detected_
- **Security:** scan 8M
- **Per-repo map:** [`asb-gear-storefront/docs/context-map.md`](../../asb-gear-storefront/docs/context-map.md)

### `askhr`

_original · public · - · 0 files · pushed 2026-04-06_

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `auto-identity-remove`

_fork · public · JavaScript · 219 files · pushed 2026-07-15_

Automated data broker opt-out runner — removes your personal info from 30+ people-search sites on a monthly schedule

- **Core / frameworks:** Express / Node, Next.js
- **Containers / cloud:** Cloudflare Workers — 3 container file(s)
- **Databases:** _none detected_
- **Security:** scan 29H/8M

### `boilerplates`

_fork · public · Python · 320 files · pushed 2025-05-27_

This is my personal template collection. Here you'll find templates, and configurations for various tools, and technologies.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Cloudflare Workers, Terraform, Ansible — 39 container file(s), 23 k8s/helm file(s), 40 IaC file(s)
- **Databases:** PostgreSQL / AlloyDB, MySQL / MariaDB, InfluxDB
- **Security:** scan 3H

### `casaos-scripts`

_fork · public · Shell · 177 files · pushed 2026-06-04_

These are scripts that are created for the BigBearYouTube Channel

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** SQLite, Vector DB (Chroma/Pinecone/pgvector/FAISS)
- **Security:** scan 9H

### `cheat-sheets`

_fork · public · - · 43 files · pushed 2025-02-12_

This is my personal knowledge-base. Here you'll find code-snippets, technical documentation, and command reference for various tools, and technologies.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Ansible
- **Databases:** _none detected_

### `chef-certification-study-guides`

_fork · public · - · 9 files · pushed 2023-07-07_

So you want to get Chef Certified. Well, I'm here to help.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** AWS, Azure, Terraform
- **Databases:** _none detected_

### `ckg-app-main`

_original · private · Go Template · 1322 files · pushed 2026-02-15_

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Terraform — 40 k8s/helm file(s), 14 cloud-deploy manifest(s), 2 IaC file(s)
- **Databases:** MySQL / MariaDB, Cassandra, Elasticsearch
- **Security:** scan 2C/13H
- **Per-repo map:** [`ckg-app-main/docs/context-map.md`](../../ckg-app-main/docs/context-map.md)

### `claude-new-repo`

_original · public · - · 4 files · pushed 2026-07-16_

claude-new-repo

- **Core / frameworks:** FastAPI + Uvicorn, React
- **Containers / cloud:** Google Cloud Run, Terraform
- **Databases:** _none detected_
- **Per-repo map:** [`claude-new-repo/docs/context-map.md`](../../claude-new-repo/docs/context-map.md)

### `cloud-run-app`

_original · private · Shell · 11 files · pushed 2026-07-16_

cloud-run-app

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Google Cloud Run — 2 container file(s), 1 cloud-deploy manifest(s)
- **Databases:** _none detected_
- **Per-repo map:** [`cloud-run-app/docs/context-map.md`](../../cloud-run-app/docs/context-map.md)

### `ContractWork`

_original · public · Python · 458 files · pushed 2023-07-07_

Class material for python finance 101

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** Redis, SQLite
- **Per-repo map:** [`ContractWork/docs/context-map.md`](../../ContractWork/docs/context-map.md)

### `create-html5-boilerplate`

_fork · public · JavaScript · 27 files · pushed 2026-06-04_

npx quick start for html5-boilerplate

- **Core / frameworks:** Express / Node
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** Dependabot 1C/32H/17M/6L

### `demo-agent-gateway-agent-id`

_original · public · Jupyter Notebook · 28 files · pushed 2026-08-04_

demo-agent-gateway-agent-id

- **Core / frameworks:** Jupyter notebooks
- **Containers / cloud:** Vertex AI / Gemini (GCP), Azure, Terraform — 7 IaC file(s)
- **Databases:** _none detected_
- **Per-repo map:** [`demo-agent-gateway-agent-id/docs/context-map.md`](../../demo-agent-gateway-agent-id/docs/context-map.md)

### `Developing-IoT-Projects-with-ESP32-2nd-edition`

_fork · public · C · 8497 files · pushed 2024-09-27_

Developing IoT Projects with ESP32, 2nd edition - Published by Packt

- **Core / frameworks:** Express / Node
- **Containers / cloud:** AWS, Terraform — 17 container file(s)
- **Databases:** _none detected_
- **Security:** scan 1C/5H/2M

### `Docker-Templates-Unraid`

_fork · public · - · 45 files · pushed 2026-06-03_

Unraid docker templates

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** PostgreSQL / AlloyDB, MySQL / MariaDB

### `EGroovy`

_original · public · Ruby · 3250 files · pushed 2014-07-11_

Features, usage and installation instructions are [summarized on the homepage][home].

- **Core / frameworks:** _none detected_
- **Containers / cloud:** AWS
- **Databases:** PostgreSQL / AlloyDB, MySQL / MariaDB, SQLite, Cassandra, Elasticsearch
- **Security:** scan 8M
- **Per-repo map:** [`EGroovy/docs/context-map.md`](../../EGroovy/docs/context-map.md)

### `esp-idf`

_fork · public · C · 21025 files · pushed 2026-07-16_

Espressif IoT Development Framework. Official development framework for Espressif SoCs.

- **Core / frameworks:** Express / Node
- **Containers / cloud:** _none detected_ — 1 container file(s)
- **Databases:** Redis
- **Security:** scan 60C/51H/13M

### `ESP32-A2DP`

_fork · public · C++ · 438 files · pushed 2026-07-16_

A Simple ESP32 Bluetooth A2DP Library (to implement a Music Receiver or Sender) that supports Arduino, PlatformIO and Espressif IDF

- **Core / frameworks:** Next.js
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 1H/8M

### `esphome`

_fork · public · - · 19 files · pushed 2024-04-22_

ESPHome

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `evilginx2`

_fork · public · Go · 1417 files · pushed 2026-07-15_

Standalone man-in-the-middle attack framework used for phishing login credentials along with session cookies, allowing for the bypass of 2-factor authentication

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Azure, Cloudflare Workers, Firebase / Firestore, BigQuery, Terraform — 3 container file(s), 1 cloud-deploy manifest(s)
- **Databases:** SQLite, Firestore (NoSQL), BigQuery (analytics)
- **Security:** scan 2H

### `fastapi`

_fork · public · Python · 3131 files · pushed 2026-07-16_

FastAPI framework, high performance, easy to learn, fast to code, ready for production

- **Core / frameworks:** FastAPI + Uvicorn, Gunicorn
- **Containers / cloud:** Cloudflare Workers
- **Databases:** PostgreSQL / AlloyDB, Redis, SQLite, Supabase
- **Security:** Dependabot 22H/4M; scan 8H/24M/54L

### `financial-app`

_original · public · Python · 4 files · pushed 2024-10-24_

financial-app

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`financial-app/docs/context-map.md`](../../financial-app/docs/context-map.md)

### `flame`

_fork · public · TypeScript · 328 files · pushed 2026-06-03_

Flame is self-hosted startpage for your server. Easily manage your apps and bookmarks with built-in editors.

- **Core / frameworks:** Express / Node, React
- **Containers / cloud:** GKE / Kubernetes — 5 container file(s), 13 k8s/helm file(s), 2 cloud-deploy manifest(s)
- **Databases:** SQLite
- **Security:** Dependabot 4C/58H/30M/7L

### `frontend`

_fork · public · TypeScript · 3394 files · pushed 2026-07-16_

:lollipop: Frontend for Home Assistant

- **Core / frameworks:** Express / Node
- **Containers / cloud:** Cloudflare Workers, Netlify — 2 container file(s), 1 cloud-deploy manifest(s)
- **Databases:** _none detected_
- **Security:** Dependabot 18H/10M; scan 8H/15M

### `geminiCoder`

_fork · public · TypeScript · 59 files · pushed 2026-06-03_

Create apps with Gemini

- **Core / frameworks:** Express / Node, Next.js
- **Containers / cloud:** Vertex AI / Gemini (GCP), Vercel
- **Databases:** _none detected_

### `geminipoc`

_original · public · HCL · 505 files · pushed 2026-06-28_

db                                88

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run, GKE / Kubernetes, Firebase / Firestore, Terraform — 2 container file(s), 40 k8s/helm file(s), 40 IaC file(s)
- **Databases:** PostgreSQL / AlloyDB, MySQL / MariaDB, Cassandra, Firestore (NoSQL)
- **Security:** scan 3C/5H/6M
- **Per-repo map:** [`geminipoc/docs/context-map.md`](../../geminipoc/docs/context-map.md)

### `General_Handouts`

_fork · public · TeX · 31 files · pushed 2024-03-06_

Course Handouts

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 1H

### `generative-ai`

_fork · public · Jupyter Notebook · 2865 files · pushed 2026-07-16_

Sample code and notebooks for Generative AI on Google Cloud, with Gemini on Vertex AI

- **Core / frameworks:** FastAPI + Uvicorn, Gunicorn, Express / Node, React, Streamlit, Jupyter notebooks
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run, GKE / Kubernetes, Firebase / Firestore, BigQuery, Terraform, Ansible, Heroku — 40 container file(s), 4 cloud-deploy manifest(s), 17 IaC file(s)
- **Databases:** SQLite, BigQuery (analytics)
- **Security:** scan 1C/18H/130M/26L

### `geopm`

_fork · public · C++ · 1591 files · pushed 2026-07-15_

Global Extensible Open Power Manager

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes — 2 container file(s)
- **Databases:** SQLite
- **Security:** scan 15H/2L

### `GLSC`

_original · public · - · 4 files · pushed 2016-03-30_

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`GLSC/docs/context-map.md`](../../GLSC/docs/context-map.md)

### `google-cloud-ai-demos`

_fork · public · TypeScript · 275 files · pushed 2023-11-24_

This repository contains the frontend and backend code for the "AI Demos" demos.

- **Core / frameworks:** FastAPI + Uvicorn, Flask, Django, Gunicorn, Express / Node, React, Jupyter notebooks
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run, BigQuery — 7 container file(s)
- **Databases:** Redis, BigQuery (analytics)
- **Security:** Dependabot 6C/48H/40M/4L; scan 1H

### `gophish`

_fork · public · Go · 486 files · pushed 2025-07-16_

Open-Source Phishing Toolkit

- **Core / frameworks:** Flask, Django, Express / Node, Next.js, React
- **Containers / cloud:** Vertex AI / Gemini (GCP), GKE / Kubernetes, AWS, Azure, Cloudflare Workers, Ansible, Vercel — 1 container file(s)
- **Databases:** MySQL / MariaDB, MongoDB, Redis, SQLite, Cassandra, Vector DB (Chroma/Pinecone/pgvector/FAISS)
- **Security:** scan 2H/2M

### `griffon-eclipse-support-plugin`

_fork · public · Groovy · 9 files · pushed 2026-06-03_

Keeps Eclipse files up to date

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `Groovy`

_original · public · JavaScript · 1086 files · pushed 2014-12-23_

The purpose of this project is to call the google API and return a valid results. I only need top 4 in each category

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 6H
- **Per-repo map:** [`Groovy/docs/context-map.md`](../../Groovy/docs/context-map.md)

### `groovy-core`

_fork · public · Java · 3610 files · pushed 2026-06-03_

Groovy language Git repository

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes
- **Databases:** MySQL / MariaDB
- **Security:** scan 1H

### `hackathon`

_original · public · Python · 121 files · pushed 2026-04-14_

- **Core / frameworks:** FastAPI + Uvicorn
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run, GKE / Kubernetes, Terraform — 4 container file(s), 1 cloud-deploy manifest(s)
- **Databases:** SQLite
- **Security:** Dependabot 5H/3M; scan 2L
- **Per-repo map:** [`hackathon/docs/context-map.md`](../../hackathon/docs/context-map.md)

### `handson-mlp`

_fork · public · Jupyter Notebook · 49 files · pushed 2026-06-03_

A series of Jupyter notebooks that walk you through the fundamentals of Machine Learning and Deep Learning in Python using Scikit-Learn, PyTorch, and Hugging Face libraries.

- **Core / frameworks:** Jupyter notebooks
- **Containers / cloud:** GKE / Kubernetes — 2 container file(s)
- **Databases:** Neo4j, Vector DB (Chroma/Pinecone/pgvector/FAISS)
- **Security:** scan 1H

### `hermes-agent-playlist`

_original · public · HTML · 4 files · pushed 2026-08-03_

test

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GitHub Pages
- **Databases:** _none detected_
- **Per-repo map:** [`hermes-agent-playlist/docs/context-map.md`](../../hermes-agent-playlist/docs/context-map.md)

### `homelab1`

_original · public · HTML · 26 files · pushed 2026-07-28_

homelab-selfhosted-stack

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Cloudflare Workers, Terraform, Vercel, Netlify, Heroku, GitHub Pages — 6 IaC file(s)
- **Databases:** _none detected_
- **Security:** scan 6H/3M
- **Per-repo map:** [`homelab1/docs/context-map.md`](../../homelab1/docs/context-map.md)

### `homelab2`

_fork · public · HCL · 188 files · pushed 2024-11-04_

This is my entire homelab documentation files. Here you'll find notes, setups, and configurations for infrastructure, applications, networking, and more.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Azure, Cloudflare Workers, Terraform, Ansible — 34 container file(s), 24 k8s/helm file(s), 3 cloud-deploy manifest(s), 35 IaC file(s)
- **Databases:** PostgreSQL / AlloyDB, MySQL / MariaDB, InfluxDB
- **Security:** scan 3H

### `homepage`

_fork · public · JavaScript · 1467 files · pushed 2026-07-23_

A highly customizable homepage (or startpage / application dashboard) with Docker and service API integrations.

- **Core / frameworks:** Express / Node, Next.js, React
- **Containers / cloud:** GKE / Kubernetes, AWS, Azure, Cloudflare Workers, GitHub Pages — 6 container file(s)
- **Databases:** InfluxDB
- **Security:** Dependabot 3C/48H/40M/6L; scan 4H/5M/1L

### `html5-boilerplate`

_fork · public · JavaScript · 81 files · pushed 2026-07-15_

A professional front-end template for building fast, robust, and adaptable web apps or sites.

- **Core / frameworks:** Express / Node, Vue
- **Containers / cloud:** _none detected_ — 1 container file(s)
- **Databases:** _none detected_
- **Security:** Dependabot 4H

### `https---github.com-avnit-ContractWork`

_original · public · Jupyter Notebook · 13 files · pushed 2018-04-05_

- **Core / frameworks:** Jupyter notebooks
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`https---github.com-avnit-ContractWork/docs/context-map.md`](../../https---github.com-avnit-ContractWork/docs/context-map.md)

### `infra`

_original · public · HCL · 13 files · pushed 2025-10-29_

Infra repo

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Terraform — 8 IaC file(s)
- **Databases:** _none detected_
- **Per-repo map:** [`infra/docs/context-map.md`](../../infra/docs/context-map.md)

### `integration`

_fork · public · Python · 764 files · pushed 2026-07-15_

HACS gives you a powerful UI to handle downloads of all your custom needs.

- **Core / frameworks:** React, Vue
- **Containers / cloud:** AWS, Azure, Cloudflare Workers — 2 container file(s)
- **Databases:** Redis, Elasticsearch, InfluxDB
- **Security:** scan 1H

### `IPTV-Player-sample`

_fork · public · JavaScript · 273 files · pushed 2023-09-14_

📺 Watch 8000+ publicly available IPTV channels within your browser

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Firebase / Firestore
- **Databases:** Firestore (NoSQL)
- **Security:** scan 1C/1H

### `it-tools`

_fork · public · Vue · 499 files · pushed 2026-06-03_

Collection of handy online tools for developers, with great UX.

- **Core / frameworks:** Express / Node, Vue
- **Containers / cloud:** BigQuery, Vercel, Netlify — 2 container file(s), 2 cloud-deploy manifest(s)
- **Databases:** BigQuery (analytics)
- **Security:** Dependabot 2C/54H/35M/7L; scan 5H/4M

### `jenkins-course`

_fork · public · Shell · 15 files · pushed 2026-06-03_

This is the repository with all the resources for the Jenkins training on Udemy

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_ — 2 container file(s)
- **Databases:** PostgreSQL / AlloyDB

### `JimsGarage`

_fork · public · Shell · 440 files · pushed 2026-07-15_

Homelab Goodies

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Cloudflare Workers, Ansible — 40 container file(s), 40 k8s/helm file(s), 2 cloud-deploy manifest(s), 40 IaC file(s)
- **Databases:** PostgreSQL / AlloyDB, MySQL / MariaDB, MongoDB, Redis, SQLite, InfluxDB
- **Security:** scan 8C/20H/13M/2L

### `Making-Java-Groovy`

_fork · public · Groovy · 924 files · pushed 2023-11-24_

Source code for Manning book "Making Java Groovy"

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** Dependabot 4C/4M; scan 1C/1M

### `Mastering-Embedded-Linux-Development`

_fork · public · C · 126 files · pushed 2026-06-03_

Mastering Embedded Linux Development Fourth Edition, published by Packt

- **Core / frameworks:** FastAPI + Uvicorn, Gunicorn, Express / Node
- **Containers / cloud:** _none detected_ — 1 container file(s)
- **Databases:** _none detected_

### `Mastering-Kali-Linux-for-Advanced-Penetration-Testing-4E`

_fork · public · Python · 35 files · pushed 2023-01-30_

Mastering Kali Linux for Advanced Penetration Testing 4E published by Packt

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 5H

### `Mastering-Ubuntu-Server-Fourth-Edition`

_fork · public · HCL · 29 files · pushed 2022-06-10_

Mastering Ubuntu Server, Fourth Edition, Published by Packt

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, AWS, Terraform — 1 container file(s), 3 IaC file(s)
- **Databases:** _none detected_
- **Security:** scan 2M

### `mediastack`

_fork · public · Shell · 105 files · pushed 2026-08-04_

The ultimate Docker Compose files and configs to build your desired media stack, quickly and easily, with secure outbound network traffic and secure remote access using multifactor authentication.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Cloudflare Workers, Terraform — 40 container file(s)
- **Databases:** PostgreSQL / AlloyDB

### `mojo`

_fork · public · Perl · 407 files · pushed 2026-07-15_

Mojolicious - Perl real-time web framework

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_ — 1 container file(s)
- **Databases:** _none detected_
- **Security:** scan 7C/1M

### `my-chat-agent`

_original · public · TypeScript · 58 files · pushed 2025-09-09_

🤖 Chat Agent Starter Kit

- **Core / frameworks:** Express / Node, React
- **Containers / cloud:** Cloudflare Workers, Terraform, Vercel — 1 cloud-deploy manifest(s), 3 IaC file(s)
- **Databases:** _none detected_
- **Security:** Dependabot 2C/21H/26M/12L
- **Per-repo map:** [`my-chat-agent/docs/context-map.md`](../../my-chat-agent/docs/context-map.md)

### `n8n-pi`

_fork · public · Shell · 30 files · pushed 2026-04-03_

Tools and Images to Build a Raspberry Pi n8n server

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes
- **Databases:** _none detected_

### `new-agent`

_original · private · Python · 37 files · pushed 2026-08-11_

Simple ReAct agent

- **Core / frameworks:** FastAPI + Uvicorn, React
- **Containers / cloud:** Vertex AI / Gemini (GCP), Google Cloud Run, BigQuery, Terraform — 1 container file(s), 11 IaC file(s)
- **Databases:** BigQuery (analytics)
- **Security:** scan 1H/1L
- **Per-repo map:** [`new-agent/docs/context-map.md`](../../new-agent/docs/context-map.md)

### `nodejs`

_original · public · JavaScript · 16 files · pushed 2021-03-10_

- **Core / frameworks:** Express / Node
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** Dependabot 10C/43H/32M/15L
- **Per-repo map:** [`nodejs/docs/context-map.md`](../../nodejs/docs/context-map.md)

### `nvm`

_fork · public · Shell · 334 files · pushed 2023-07-07_

Node Version Manager - Simple bash script to manage multiple active node.js versions

- **Core / frameworks:** Express / Node
- **Containers / cloud:** Ansible — 2 container file(s)
- **Databases:** _none detected_
- **Security:** Dependabot 32M/8L; scan 9H

### `openclaw-trading-agent`

_original · public · - · 3 files · pushed 2026-05-02_

AI trading agent for OpenClaw using Claude Agent SDK — market data, portfolio management, and order execution

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`openclaw-trading-agent/docs/context-map.md`](../../openclaw-trading-agent/docs/context-map.md)

### `openwrt`

_fork · public · C · 11384 files · pushed 2026-07-16_

This repository is a mirror of https://git.openwrt.org/openwrt/openwrt.git It is for reference only and is not active for check-ins.  We will continue to accept Pull Requests here. They will be merged via staging trees then into openwrt.git.

- **Core / frameworks:** Express / Node
- **Containers / cloud:** _none detected_ — 1 container file(s)
- **Databases:** _none detected_
- **Security:** scan 6H/14M

### `opnsense-config`

_original · public · - · 5 files · pushed 2026-03-01_

configuration for opnsense router

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`opnsense-config/docs/context-map.md`](../../opnsense-config/docs/context-map.md)

### `optionPricing`

_original · public · CSS · 665 files · pushed 2016-04-11_

The option price calculator

- **Core / frameworks:** Express / Node
- **Containers / cloud:** Azure, Vercel
- **Databases:** _none detected_
- **Security:** scan 2H/25M
- **Per-repo map:** [`optionPricing/docs/context-map.md`](../../optionPricing/docs/context-map.md)

### `pico-ducky`

_fork · public · Python · 3582 files · pushed 2026-07-15_

Create a USB Rubber Ducky like device using a Raspberry PI Pico

- **Core / frameworks:** FastAPI + Uvicorn, Express / Node, Next.js
- **Containers / cloud:** Vertex AI / Gemini (GCP), GKE / Kubernetes, AWS, Azure, Terraform, Ansible — 38 container file(s), 14 k8s/helm file(s), 2 cloud-deploy manifest(s), 40 IaC file(s)
- **Databases:** PostgreSQL / AlloyDB, MySQL / MariaDB, MongoDB, Redis, Elasticsearch, InfluxDB
- **Security:** scan 42C/101H/34M/10L

### `pihole-ha-dns`

_original · private · Shell · 25 files · pushed 2026-06-05_

Highly-available Pi-hole DNS via VRRP (keepalived) + DNS-over-TLS (Stubby). One Ansible playbook for 3 hosts: Unraid, Orange Pi, Proxmox.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Cloudflare Workers, Ansible — 2 IaC file(s)
- **Databases:** _none detected_
- **Security:** scan 1H
- **Per-repo map:** [`pihole-ha-dns/docs/context-map.md`](../../pihole-ha-dns/docs/context-map.md)

### `pimox7`

_fork · public · Shell · 656 files · pushed 2024-01-08_

Proxmox V7 for Raspberry Pi

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `pop-kustomize`

_fork · public · Python · 35 files · pushed 2024-04-17_

End-to-End Google Cloud CI/CD example repo and tutorial

- **Core / frameworks:** Flask, Gunicorn
- **Containers / cloud:** Google Cloud Run, GKE / Kubernetes — 2 container file(s), 14 k8s/helm file(s), 2 cloud-deploy manifest(s)
- **Databases:** _none detected_
- **Security:** scan 1H/2L

### `PricingConsole`

_original · public · C# · 30 files · pushed 2019-05-10_

PricingConsole

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Azure — 1 cloud-deploy manifest(s)
- **Databases:** _none detected_
- **Security:** Dependabot 2H
- **Per-repo map:** [`PricingConsole/docs/context-map.md`](../../PricingConsole/docs/context-map.md)

### `Project`

_original · public · R · 48 files · pushed 2016-02-20_

SG 40 FINC 621 Trading project

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`Project/docs/context-map.md`](../../Project/docs/context-map.md)

### `project-keyword-spotter`

_fork · public · Python · 23 files · pushed 2022-03-31_

Audio Keyphrase Detector

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `pve-moosefs`

_fork · public · Perl · 18 files · pushed 2026-06-03_

MooseFS Storage Plugin for Proxmox Virtual Environment (PVE)

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `python-4-everyone-hw-2252026`

_original · public · - · 4 files · pushed 2026-02-26_

Python HW and Project

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`python-4-everyone-hw-2252026/docs/context-map.md`](../../python-4-everyone-hw-2252026/docs/context-map.md)

### `python-collections-budget`

_fork · public · Python · 18 files · pushed 2022-06-22_

In this project we’ll process spending data into different types of Python collections. Then we’ll use those collections to graph our spending categories and budget outcomes.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_ — 1 container file(s)
- **Databases:** _none detected_
- **Security:** Dependabot 2H/3M

### `python-flask-ext-api-example`

_fork · public · Python · 13 files · pushed 2023-05-22_

A simple Flask front-end web app accessing the Airthings ext-api using the requests_oauthlib library in Python.

- **Core / frameworks:** Flask
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** Dependabot 1H/4M/1L; scan 1H

### `Python-for-everyone`

_original · public · Jupyter Notebook · 126 files · pushed 2026-03-10_

This is for the class

- **Core / frameworks:** FastAPI + Uvicorn, Jupyter notebooks
- **Containers / cloud:** Terraform
- **Databases:** SQLite
- **Security:** scan 2H
- **Per-repo map:** [`Python-for-everyone/docs/context-map.md`](../../Python-for-everyone/docs/context-map.md)

### `python-scraping`

_fork · public · Jupyter Notebook · 336 files · pushed 2024-06-01_

Code samples from the book Web Scraping with Python http://shop.oreilly.com/product/0636920034391.do

- **Core / frameworks:** Jupyter notebooks
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `pytube`

_fork · public · Python · 89 files · pushed 2024-07-11_

A lightweight, dependency-free Python library (and command-line utility) for downloading YouTube Videos.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 8C/1H

### `reactjs-webpage`

_original · public · JavaScript · 172 files · pushed 2025-07-01_

reactjs-webpage

- **Core / frameworks:** Express / Node, React
- **Containers / cloud:** AWS
- **Databases:** _none detected_
- **Security:** Dependabot 1M
- **Per-repo map:** [`reactjs-webpage/docs/context-map.md`](../../reactjs-webpage/docs/context-map.md)

### `reactjsWebs`

_original · public · CSS · 62 files · pushed 2025-07-01_

Sample website with React Js and bootstrap

- **Core / frameworks:** Express / Node, React
- **Containers / cloud:** AWS
- **Databases:** _none detected_
- **Security:** Dependabot 9C/40H/36M/14L
- **Per-repo map:** [`reactjsWebs/docs/context-map.md`](../../reactjsWebs/docs/context-map.md)

### `salespage`

_original · public · Groovy · 21 files · pushed 2024-08-14_

Salespage

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`salespage/docs/context-map.md`](../../salespage/docs/context-map.md)

### `SampleCodeStar`

_original · public · Java · 12 files · pushed 2019-05-10_

GitHub repository for AWS CodeStar Java Spring web service

- **Core / frameworks:** _none detected_
- **Containers / cloud:** AWS, Azure — 2 cloud-deploy manifest(s)
- **Databases:** _none detected_
- **Security:** Dependabot 2H
- **Per-repo map:** [`SampleCodeStar/docs/context-map.md`](../../SampleCodeStar/docs/context-map.md)

### `scc-iac-scanning`

_fork · public · HCL · 29 files · pushed 2026-06-03_

This shows how to validate your infrastructure as code (IaC) against the organization policies and Security Health Analytics detectors that you have defined in your Google Cloud organization.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Google Cloud Run, GKE / Kubernetes, BigQuery, Terraform — 1 cloud-deploy manifest(s), 19 IaC file(s)
- **Databases:** BigQuery (analytics)
- **Security:** scan 4H/1M

### `signal-rgb`

_original · public · PowerShell · 3 files · pushed 2026-07-20_

Control SignalRGB from Claude via MCP - version-resolving wrapper, CLI helper, and setup docs

- **Core / frameworks:** React
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`signal-rgb/docs/context-map.md`](../../signal-rgb/docs/context-map.md)

### `stock-trading-assistance`

_original · public · Python · 56 files · pushed 2026-07-16_

argo — Stock Research & Trading Assistant (Phase 1)

- **Core / frameworks:** FastAPI + Uvicorn, Express / Node, React
- **Containers / cloud:** Google Cloud Run — 2 container file(s), 1 cloud-deploy manifest(s)
- **Databases:** SQLite
- **Security:** Dependabot 1H/1M; scan 1H/1L
- **Per-repo map:** [`stock-trading-assistance/docs/context-map.md`](../../stock-trading-assistance/docs/context-map.md)

### `StockSelector`

_original · public · Groovy · 68 files · pushed 2019-04-25_

This project will work on the principle of EMH .[ EFFICIENT MARKET HYPOTHESIS - EMH ] .

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Azure — 1 cloud-deploy manifest(s)
- **Databases:** _none detected_
- **Per-repo map:** [`StockSelector/docs/context-map.md`](../../StockSelector/docs/context-map.md)

### `SwiftCalc`

_original · public · C# · 117 files · pushed 2016-03-23_

IOS calculator for Mtg

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Per-repo map:** [`SwiftCalc/docs/context-map.md`](../../SwiftCalc/docs/context-map.md)

### `swot`

_fork · public · Kotlin · 26853 files · pushed 2026-07-16_

Identify email addresses or domains names that belong to colleges or universities. Help automate the process of approving or rejecting academic discounts.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `terraform-docs-samples`

_fork · public · HCL · 656 files · pushed 2026-07-15_

Terraform samples intended for inclusion in cloud.google.com

- **Core / frameworks:** Express / Node
- **Containers / cloud:** Vertex AI / Gemini (GCP), GKE / Kubernetes, BigQuery, Terraform — 40 IaC file(s)
- **Databases:** BigQuery (analytics)
- **Security:** scan 1C/16H/14M

### `terraform-google-influx`

_fork · public · HCL · 98 files · pushed 2026-06-03_

Reusable infrastructure modules for running TICK stack on GCP

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Terraform — 24 IaC file(s)
- **Databases:** InfluxDB
- **Security:** Dependabot 7C/13H/22M/4L; scan 1H/4M/2L

### `terraform-google-workload-identity-federation`

_fork · public · HCL · 34 files · pushed 2023-07-07_

terraform-google-workload-identity-federation

- **Core / frameworks:** Express / Node
- **Containers / cloud:** Google Cloud Run, Terraform — 1 container file(s), 11 IaC file(s)
- **Databases:** _none detected_

### `Terraforms`

_original · private · HCL · 91 files · pushed 2024-08-14_

This is a readme file for terraform project

- **Core / frameworks:** Express / Node
- **Containers / cloud:** Google Cloud Run, GKE / Kubernetes, AWS, BigQuery, Terraform — 40 IaC file(s)
- **Databases:** BigQuery (analytics)
- **Security:** scan 2M
- **Per-repo map:** [`Terraforms/docs/context-map.md`](../../Terraforms/docs/context-map.md)

### `TradingAgents`

_fork · public · Python · 160 files · pushed 2026-08-10_

TradingAgents: Multi-Agents LLM Financial Trading Framework

- **Core / frameworks:** Express / Node
- **Containers / cloud:** Vertex AI / Gemini (GCP), AWS, Azure — 3 container file(s)
- **Databases:** SQLite
- **Security:** scan 1H

### `trustworthyml-ai.github.io`

_fork · public · HTML · 131 files · pushed 2025-07-03_

Trustworthy Machine Learning Resource Hub

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Azure, GitHub Pages
- **Databases:** _none detected_
- **Security:** scan 2H

### `USB-Uncensored-LLM`

_fork · public · HTML · 26 files · pushed 2026-07-15_

The ultimate zero-install, portable local AI environment. Run high-quality, uncensored LLMs (Gemma, Qwen, NemoMix) directly from any USB drive or SSD. Fully air-gapped, cross-platform (Win/Mac/Linux), and privacy-first with persistent chat history.

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 9M

### `user-security`

_original · public · Java · 260 files · pushed 2021-03-29_

user-security

- **Core / frameworks:** Express / Node, Spring Boot
- **Containers / cloud:** Firebase / Firestore — 3 container file(s)
- **Databases:** PostgreSQL / AlloyDB, Firestore (NoSQL)
- **Security:** Dependabot 7C/29H/24M/15L; scan 1M
- **Per-repo map:** [`user-security/docs/context-map.md`](../../user-security/docs/context-map.md)

### `vault`

_original · private · - · 6 files · pushed 2021-12-08_

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes
- **Databases:** _none detected_
- **Per-repo map:** [`vault/docs/context-map.md`](../../vault/docs/context-map.md)

### `vault-kms`

_original · private · HCL · 7 files · pushed 2021-12-08_

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Terraform — 6 IaC file(s)
- **Databases:** _none detected_
- **Per-repo map:** [`vault-kms/docs/context-map.md`](../../vault-kms/docs/context-map.md)

### `vault-kubernetes`

_original · private · HCL · 13 files · pushed 2021-12-08_

| Name | Version |

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, Terraform — 9 IaC file(s)
- **Databases:** _none detected_
- **Per-repo map:** [`vault-kubernetes/docs/context-map.md`](../../vault-kubernetes/docs/context-map.md)

### `vault-storage`

_original · private · - · 0 files · pushed 2021-12-08_

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `vault-storage-1`

_original · private · Smarty · 31 files · pushed 2022-09-25_

<<<<<<< Updated upstream

- **Core / frameworks:** _none detected_
- **Containers / cloud:** GKE / Kubernetes, AWS, Terraform — 3 k8s/helm file(s), 6 IaC file(s)
- **Databases:** Redis
- **Security:** scan 1H
- **Per-repo map:** [`vault-storage-1/docs/context-map.md`](../../vault-storage-1/docs/context-map.md)

### `VPC-SC-Demo-Terraform`

_fork · public · HCL · 59 files · pushed 2024-10-16_

GCP VPC Service Controls

- **Core / frameworks:** _none detected_
- **Containers / cloud:** Terraform — 40 IaC file(s)
- **Databases:** _none detected_
- **Security:** scan 15M

### `webretro`

_fork · public · GLSL · 399 files · pushed 2023-03-31_

RetroArch in your browser

- **Core / frameworks:** Express / Node
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 1C/1H/7M

### `wizlights-mcp-server`

_fork · public · Python · 21 files · pushed 2026-07-15_

Model Context Protocol (MCP) server to allow LLMs to controls WiZ devices.

- **Core / frameworks:** FastAPI + Uvicorn
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `WLED`

_fork · public · C++ · 580 files · pushed 2026-07-15_

Control WS2812B and many more types of digital RGB LEDs with an ESP32 over WiFi!

- **Core / frameworks:** FastAPI + Uvicorn, Express / Node, Next.js, React
- **Containers / cloud:** _none detected_ — 3 container file(s)
- **Databases:** _none detected_
- **Security:** scan 21M

### `workforceidentity`

_original · public · - · 1 files · pushed 2026-03-02_

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `XCS224N-A4`

_original · public · Python · 7 files · pushed 2025-11-23_

Training the model for the class

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_
- **Security:** scan 1H
- **Per-repo map:** [`XCS224N-A4/docs/context-map.md`](../../XCS224N-A4/docs/context-map.md)

### `XCS224N-Handouts`

_fork · public · TeX · 55 files · pushed 2026-06-03_

Contains Lecture Notes and Suggested Readings for XCS224N

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

### `xonora-ios`

_fork · public · Swift · 205 files · pushed 2026-02-22_

Xonora: Music Assistant Player for iOS, watchOS & CarPlay

- **Core / frameworks:** _none detected_
- **Containers / cloud:** _none detected_
- **Databases:** _none detected_

---
_Generated by repo context-mapping pass on 2026-08-13. Per-repo detail maps live at `<repo>/docs/context-map.md` for original repos._
