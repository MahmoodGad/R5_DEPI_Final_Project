# Requirements Gathering

## Stakeholder Analysis

| Stakeholder | Role | Needs | Influence |
|---|---|---|---|
| Marketing manager | Runs retention campaigns | List of high-risk customers; churn by segment | High |
| Customer retention / success team | Contacts at-risk customers | Prioritized customers and likely churn drivers | High |
| Executive management | Business decisions | Overall churn rate, trends, revenue impact | High |
| Product manager | Plan and pricing design | Churn by subscription type and features | Medium |
| Customer support | Handles complaints | Link between services (e.g. TechSupport, OnlineSecurity) and churn | Medium |
| Data/IT team | Data access and maintenance | Clear data dictionary, reproducible pipeline | Medium |
| Project team and instructor | Build and evaluate | Complete, documented, well-presented deliverables | High |

---

## User Stories & Use Cases

### User Stories
| ID | As a... | I want to... | So that... |
|---|---|---|---|
| US-01 | Marketing manager | see the list of high-risk customers | I can target them with retention offers |
| US-02 | Executive | see the overall churn rate and its trend | I can track business health |
| US-03 | Marketing manager | view churn by customer segment | I can design differentiated campaigns |
| US-04 | Product manager | view churn by subscription type | I can adjust plans and pricing |
| US-05 | Retention analyst | filter the dashboard by segment, plan and period | I can explore specific groups |
| US-06 | Data analyst | query customer, service, contract and billing tables with SQL | I can investigate churn patterns |
| US-07 | Data scientist | compare several classification models | I can choose the best one for deployment |
| US-08 | Stakeholder | read a clear business report | I can understand the findings without technical background |

### Use Cases
#### UC-01: View churn overview
- **Actor:** Executive, Marketing manager
- **Precondition:** Dashboard is running with data loaded
- **Main flow:** Open dashboard, view churn rate, trends, churn by segment and subscription type
- **Postcondition:** User understands current churn situation

#### UC-02: Identify high-risk customers
- **Actor:** Marketing manager, Retention team
- **Precondition:** Model predictions are generated
- **Main flow:** Open high-risk list, filter or sort by risk, export or review customers
- **Postcondition:** Retention targets are selected

#### UC-03: Explore churn by group
- **Actor:** Analyst
- **Main flow:** Apply filters (segment, subscription type, period), review updated charts
- **Postcondition:** Insight about a specific group

#### UC-04: Train and compare models
- **Actor:** Data scientist
- **Main flow:** Load cleaned data, train the four classifiers, compute metrics, compare, select best model
- **Postcondition:** Selected model and comparison results documented

---

## Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | The system shall load the Telco Customer Churn dataset into a relational database, split into tables (customers, services, contracts/billing) | High |
| FR-02 | The system shall provide SQL scripts to query churn-related data | High |
| FR-03 | The system shall clean missing and inconsistent values (e.g. blank `TotalCharges`, which must be converted from text to numeric) | High |
| FR-04 | The system shall perform EDA on customer characteristics and churn | High |
| FR-05 | The system shall analyze relationships between customer characteristics and churn | High |
| FR-06 | The system shall train multiple classification models: Logistic Regression, KNN, Decision Tree, SVM | High |
| FR-07 | The system shall compare model performance using evaluation metrics and select the best model | High |
| FR-08 | The system shall produce customer-level churn predictions | High |
| FR-09 | The dashboard shall display the overall churn rate | High |
| FR-10 | The dashboard shall display churn by customer segment | High |
| FR-11 | The dashboard shall display churn by subscription type | High |
| FR-12 | The dashboard shall display churn trends by customer tenure (cohorts such as 0-12, 13-24, 25-48, 49+ months), since the dataset has no calendar dates | High |
| FR-13 | The dashboard shall display a high-risk customer list | High |
| FR-14 | The project shall include a data dictionary describing every field | Medium |
| FR-15 | The project shall include a final business report explaining findings to a stakeholder | High |
| FR-16 | The repository shall include a README with setup and run instructions | High |
| FR-17 | (Optional) Track experiments and register the model with MLflow, serve predictions through FastAPI | Low |

---

## Non-Functional Requirements

| ID | Category | Requirement |
|---|---|---|
| NFR-01 | Performance | Dashboard filters should update within a few seconds on the project dataset |
| NFR-02 | Performance | Model training and prediction should finish in reasonable time on a standard laptop |
| NFR-03 | Security / Privacy | Use anonymized or public customer data; do not use project data outside the initiative |
| NFR-04 | Security | No credentials or secrets committed to GitHub |
| NFR-05 | Usability | Dashboard should be understandable by non-technical stakeholders, with clear titles and labels |
| NFR-06 | Reliability | Pipeline should run end to end without errors from a clean environment |
| NFR-07 | Reproducibility | Fixed random seeds, a requirements file, and documented steps to reproduce results |
| NFR-08 | Maintainability | Clean, commented, modular code following consistent naming conventions |
| NFR-09 | Portability | Runs on Windows, macOS and Linux with documented Python dependencies |
| NFR-10 | Documentation | All documents stored in the GitHub repository and kept up to date |

---

