# Corentin Seu
**Data & AI Engineer | Aspiring Solutions Architect** 
[LinkedIn](https://www.linkedin.com/in/corentin-seu-28840029b/)
📍 Sophia Antipolis | English: C1 (TOEIC: 915/990) | French: Native

I am a driven Data Engineering student and developer with a strong focus on building resilient infrastructures and Generative AI systems. Currently transitioning from hands-on development to system architecture, I specialize in turning complex operational challenges into scalable, automated solutions.
### Focus Areas:
* **Generative AI & LLMOps:** Designing RAG pipelines, autonomous agents, and multimodal AI systems (Gemini, OpenAI).
* **Data Engineering & iPaaS:** Expert in enterprise orchestration, ETL/EDI workflows, and platform migrations (Workato, SnapLogic, n8n).
* **Scalable SaaS Infrastructure:** Building multi-tenant architectures with hybrid data models (PostgreSQL JSONB, Docker).
* **Enterprise System Integration**: Orchestrating complex EDI flows and API connectivity between legacy ERPs and modern SaaS to ensure data consistency.
---

## 🚀 Projects

*All case studies represent real-world professional implementations and personal R&D. Specific business details have been generalized to protect confidentiality.*
### 🏛 Generative AI-powered SaaS for Field Operations

**Industry:** Field Services, Construction & Real Estate (SaaS)

**Problem**
Field professionals across various verticals (construction, facility maintenance, real estate audits) spend 30-40% of their working time on administrative tasks. Each trade requires specific report formats and data points, making standard "one-size-fits-all" software rigid and inefficient. Critical data is often fragmented, and existing solutions lack the flexibility to adapt to the specific workflows of different field trades without costly custom development.

**Solution**
The solution implements a **modular, multi-tenant SaaS platform** designed to be industry-agnostic. It combines **Generative AI** with a **Hybrid Data Architecture**, allowing the system to adapt its data collection and reporting logic dynamically based on the client's trade.

**Modular & Agnostic Data Modeling:** Unlike traditional rigid schemas, the database architecture leverages **PostgreSQL `JSONB` columns** to store dynamic configurations and trade-specific metadata.

* **Dynamic Configuration:** Report templates, checklists, and workflows are defined in JSON structures linked to the user's organization.
* **Scalability:** This hybrid approach allows the platform to onboard an Architect (needs: "Snagging list"), a Plumber (needs: "Intervention voucher"), or a Real Estate Agent (needs: "Inventory check") using the same backend code, simply by injecting a different JSON configuration.

**Conversational Ingestion (UX):** The frontend utilizes the Telegram Bot API to provide a low-latency interface. The bot's menu and questions adapt in real-time based on the JSON configuration of the user's profile, ensuring a personalized experience for every trade.

**Multi-modal AI Pipeline (RAG):**

* **Contextual Intelligence:** The RAG pipeline retrieves both the structured project data and the unstructured field inputs (Voice/Photos).
* **AI Processing:** **OpenAI Whisper** handles transcription while **Google Gemini Pro** analyzes visual evidence. The AI output is constrained by the specific requirements defined in the client's JSON configuration to ensure compliance.

**Infrastructure:** The solution is orchestrated by **n8n** workflows running in **Docker** containers, with **Cloudflare Tunnel** for secure exposure and **Gotenberg** for dynamic PDF generation based on the custom data models.

**My responsibilities included:**

* Architected a **Hybrid Relational/Document database** (PostgreSQL) using `JSONB` to enable strictly typed core data (Users, Auth) mixed with flexible, schema-less trade configurations.
* Designed the **end-to-end SaaS infrastructure** using containerized micro-services (Docker) to ensure scalability.
* Implemented the **RAG pipeline** integrating LLMs (Gemini) and STT (Whisper) to process multimodal inputs.
* Engineered a **dynamic conversational UX** where bot interactions are rendered programmatically based on the stored JSON configuration.
* Automated the **CI/CD pipeline** and monitoring strategy to ensure high availability.
<img src="https://raw.githubusercontent.com/corentinseu/Portfolio_Corentin/blob/main/images/CS_Labs_Schema.png" alt="CS_Labs_Schema" width="100%" />
**Technology stack:** Docker, PostgreSQL (JSONB), n8n, Google Gemini Pro, OpenAI Whisper, Telegram API, Gotenberg, Cloudflare Tunnel, Node.js.

---

### 📦 B2B EDI Automation & Complex Data Transformation

**Context:** Supply chain optimization for a European leader in tire distribution (MPSA).

**The Challenge**
Establishing a robust, automated data bridge with a Tier-1 digital partner (e.g., Allopneus). While both entities exchanged standard file formats (CSV, XML), the **data structures and schemas were incompatible**. The challenge was to automate the translation of internal data extracts into the partner's strict EDI specifications without altering internal legacy processes.

**The Solution**
I designed a **Decoupled Architecture** using **Workato** as a transformation middleware between an **Internal Repository (SFTP)** and an **External Exchange Zone**.

* **Asynchronous "Double SFTP" Architecture:** To ensure security and decoupling, internal systems drop files on a secure internal SFTP. Workato detects these events, processes the data, and pushes the result to the partner's shared SFTP (and vice-versa).
* **Complex CSV Re-Mapping (Stock Flow):** The system ingests raw internal SQL extracts (CSV). Workato applies a rigid **column mapping strategy** (renaming headers, reformatting dates, calculating availability) to generate a partner-compliant CSV file.
* **Deep XML Node Translation (Order Cycle):** For the Order-to-Cash loop (Orders, Responses, Tracking), implemented a **node-by-node translation logic**. The middleware parses the partner's specific XML tags and reconstructs the file into the internal XML standard (e.g., mapping `<Customer_Reference>` to `<Internal_Client_ID>`) ensuring semantic consistency.

<img src="https://raw.githubusercontent.com/corentinseu/Portfolio_Corentin/blob/main/images/EDI_AP_MPSA.png" alt="EDI_Architecture_Schema" width="100%" />

**Technology stack:** Workato (iPaaS), SFTP (SSH File Transfer Protocol), XML/CSV Transformation, EDI Logic.

---

### 🔄 Strategic iPaaS Migration: SnapLogic to Workato

**Context:** Digital transformation of the integration layer for a major automotive distributor.

**Challenge:** Transitioning critical business logic and real-time data flows from a legacy iPaaS (SnapLogic) to a modern, scalable environment (Workato) with **zero downtime**.

**Key Achievements:**

* **Architectural Mapping:** Analyzed and re-engineered complex SnapLogic "Snaps" into optimized Workato "Recipes," improving workflow readability and maintainability.
* **Infrastructure Connectivity:** Configured and secured hybrid cloud/on-premise connectors to ensure seamless data continuity between legacy ERPs and modern SaaS tools.
* **Data Integrity:** Led the testing and validation phase to ensure that 100% of data mappings remained consistent during the transition.
* **Skill Shift:** Acted as a technical bridge during the migration, mastering both platforms to ensure a smooth architectural handover.

**Technology stack:** SnapLogic, Workato, REST APIs, JSON, SQL.

