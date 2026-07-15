# 🚀 Supply Prescript: Closed-Loop Prescriptive Analytics

**Domain:** Supply Chain Operations & Operations Research

## 📌 Problem Statement
Predictive analytics (e.g., predicting a supply chain delay) are now standard, but they only tell you *what will happen*. The human operator still has to figure out *what to do*. Furthermore, standard dashboards don't learn; if an operator makes a decision, the system rarely tracks whether that decision actually worked.

## 💡 Use Case
A logistics manager is warned by the predictive model of an impending 14-day delay for microchips. Instead of stopping there, the **SupplyPrescript** engine runs a linear optimization algorithm and *prescribes* three mathematically optimal alternatives:
* **(A)** Pay $15k for Air Freight
* **(B)** Buy from a secondary supplier at a 10% premium
* **(C)** Delay the final product launch

The manager clicks Option A directly in the dashboard. The system writes this decision back to the operational database. Three weeks later, the system evaluates the outcome—learning that air freight actually cost $18k—and adjusts its future optimization weights accordingly (Closed-Loop Analytics).

---

## 🛠 Key Modules & Tech Stack

* **Predictive Model (XGBoost / LightGBM):** Predicts the probability and duration of a supply chain disruption based on historical lead times.
* **Prescriptive Solver (SciPy / PuLP):** A mathematical optimization engine that calculates the absolute best business decisions subject to constraints (Budget, Time, Capacity).
* **Write-Back Architecture (Snowflake & FastAPI):** A transactional pipeline allowing business users to insert operational decisions *back* into the data warehouse, closing the loop.
* **Operational Dashboard (Retool or React):** An interactive interface where users review AI recommendations and execute decisions directly, replacing passive read-only BI reports.

---

## 📅 Week-wise Development Plan

### Week 1: Baselines & Scaffolding
* **ML & Optimization Engine:** Train an XGBoost model on historical mock supply chain data to accurately predict shipment delays (Classification/Regression).
* **Operational UI & Write-Back:** Set up a Retool app (or custom React UI) connected to a PostgreSQL or Snowflake database.

### Week 2: Optimization & Prescriptive UI
* **ML & Optimization Engine:** Define the business constraints (e.g., maximum budget, minimum inventory). Write a SciPy Linear Programming script to generate the 3 best alternative actions when a delay is predicted.
* **Operational UI & Write-Back:** Build the UI cards displaying the model's prescriptions, clearly highlighting the trade-offs (Cost vs. Speed) for each option.

### Mid-Project Review
* **Optimization Audit:** Prove that the SciPy solver never recommends an action that violates the hard budget constraints defined in the code.
* **Write-Back Check:** Ensure that clicking an "Execute Decision" button in the UI successfully performs an `INSERT` statement back into the operational database.

### Week 3: The Closed Loop
* **ML & Optimization Engine:** Write the evaluation script. Compare the *predicted* cost of the user's decision against the *actual* historical outcome stored in the database.
* **Operational UI & Write-Back:** Build an analytics view showing the "Decision ROI"—tracking how often the AI's recommendations resulted in positive business outcomes.

### Week 4: Continuous Learning & Polish
* **ML & Optimization Engine:** Implement a pipeline where the discrepancies discovered in the Closed Loop automatically trigger a re-training of the XGBoost model.
* **Operational UI & Write-Back:** Polish the workflow, ensuring the analyst is no longer just a passive observer, but an active participant in an AI-driven workflow.

### Final Review
* **Goal:** A massive leap from "What will happen?" to "What should we do?" using Operations Research. A true closed-loop operational application that compounds business value over time.

---

## 🌟 Common Project Features
* **Agentic & Automated Workflows:** Replacing manual, human-in-the-loop BI analysis with agentic orchestration, self-healing data pipelines, and prescribed decision-making.
* **Modern Data Architecture (2026 Standards):** Utilizing Lakehouse architectures (Apache Iceberg/Delta Lake), semantic layers, and streaming ingestions to overcome the latency and governance limitations of legacy data warehouses.
* **Write-Back and Closed-Loop Systems:** Moving away from read-only "dead" dashboards. Data flows bidirectionally, allowing user decisions to mutate the underlying databases and retrain models.
* **Strict Governance & Observability:** Treating data quality and metric consistency as engineering requirements (using Circuit Breakers, Great Expectations, and Semantic logic) rather than business afterthoughts.
