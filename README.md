# Natural Language to SQL Query Agent

![Project Banner](https://img.shields.io/badge/Status-Active-brightgreen) ![License](https://img.shields.io/badge/License-MIT-blue)

## Overview

This project implements a **Natural Language to SQL Query Agent**, an AI-powered system capable of converting human-readable questions into executable SQL queries and returning the results automatically. The agent is built using **n8n**, **Supabase**, and a **chat AI model (Gemini)**.

The goal is to simplify database querying by allowing users to interact with a database in plain English without needing SQL knowledge.

---

## Key Features

* **Natural Language Understanding**: Converts plain English queries into SQL commands.
* **Automated Query Execution**: Executes generated SQL queries on a PostgreSQL database.
* **Simple Memory Storage**: Uses lightweight memory to store context and previous interactions.
* **Real-Time Responses**: Replies to user queries immediately via n8n workflow triggers.
* **Database Tool Integration**: Fully integrated with Supabase PostgreSQL for data storage and retrieval.

---

## Architecture & Workflow

```mermaid
flowchart TD
    A[User sends a chat message] --> B[n8n Workflow Trigger]
    B --> C[AI Agent (Gemini)]
    C --> D[Memory (Simple Context Storage)]
    C --> E[SQL Query Generator]
    E --> F[Supabase PostgreSQL Executor]
    F --> G[Query Result Returned to User]
```

**Step-by-step workflow:**

1. **Trigger**: User sends a natural language message via chat or web interface.
2. **AI Agent**: The message is processed by the AI model (Gemini) to interpret intent.
3. **Memory**: Simple memory stores previous interactions to maintain context if needed.
4. **Query Generation**: The AI generates a SQL query based on the user input.
5. **Execution**: SQL query is executed on the Supabase PostgreSQL database.
6. **Response**: The agent returns query results to the user in a readable format.

---

## Technologies Used

* **[n8n](https://n8n.io/)** – Automation workflow for triggering AI actions.
* **[Supabase](https://supabase.com/)** – PostgreSQL backend for storing and querying data.
* **[Gemini AI Model](https://gemini.com/)** – AI model for natural language understanding.
* **PostgreSQL** – Database for storing structured data.

---

## Installation

### Prerequisites

* Node.js v18+
* n8n installed globally (`npm install n8n -g`)
* Supabase project with PostgreSQL database
* Access to Gemini AI API or model

### Setup Steps

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/nl-to-sql-agent.git
   cd nl-to-sql-agent
   ```
2. Install dependencies:

   ```bash
   npm install
   ```
3. Configure environment variables in `.env`:

   ```env
   GEMINI_API_KEY=your_api_key_here
   SUPABASE_URL=your_supabase_url
   SUPABASE_KEY=your_supabase_key
   ```
4. Start the n8n workflow:

   ```bash
   n8n start
   ```

---

## Usage

1. Send a message to the chat interface.
2. The AI agent interprets your question.
3. The system generates and executes a SQL query.
4. Query results are returned directly in the chat.

**Example:**

* **Input:** “Show total sales for 2023 by product category.”
* **Generated SQL:**

  ```sql
  SELECT category, SUM(sales) as total_sales
  FROM sales_data
  WHERE year = 2023
  GROUP BY category;
  ```
* **Output:**

  | Category    | Total Sales |
  | ----------- | ----------- |
  | Electronics | 1,200,000   |
  | Furniture   | 800,000     |

---

## Contributing

Contributions are welcome! You can:

* Suggest new features
* Report bugs
* Submit pull requests

Please follow standard GitHub PR guidelines.

---



