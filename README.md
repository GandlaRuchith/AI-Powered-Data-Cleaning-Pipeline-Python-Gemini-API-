🧠 Universal AI-Powered Data Cleaning Pipeline (Python + Gemini API)

📌 Project Overview

This project focuses on automating the cleaning and structuring of raw, unstructured enterprise data across any domain (Supply Chain, Finance, CRM, Healthcare) using Generative AI (Google Gemini API) integrated within a Python ETL pipeline.
The objective was to convert messy, inconsistent composite text fields (like product names, transaction memos, or lead descriptions) into cleanly structured columns dynamically dictated by the prompt (e.g., entity_or_merchant, category, and channel).

The solution utilizes a hybrid approach: fast Pandas heuristics for basic formatting, combined with prompt engineering and JSON-enforced AI responses to ensure structured, production-ready outputs for complex text.

🚀 Problem Statement

Raw enterprise datasets consistently contain:

Inconsistent naming formats

Embedded attributes (e.g., SKUs in product names, location codes in bank statements)

Mixed casing

Spelling errors and abbreviations

Random spacing

Multiple distinct data points merged into a single string

Manual cleaning was:

Time-consuming

Error-prone

Not scalable across different departments

🛠 Solution Architecture

🔹 Technology Stack

Python

Google Gemini API (gemini-3.6-flash)

Pandas & Regex (Hybrid preprocessing)

JSON-enforced mapping

Unique-item batch processing

Permission-safe file saving logic

🧠 GenAI Prompt Engineering Logic

The system prompt was carefully designed to adapt to any dataset by instructing the AI to:

Identify the core entity (brand, merchant, or person).

Extract categorical data (product type, financial category, or job title).

Isolate specific attributes (SKUs, payment channels, or locations).

Correct spelling errors automatically.

Normalize casing.

Enforce strict JSON output mapping for the parsed elements.

Examples Across Domains:

Finance Domain Input:
UBER *TRIP SF CA 09/21

Finance Output:

JSON
{
  "entity_or_merchant": "Uber",
  "category": "Travel/Transport",
  "channel": "Card"
}
SCM Domain Input:
Parle-G Gold Biscuits -10 RS

SCM Output:

JSON
{
  "main_product": "Parle-G",
  "product_type": "Gold Biscuits",
  "SKU": "10 RS"
}
🔄 ETL Pipeline Design

1️⃣ Data Extraction & Preprocessing

Loaded the raw CSV dataset.

Utilized Pandas and Regex to automatically clean standard tabular data (standardizing dates, stripping currency symbols, resolving booleans, formatting countries) before API interaction.

2️⃣ Transformation (AI-Based Cleaning)

Isolated only unique composite strings (e.g., transaction descriptions or product names) to optimize API usage and avoid redundant API calls.

Sent batched items to Gemini with instructions to enforce a structured JSON output based on the specific domain's needs.

Handled API responses with robust JSON parsing and fallback error handling.

3️⃣ Incremental Loading & Safe Saving

Mapped the AI-parsed JSON results back into the full dataset seamlessly.

Implemented a safe-saving loop that prevents PermissionError (e.g., if the destination file is open in Excel) by dynamically appending version numbers to the output file.

📊 Key Features

✔ Hybrid cleaning architecture (Pandas Regex + GenAI)
✔ AI-based structured entity extraction & spelling correction
✔ API-optimized batching (processing only unique items)
✔ Deterministic output (JSON structured mapping)
✔ Dynamic safe file-saving mechanism to prevent data loss
✔ Highly adaptable, domain-agnostic core engine (works for any industry)

📈 Business Impact

Reduced manual data cleaning effort significantly.

Standardized unstructured text into highly accurate tabular columns.

Improved downstream analytics accuracy in BI dashboards.

Enabled consistent reporting (e.g., merchant-level spend, SKU-level inventory).

Replaced hundreds of brittle Regex rules with a single adaptable AI prompt.

🧪 Example Workflow

Load messy CSV from any domain.

Clean standard columns using fast Pandas heuristics (dates, numbers, countries).

Isolate unique composite text strings and process them through the AI.

Map extracted structured fields back to the main dataframe.

Save results safely to disk, avoiding file-lock crashes.

🧩 Why This Project is Important

This project demonstrates:

Practical application of Generative AI in real business workflows.

Prompt engineering for structured data extraction.

Production-level Python scripting and error handling.

ETL pipeline thinking and API optimization.

Data standardization for enterprise analytics across multiple domains.

🏷 Tech Keywords (For Recruiters)

Python, Google Gemini API, Prompt Engineering, JSON Parsing, ETL Pipeline, Data Cleaning, Data Engineering, Pandas, Regex, Automation, Domain-Agnostic Architecture
