End-to-End Marketing Analytics Platform | dbt, BigQuery, Mage
From Raw Data to Revenue Insights: A Modern Data Engineering Showcase
This isn't just a project; it's a demonstration of how I translate complex business needs into automated, reliable, and scalable data solutions. This repository showcases a production-grade ELT pipeline that ingests data from disparate marketing channels, centralizes it in a cloud data warehouse, and transforms it into a "single source of truth" ready for strategic analysis.

Why This Project Stands Out
For a potential client, this project demonstrates key capabilities that are crucial for successful data initiatives:

Business Acumen: The project directly solves a common business problem—understanding marketing ROI—by creating a unified data model from fragmented sources.

Modern Tooling: Expertise with the modern data stack (dbt, BigQuery, Mage) shows I am current with industry best practices for efficiency and scalability.

End-to-End Ownership: The pipeline covers the entire data lifecycle, from ingestion and orchestration to transformation and testing, proving I can manage a project from concept to completion.

Production-Ready Practices: The use of version control, modular data models, and a clear project structure are hallmarks of a professional, maintainable, and scalable solution.

🏛️ Architecture: The Blueprint for Success
The pipeline is built on a modern ELT (Extract, Load, Transform) architecture, prioritizing scalability and performance. Raw data is loaded first, allowing for complex, SQL-based transformations to be handled efficiently within the data warehouse.

graph TD
    subgraph "Data Sources (Simulated)"
        A[<img src='https://i.imgur.com/gS1AlmE.png' width='20' /> Google Analytics]
        B[<img src='https://i.imgur.com/8zTjsI4.png' width='20' /> Google Ads]
        C[<img src='https://i.imgur.com/KzJ2p24.png' width='20' /> Meta Ads]
        D[<img src='https://i.imgur.com/k2j4p31.png' width='20' /> Bing Ads]
    end

    subgraph "Ingestion & Orchestration (Mage)"
        E(Mage Pipeline Controller)
    end

    subgraph "Data Warehouse (Google BigQuery)"
        F{Dataset: marketing_raw}
        G{Dataset: marketing_transformed}
    end

    subgraph "Transformation (dbt)"
        H((dbt Core Engine))
    end

    subgraph "Analytics & BI"
        I[/Looker, Tableau, Power BI/]
    end

    A --> E
    B --> E
    C --> E
    D --> E
    E -- Loads Data --> F
    H -- Reads from --> F
    H -- Writes to --> G
    G -- Feeds --> I


🛠️ Tech Stack & Strategic Choices
Every tool in this stack was chosen for its specific strengths in building modern, efficient data platforms.

Component

Technology

Reasoning

Orchestration

 Mage

Provides an intuitive, code-first framework for building and managing data pipelines. Its interactive notebook-style UI is excellent for development, debugging, and demonstrating pipeline logic clearly.

Cloud Provider

 Google Cloud (GCP)

Offers a suite of powerful, fully-managed, and seamlessly integrated data services. The pay-as-you-go model is ideal for cost-effectively scaling projects from proof-of-concept to enterprise-grade.

Data Warehouse

 Google BigQuery

A serverless, highly scalable cloud data warehouse. Its separation of storage and compute allows for lightning-fast querying over massive datasets, making it a top-tier choice for analytical workloads.

Transformation

 dbt (Data Build Tool)

The industry standard for the "T" in ELT. It brings software engineering best practices (version control, testing, documentation) to analytics, enabling the creation of reliable and modular data models.

Core Languages

 Python &  SQL

Python is the premier language for data engineering automation and scripting, while SQL remains the universal language of data manipulation and analysis.

🚀 Get It Running: From Zero to Pipeline in Minutes
Follow these steps to replicate the project environment and run the pipeline locally.

1. Initial Setup
Clone the repository and prepare your environment.

# Clone the project
git clone https://github.com/YOUR_USERNAME/marketing_analytics_platform.git
cd marketing_analytics_platform

# Create and activate a virtual environment
python3 -m venv venv
source venv/bin/activate

# Install all dependencies
pip install -r requirements.txt

2. GCP & BigQuery Configuration
In your GCP project console, enable the BigQuery API.

Create two BigQuery datasets: marketing_raw and marketing_transformed.

Create a GCP Service Account with the BigQuery Data Editor and BigQuery Job User roles.

Download the JSON key for the service account and save it in the project's root directory as gcp-credentials.json.

3. Project Configuration
Update the placeholder values in the following files with your specific GCP Project ID:

dbt: dbt_marketing/profiles.yml (the project field)

Mage: mage_orchestration/marketing_pipeline/metadata.yaml (the gcp_project_id variable)

4. Generate Seed Data
This project uses a Python script to generate realistic mock data for the pipeline.

python data_ingestion/mock_data_generator.py

This command creates the necessary .csv files in the dbt_marketing/seeds/ directory.

5. Launch & Run the Pipeline
Start the Mage orchestrator:

mage start marketing_analytics_platform

Navigate to http://localhost:6789 in your browser.

Execute the pipeline run:

In the Mage UI, open the marketing_pipeline.

Click the "Run @once" button to trigger a new run.

You can monitor the progress of each block (ingest_data -> transform_data) in real-time.

Verify the Output:

Once the pipeline succeeds, navigate to the BigQuery console.

You will find raw tables in the marketing_raw dataset and the final, unified marketing_performance table in the marketing_transformed dataset.

✨ Data Modeling with dbt: The Logic Layer
The dbt project is structured logically to promote modularity, reusability, and clarity.

models/staging: This is the first layer of transformation. Each model cleans and standardizes a single raw source. This includes renaming columns, casting data types, and handling basic data quality issues.

models/intermediate: This layer is for building reusable, logical components. Here, data from different staging models is combined (e.g., unioning ad spend from Google, Meta, and Bing).

models/marts: This is the final layer, representing the data models that business users and BI tools will consume. The marketing_performance model joins ad spend data with analytics data to create a comprehensive view with key metrics like CPC, CPM, and ROAS.

📞 Let's Build Something Great Together
I am passionate about building data solutions that drive business value. If you are looking for a data engineer who combines technical expertise with a clear understanding of business objectives, I would be a great fit for your team.

Ready to discuss your project?

Connect with me on Upwork: [Link to your Upwork Profile]

View my Portfolio: [Link to your Portfolio Website]

Find me on LinkedIn: [Link to your LinkedIn Profile]
