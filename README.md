# 🤖 AIoT-LLM-RAG-SmartHome-Engine

An enterprise-grade **GenAI & Hybrid Search RAG Architecture** integrated with **Agentic Workflows** for next-generation smart appliance interaction and diagnostic systems.

---

## 🌟 Architecture Overview

This architecture bridges standard IoT protocols with Generative AI models (e.g., DeepSeek-V3/R1), solving traditional home automation pain points such as rigid intent recognition and complex diagnostic flows.

```mermaid
graph TD
    User([User Voice / Text Input]) --> Gateway[API Gateway / Intent Router]
    
    subgraph AI Agent & RAG Pipeline
        Gateway --> Router{Intent Classification}
        Router -->|Device Control| Agent[Agentic Function Calling Engine]
        Router -->|Diagnostic / Q&A| RAG[Hybrid Search RAG System]
        
        RAG --> Dense[Dense Retrieval: Vector DB]
        RAG --> Sparse[Sparse Retrieval: BM25 Keyword]
        Dense --> Reranker[Rerank Model: Cross-Encoder]
        Sparse --> Reranker
        Reranker --> LLM[DeepSeek-V3/R1 LLM]
    end

    subgraph AIoT Execution Layer
        Agent -->|Structured JSON| ThingModel[Thing Model Mapper]
        ThingModel --> MQTT[MQTT / Cloud Service]
        MQTT --> Device[Smart Home Appliances]
    end

    LLM --> Response([Streaming Response / Action Render])
