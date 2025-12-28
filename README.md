# 🏢 Shadow Workplace: The AI Job Simulator

> **"Stop learning tutorials. Start working a real job."**

Shadow Workplace is an AI-powered simulation engine that mimics a high-pressure software engineering environment. Instead of guiding users through tutorials, it assigns them vague Jira tickets, creates real GitHub repositories, and uses an AI "Senior Engineer" to reject their code if it isn't production-ready.

---

## 🏗 Architecture

The system is built on the **Supervisor-Worker** pattern using **LangGraph**. A central "Brain" orchestrates three specialized agents to simulate a real dev team.

```mermaid
graph TD
    User(User "Alex") -->|1. Selects Job| Manager(Product Owner Agent)
    Manager -->|2. Generates Specs| State[Shared State]
    State -->|3. Trigger| GitOps(GitOps Agent)
    GitOps -->|4. Creates Repo & Issues| GitHub[User's GitHub]
    User -->|5. Pushes Code/PR| GitHub
    GitHub -->|6. Webhook| Senior(Senior Engineer Agent)
    Senior -->|7. Strict Review| GitHub
