# StoryCode

> **StoryCode = 本地优先 + 可扩展 MCP 工具生态 + 项目记忆（Story）+ 本地 RAG 知识库 + IM 聊天机器人，一个掌控在自己手中的 AI 智能体平台。**


> **StoryCode = a local-first + an extensible MCP tool ecosystem + project memory (Story) + local RAG knowledge base + IM chatbot, an AI agent platform you fully control.**


**[← English](#storycode-introduction)**

---

## StoryCode 介绍

StoryCode 是一个本地优先（Local-first）的桌面端 AI 智能体平台。它以 Rust 代理内核 + Tauri 桌面应用为主体，集编码助手、办公自动化、多媒体处理、知识库、IM 机器人于一体，构成一个可扩展的 Agent 系统。

所有数据默认留在本地，模型可选云端或本地，既能获得大模型能力，又保持对代码、文件、隐私的完全掌控。

---

### 核心能力

#### 1. 智能体运行时（Agent Runtime）

- 完整的代理编排层：tool loop、上下文管理、会话生命周期。
- 子代理（Subagents）：任务可分解到独立子代理执行，主会话保持精简。
- 技能系统（Skills）：可动态加载的能力包，快速扩展 Agent 本领。
- 工作流引擎：YAML/JSON 定义可复用流程，支持参数化、嵌套子工作流、模型覆盖，配合 `{{parameter}}` 模板语法。
- 定时调度器：Cron 表达式调度工作流，支持暂停 / 恢复 / 执行历史。

#### 2. 模型接入：云端 + 本地全覆盖

- **模型供应商**：OpenAI、Anthropic、DeepSeek、xAI（Grok）、Mistral、Groq、智谱 AI（GLM）、阿里云百炼（Qwen）、Kimi、MiniMax、火山引擎方舟、小米 MiMo、美团 LongCat。
- **云平台 / 聚合网关**：Azure、Google Gemini、LiteLLM、OpenRouter、AWS Bedrock、GCP Vertex AI、SageMaker TGI。
- **Agent / CLI 与 Copilot**：Codex、Claude Code、Cursor Agent、Gemini CLI、GitHub Copilot。
- **数据 / 行业平台**：Databricks、Snowflake。
- **其他平台**：Venice、Tetrate、Inception。
- **本地推理**：内置 llama.cpp 本地推理引擎（llama-server）。
- **自定义 Provider**：可自建 OpenAI / Anthropic / Ollama 兼容的私有模型接入。

#### 3. MCP 扩展生态

基于 Model Context Protocol 的可插拔工具系统，内置扩展包括：

- **Developer**：文件系统、Shell、文本编辑、tree-sitter 代码结构分析。
- **Computer Use**：UI 自动化、网页抓取、PDF/DOCX/XLSX 文档处理。
- **Web Search**：联网搜索（Tavily / Brave / Bocha / DuckDuckGo），返回带引用来源的结果。
- **Memory**：跨会话持久化记忆（分类 + 标签）。
- **Knowledge**：RAG 知识库（内置 embedding 模型随包分发）。
- **Visualizer**：Mermaid、Sankey、雷达图、地图等交互式可视化。
- **Tutorial**：引导式教程。
- **DevTools**：数据库（SQLite / PostgreSQL / MySQL）、SSH。
- **多媒体**：音频 / 视频 / 截图 / AI 生成。


#### 4. Story：项目故事与决策记忆

Story 是 StoryCode 中承载“可长期沉淀的项目记忆”的载体。Agent 不再每次从零开始，而是能读取项目历史、理解“为什么这样写”。

- **三种内容类型**：
  - 笔记（Note）：自由 Markdown 记录、灵感、需求分析。
  - 检查点（Checkpoint）：自动记录代码变更背后的故事（Commit SHA、变更文件数、增删行数、状态）。
  - 会话摘要（Session Summary）：把一次高质量会话归档成可复用的知识片段。
- **三种来源**：手动创建、Agent 自动沉淀、会话归档。
- **版本历史**：每次保存自动生成新版本，随时回溯与恢复。
- **全文检索（FTS5）**：按标题、正文、关键词、标签快速定位 Story。
- **双向关联**：关联会话 / 轮次 / 文件 / Git Commit；Story 之间也可以互相链接，实现需求 ↔ 代码 ↔ 决策的可追溯。
- **星标收藏**：重要 Story 一键置顶。
- **自动召回（Auto Recall）**：新建会话时自动加载相关 Story 作为上下文，减少重复解释。

核心理念：不要让用户刻意记录，而是让 Agent 工作过程中的关键决策自然沉淀为可追溯的项目故事。

#### 5. 知识库（Knowledge）：本地 RAG 知识底座

知识库是 StoryCode 的“可增长的知识层”。它不仅被动索引，更能在 Agent 工作过程中主动更新。

- **多知识库管理**：可创建多个知识库，索引本地文档目录；托管知识库（Managed KB）可直接由 Agent 写入。
- **混合检索**：全文检索 + 向量语义检索（RAG），内置 embedding 模型随安装包分发，开箱即用、无需联网下载。
- **内置 OCR**：图片、PDF 扫描件文字识别入库，内置 OCR 模型随包分发。
- **多格式摄取**：支持 Markdown、PDF、DOCX、XLSX、PPTX、ODT/ODP、图片、HTML 页面及常见代码文件等文本提取与增量索引。
- **Agent 深度集成**：
  - 搜索 / 读取知识库工具。
  - 回答后可一键归档为 Story 或写入知识库。
  - 支持手动触发摘要、建关联、更新 wiki，所有写入均受控、可审阅、可回滚。

闭环流程：导入资料 → 生成摘要/笔记 → 回答后归档 → 重新索引 → 下次复用。

#### 6. DevTools 套件

- **数据库工具**：SQLite / PostgreSQL / MySQL 查询、行编辑、CSV 导出（含公式注入防护）。
- **Git / SSH / 终端**：远程主机管理、SFTP 文件传输、内置终端。
- **Vault**：凭据安全保管。

#### 7. 多媒体能力

- **AI 生成**：文生图、图生图、图生视频（本地推理或阿里云百炼）。
- **录制**：屏幕录制、窗口 / 全屏截图、麦克风与系统音频采集（Windows 采用进程内 WASAPI loopback）。
- **本地语音**：
  - ASR：Whisper / Qwen3 语音转文字（含说话人分离 sherpa-onnx）。
  - TTS：Kokoro / Qwen3 / MOSS 语音合成。

#### 8. IM 通道：把 Agent 变成聊天机器人

StoryCode 通过统一的 `channel-common` 基础设施，把桌面 Agent 延伸为可在 IM 中使用的聊天机器人。

- 已支持：QQ、微信、企业微信、钉钉、飞书、Telegram、Discord、WhatsApp、Linq。
- 群聊 / 私聊中直接调用 Agent 的全部工具能力。
- 消息收发、会话映射、权限控制统一封装，接入新通道成本低。

---

**[← 中文](#storycode-介绍)**

## StoryCode Introduction

StoryCode is a **local-first desktop AI agent platform**. Built around a Rust agent core and a Tauri desktop app, it brings together coding assistance, office automation, multimedia processing, knowledge bases, and IM bots into a single extensible agent system.

By default, all your data stays local. Models can be cloud-based or local, so you get the power of large language models while retaining full control over your code, files, and privacy.

---

### Core Capabilities

#### 1. Agent Runtime

- A complete agent orchestration layer: tool loop, context management, and session lifecycle.
- **Subagents**: Decompose tasks into independent subagents so the main session stays lean.
- **Skills**: Dynamically loadable capability packs.
- **Workflow Engine**: Reusable YAML/JSON workflows with parameters, nested sub-workflows, model overrides, and `{{parameter}}` template syntax.
- **Scheduler**: Cron-based workflow scheduling with pause/resume and execution history.

#### 2. Model Access: Cloud + Local

- **Model providers**: OpenAI, Anthropic, DeepSeek, xAI (Grok), Mistral, Groq, Zhipu AI (GLM), Aliyun Bailian (Qwen), Kimi, MiniMax, Volcengine Ark, Xiaomi MiMo, Meituan LongCat.
- **Cloud platforms / gateways**: Azure, Google Gemini, LiteLLM, OpenRouter, AWS Bedrock, GCP Vertex AI, SageMaker TGI.
- **Agent / CLI and Copilot**: Codex, Claude Code, Cursor Agent, Gemini CLI, GitHub Copilot.
- **Data / industry platforms**: Databricks, Snowflake.
- **Other platforms**: Venice, Tetrate, Inception.
- **Local inference**: Built-in llama.cpp inference engine (llama-server).
- **Custom providers**: Bring your own OpenAI / Anthropic / Ollama-compatible private models.

#### 3. MCP Extension Ecosystem

A pluggable tool system built on the Model Context Protocol. Built-in extensions include:

- **Developer**: File system, shell, text editing, and tree-sitter code structure analysis.
- **Computer Use**: UI automation, web scraping, PDF/DOCX/XLSX document processing.
- **Web Search**: Web search (Tavily / Brave / Bocha / DuckDuckGo) with cited results.
- **Memory**: Cross-session persistent memory with categories and tags.
- **Knowledge**: RAG knowledge base with bundled embedding models.
- **Visualizer**: Interactive visualizations including Mermaid, Sankey, radar charts, and maps.
- **Tutorial**: Guided tutorials.
- **DevTools**: Database (SQLite / PostgreSQL / MySQL) and SSH (see section 6).
- **Multimedia**: Audio / video / screenshots / AI generation (see section 7).


#### 4. Story: Project Stories and Decision Memory

Story is how StoryCode captures long-lived project memory. Agents no longer start from scratch every session—they can read project history and understand *why* things were done.

- **Three content types**:
  - **Note**: Free-form Markdown for ideas, requirements, and analysis.
  - **Checkpoint**: Automatically records the story behind code changes (commit SHA, changed files, insertions/deletions, status).
  - **Session Summary**: Archives a high-quality chat session into a reusable knowledge snippet.
- **Three sources**: Manual creation, agent-generated, and archived from sessions.
- **Version history**: Every save creates a new version, so you can roll back anytime.
- **Full-text search (FTS5)**: Search by title, body, keywords, or tags.
- **Bidirectional relations**: Link sessions / turns / files / Git commits; Stories can also link to each other, making requirements ↔ code ↔ decisions traceable.
- **Starred**: Pin important Stories for quick access.
- **Auto recall**: New sessions automatically load relevant Stories as context, reducing repeated explanations.

Core idea: Instead of asking users to manually document everything, let the agent naturally turn key decisions into traceable project stories.

#### 5. Knowledge: Local RAG Knowledge Base

The knowledge base is StoryCode’s *growing knowledge layer*. It is not just a passive index; it actively update.

- **Multi-KB management**: Create multiple knowledge bases and index local document directories. Managed KBs can be written to directly by agents.
- **Hybrid retrieval**: Full-text + vector semantic search (RAG), with bundled embedding models included in the installer—works out of the box without downloading from the cloud.
- **Built-in OCR**: Extract text from images and scanned PDFs, using bundled OCR models.
- **Multi-format ingestion**: Extract and incrementally index Markdown, PDF, DOCX, XLSX, PPTX, ODT/ODP, images, HTML pages, and common source-code files.
- **Deep agent integration**:
  - Tools to search / read the knowledge base.
  - One-click archiving of answers into a Story or into the KB.
  - Manual triggers for summarization, linking, and wiki updates. All writes are controlled, reviewable, and rollback-friendly.

Closed loop: Import → Summarize/Note → Archive → Re-index → Reuse.

#### 6. DevTools Suite

- **Database tools**: SQLite / PostgreSQL / MySQL query, row editing, CSV export (with formula-injection protection).
- **Git / SSH / Terminal**: Remote host management, SFTP file transfer, built-in terminal.
- **Vault**: Secure credential storage.

#### 7. Multimedia Capabilities

- **AI generation**: Text-to-image, image-to-image, and image-to-video (local inference or Alibaba Cloud Bailian).
- **Recording**: Screen recording, window/full-screen capture, microphone and system audio capture (Windows uses in-process WASAPI loopback).
- **Local voice**:
  - **ASR**: Whisper / Qwen3 speech-to-text, with speaker diarization via sherpa-onnx.
  - **TTS**: Kokoro / Qwen3 / MOSS text-to-speech.

#### 8. IM Channels: Turn the Agent into a Chatbot

StoryCode uses the unified `channel-common` infrastructure to extend the desktop agent into IM chatbots.

- **Supported channels**: QQ, WeChat (Weixin), WeCom, DingTalk, Feishu, Telegram, Discord, WhatsApp, Linq.
- Use all agent tool capabilities directly in group chats and private messages.
- Unified message handling, session mapping, and permission control make adding new channels straightforward.

---



