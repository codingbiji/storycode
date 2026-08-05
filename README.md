
# StoryCode — Your Local-First AI Coding Agent

**StoryCode** is a desktop AI coding agent that helps you build, refactor, and manage code right on your own machine. Powered by a Rust core with a modern desktop interface, it brings the power of an AI programming assistant to your local environment — fast, private, and fully under your control.

### Why StoryCode?

- **Local-first & private** — Your code, prompts, and data stay on your machine. No mandatory cloud uploads, no vendor lock-in.
- **Works with your favorite models** — One interface, many providers: Claude, OpenAI, Azure, Gemini, Ollama, LLaMA Server and more. Use cloud models when you want, or run everything fully offline with local inference.
- **Safe by design** — Code runs in a sandboxed environment (seccomp-bpf / landlock on Linux, job objects on Windows), so experiments can't damage your system.
- **Extensible with MCP** — Plug in powerful tools for files, shells, code analysis, document processing (PDF/DOCX/XLSX), knowledge bases, and UI automation — and add your own extensions easily.
- **Built-in voice** — Local speech-to-text (Whisper / Qwen3) and text-to-speech (Kokoro / Qwen3) let you talk to your agent and hear it respond, all offline.
- **Memory & knowledge** — Persistent conversation memory and a built-in knowledge base (RAG) mean your agent remembers context and answers from your own documents.
- **Reusable workflows** — Define complex agent behaviors as simple YAML/JSON workflows with parameters, then reuse them across tasks.
- **Multimedia toolkits** — Audio, video, vision, and database tools round out a full toolbox for real-world tasks.


---


# StoryCode —— 你的本地优先 AI 编码 Agent

**StoryCode** 是一款桌面端 AI 编码 Agent，帮助你在自己的电脑上高效地编写、重构和管理代码。它采用 Rust 高性能内核，配合现代化的桌面界面，把 AI 编程助手的强大能力带到本地环境——更快、更私密、完全由你掌控。

### 为什么选择 StoryCode？

- **本地优先、保护隐私** — 你的代码、提示词和数据都留在本机，没有强制云端上传，不绑定任何厂商。
- **兼容主流大模型** — 一套界面，多家提供商：Claude、OpenAI、Azure、Gemini、Ollama、LLaMA Server 等。想用云端模型就用云端，想完全离线就用本地推理。
- **安全沙箱设计** — 代码在沙箱环境中执行（Linux 使用 seccomp-bpf / landlock，Windows 使用 job objects），实验性操作不会破坏你的系统。
- **MCP 生态可扩展** — 内置文件、Shell、代码分析、文档处理（PDF / DOCX / XLSX）、知识库、UI 自动化等强大工具，还可以轻松接入自己的扩展。
- **内置语音能力** — 本地语音转文字（Whisper / Qwen3）与文字转语音（Kokoro / Qwen3），可以和代理对话、听它回复，全程离线可用。
- **记忆与知识库** — 持久的会话记忆和内置知识库（RAG），让代理记住上下文，并能基于你自己的文档回答问题。
- **可复用的工作流** — 用简单的 YAML/JSON 定义带参数的复杂代理行为，一次配置，反复使用。
- **多媒体工具箱** — 音频、视频、视觉与数据库工具一应俱全，覆盖真实世界的各类任务。
