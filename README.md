# 👋 Hi, I'm **SSEREMBA CYPRIAN DAVIS**  
### 🇺🇬 Software Developer | Java Developer | Spring Boot | Microservices | Cloud | AI | React

<p align="left">
  <img src="https://img.shields.io/badge/Java-Expert-orange?logo=java&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_Boot-Professional-6DB33F?logo=springboot&logoColor=white" />
  <img src="https://img.shields.io/badge/Microservices-Architect-blueviolet?logo=microgen" />
  <img src="https://img.shields.io/badge/Docker-Containers-2496ED?logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/AWS-Cloud-232F3E?logo=amazonaws&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_AI-AI%20Developer-40AEF0?logo=spring&logoColor=white" />
</p>

---

## 🚀 About Me
I'm a passionate **Java Developer** who builds **scalable backend systems**, **enterprise applications**, and **cloud-ready microservices**.  
I love clean architecture, high-performance APIs, and integrating modern technologies like **Spring AI** and **React**.

---

# 🛠️ Tech Stack

### 💻 Backend & Architecture
<p>
  <img src="https://img.shields.io/badge/Java-17/21-orange?logo=java&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_Boot-%236DB33F?logo=springboot&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_Security-%236DB33F?logo=springsecurity&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_Data_JPA-%236DB33F?logo=hibernate&logoColor=white" />
  <img src="https://img.shields.io/badge/Microservices-Architecture-blueviolet" />
  <img src="https://img.shields.io/badge/Spring_AI-Integration-40AEF0?logo=spring" />
</p>

<p>
  <img src="https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/SQL_Server-CC2927?logo=microsoftsqlserver&logoColor=white" />
  <img src="https://img.shields.io/badge/Hibernate-59666C?logo=hibernate&logoColor=white" />
</p>


### ☁️ Cloud & DevOps
<p>
  <img src="https://img.shields.io/badge/AWS-Cloud-232F3E?logo=amazonaws&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-%232496ED?logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/GitHub_Actions-CI/CD-2088FF?logo=githubactions&logoColor=white" />
  <img src="https://img.shields.io/badge/Railway-Deployment-000000?logo=railway&logoColor=white" />
</p>

### 🎨 Frontend & UI
<p>
  <img src="https://img.shields.io/badge/React-50%25-61DAFB?logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/JavaFX-Desktop-blue?logo=java&logoColor=white" />
</p>

### 🔧 Tools
<p>
  <img src="https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white" />
  <img src="https://img.shields.io/badge/Maven-C71A36?logo=apachemaven&logoColor=white" />
  <img src="https://img.shields.io/badge/Linux-blue?logo=linux&logoColor=white" />
  <img src="https://img.shields.io/badge/Postman-FF6C37?logo=postman&logoColor=white" />
  <img src="https://img.shields.io/badge/IntelliJ_IDEA-000000?logo=intellijidea&logoColor=white" />
</p>

---

# 📌 What I Build
- Distributed microservices  
- Event-driven architectures  
- Multi-tenant enterprise systems  
- Modular monoliths  
- AI-powered apps using Spring AI  
- React dashboards  
- JavaFX desktop applications  
- Cloud-deployed solutions with Docker + AWS  

---

# 🚧 Featured Projects
## 🧩 AISMS — Multi-Tenant Enterprise Management System

AISMS is a fully modular, BusinessUnit-scoped, role-based, and approval-driven enterprise platform. Every operational record is scoped by **business_unit_id**, and user access is restricted to their **primary + assigned Business Units**.

---

### 🔥 1) Purpose & Goals
- Unified system for **Inventory, Sales, Purchases, CRM, Invoicing, Documents, Expenses, Approvals, Reporting**.
- Data visibility restricted through BusinessUnit scoping.
- Dynamic architecture using **type tables** and **custom_fields JSON**.
- Governance enforced via **approval_status** on all operational entities.

---

### 👥 2) Users & Access Model
- Each user has:
  - `primary_business_unit_id`
  - Additional BUs via **UserBusinessUnitRole**
- One role per user per BU → enforced by **UNIQUE(user_id, business_unit_id)**.
- Permissions flow: **Role → Permission**.
- Effective BU scope = `{primary BU} ∪ {assigned BUs}`.
- All queries must filter by:
  `business_unit_id IN (:allowedBUIds)`.

---

### 🗂️ 3) Multi-BU Data Partitioning
- No tenant ID — **BusinessUnit is the partition**.
- All scoped entities include:
  - `business_unit_id`
  - `approval_status` (PENDING | APPROVED | REJECTED | RETURNED)
  - `custom_fields JSON`
  - `is_active`, timestamps
- Cross-BU workflows (e.g., StockTransfer) explicitly reference both source and destination BUs.

---

### 🏗️ 4) Core Domain Model
- **BusinessUnit** (+ optional hierarchy)
- Global: User, Role, Permission
- Scoped membership: **UserBusinessUnitRole**  
- Every operational entity inherits base fields (BU, approval, customization).

---

### 📦 5) Modules (BU-Scoped & Type-Driven)

#### 📊 Inventory  
- ProductType, ProductCategory, Product  
- StockItem, StockAdjustment(+Type)  
- StockTransfer(+Items)

#### 🛒 Sales (POS)  
- PromotionType, Promotion  
- SaleTransaction, SaleItem  
- PaymentType, Payment

#### 📦 Purchases & Suppliers  
- SupplierType, Supplier  
- PurchaseType, PurchaseOrder, PurchaseItem  
- GoodsReceipt(+Items)

#### 💳 Invoicing (AP/AR)  
- InvoiceType, Invoice  
- InvoicePayment

#### 🧑‍🤝‍🧑 CRM  
- CustomerType, Customer

#### 📄 Documents  
- DocumentType, Document (linkable to any entity)

#### ✔️ Approvals  
- ApprovalConfiguration  
- ApprovalRequest  
- ApprovalLog

#### 🔔 Notifications & Reporting  
- NotificationType, Notification  
- ReportType, Report, ReportSchedule

#### 💰 Expenses  
- ExpenseType, Expense

#### 🧩 Customization  
- `custom_fields JSON` everywhere  
- Optional: CustomField + EntityCustomFieldValue

---

### 🔄 6) Key Workflows
- **Sales** → Scan → Promotions → Payment → Stock decrement → Optional invoice  
- **Purchasing** → PO → GoodsReceipt → Stock increment → Supplier invoice  
- **Stock Transfer BU→BU** → Request → Approval → Ship/Receive  
- **Approval Flow** → Pending → Routed via ApprovalConfiguration → Logged in ApprovalLog  

---

### 🔐 7) Security & Enforcement
Backend (Spring Security):
- Resolve allowed BUs
- Enforce permission + BU checks

Frontend:
- User selects active BU
- UI hides unauthorized modules automatically

---

### ⚙️ 8) Tech Stack
- Spring Boot, JPA/Hibernate, Spring Security  
- PostgreSQL (JSONB, enums, Flyway)  
- Optional: Redis, RabbitMQ/Kafka  
- SMTP, SMS/WhatsApp  
- File storage: S3 / MinIO

---

### 🧩 9) Schema & Conventions
- PKs = BIGSERIAL  
- Enums: `approval_status`, `business_unit_status`  
- JSONB used for custom fields and rules  
- Unique per BU: `(business_unit_id, code)` and `(business_unit_id, sku)`  
- Index all foreign keys + business_unit_id  

---

### 📈 10) Observability & Ops
- AuditLog for sensitive actions  
- BU context in all logs  
- Metrics: throughput, stock accuracy, approval latency  
- Daily backups  
- Dev → Staging → Prod environments  

---

### 🧱 11) Extensibility
- Add new type tables (ProductType, DocumentType, etc.) without code  
- Custom fields for metadata flexibility  
- Approval rules defined entirely in data  

---

### 🧪 12) Testing Strategy
- Unit: services, approval transitions  
- Integration: BU filters, FKs  
- E2E: role matrix, BU boundaries  

---

### 🛠️ 13) Delivery Roadmap
1. Foundation: BU + Users + Roles + Permissions  
2. Inventory Core  
3. Sales & Payments  
4. Purchasing & Accounts Payable  
5. CRM & Accounts Receivable  
6. Documents + Approvals  
7. Notifications + Reporting  
8. Hardening, Observability, Indexing  

---

### ✅ AISMS Summary
A scalable, BusinessUnit-scoped enterprise system with strict access control, data-driven configuration, multi-stage approvals, and modular domain architecture — designed for organizations needing clean data separation, robust workflows, and operational excellence.


### 🔍 Lost & Found System
- REST API with Spring Boot  
- Image processing  
- Admin role restrictions  

---

# 🧠 Strengths
✔ Clean, maintainable coding style  
✔ Strong understanding of backend architecture  
✔ Excellent debugging skills  
✔ Fast learner  
✔ Strong in system design & problem-solving  

---

### 🏆 GitHub Achievements

<p align="left">
  <a href="https://github.com/users/CyprianDavis/achievements/pair-extraordinaire">
    <img src="https://github.githubassets.com/images/modules/profile/achievements/pair-extraordinaire-default.png" width="90" title="Pair Extraordinaire" />
  </a>

  <a href="https://github.com/users/CyprianDavis/achievements/quickdraw">
    <img src="https://github.githubassets.com/images/modules/profile/achievements/quickdraw-default.png" width="90" title="Quickdraw" />
  </a>

  <a href="https://github.com/users/CyprianDavis/achievements/pull-shark">
    <img src="https://github.githubassets.com/images/modules/profile/achievements/pull-shark-default.png" width="90" title="Pull Shark" />
  </a>
</p>

---

# 📫 Let's Connect
<p>
  <a href="mailto:sserembacyprian25@gmail.com">
    <img src="https://img.shields.io/badge/Email-Contact_me-red?logo=gmail&logoColor=white" />
  </a>

  <a href="https://www.linkedin.com/in/sseremba-cyprian/">
    <img src="https://img.shields.io/badge/LinkedIn-Profile-blue?logo=linkedin&logoColor=white" />
  </a>

  <a href="https://github.com/CyprianDavis">
    <img src="https://img.shields.io/badge/GitHub-Follow-black?logo=github&logoColor=white" />
  </a>
</p>

---

# ⚡ Fun Fact
**I don't just write Java code — I architect reliable systems that power real businesses.**
