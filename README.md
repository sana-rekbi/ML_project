# ML_project
# 🤖 AI Chatbot for Food Delivery System using Dialogflow, Python, and FastAPI

## 📌 Project Overview
In this project, we have built an **AI-powered chatbot** designed to handle food delivery orders. The chatbot uses **Dialogflow** for natural language understanding (NLU) to recognize user intents and extract relevant entities. We have integrated a backend using **Python (FastAPI)** and a **MySQL database** to store user data and order details.

This project demonstrates the use of **AI agent techniques**, including:
- **Natural Language Processing (NLP)** for understanding and responding to user queries.
- **Context management** to handle conversations smoothly.
- **Autonomous decision-making** for recommending food items based on user preferences.

## 🚀 Features
- **Conversational AI**: Uses Dialogflow to interpret user inputs and respond intelligently.
- **Contextual Understanding**: Utilizes Dialogflow contexts to manage conversation flow and track user sessions.
- **Backend API**: Built with FastAPI to handle interactions between the chatbot and the database.
- **Database Integration**: MySQL database to store order history, user preferences, and more.
- **AI Agent Techniques**: Uses NLP and autonomous decision-making to enhance user interactions.

## 🗂 Directory Structure
```
project-root/
├── backend/                    # Contains Python FastAPI backend code
│   ├── main.py                 # Main backend application
│   ├── database.py             # MySQL database connection
│   ├── models.py               # Data models for FastAPI
│   ├── routes/                 # API routes
│   └── utils/
│       └── dialogflow_utils.py # Helper functions for Dialogflow
├── db/                         # MySQL database dump
├── dialogflow_assets/          # Dialogflow intents, entities, and contexts
├── frontend/                   # Website frontend code
└── README.md
```

## 🛠 Installation Guide

### Step 1: Clone the Repository

### Step 2: Set Up a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate    # On Windows: venv\Scripts\activate
```

### Step 3: Install Dependencies
```bash
pip install -r backend/requirements.txt
```
Alternatively, install the key modules manually:
```bash
pip install mysql-connector
pip install "fastapi[all]"
```

## 🚀 Running the Backend Server
```bash
cd backend
uvicorn main:app --reload
```

### Expose the local server using ngrok (for HTTPS)
- Download [ngrok](https://ngrok.com/download) and extract it.
- Run the following command:
```bash
ngrok http 8000
```
Use the HTTPS URL provided by ngrok to integrate with Dialogflow.

## 💡 Dialogflow Setup

1. **Create a Dialogflow Agent**:
   - Go to the [Dialogflow Console](https://dialogflow.cloud.google.com/).
   - Create a new agent and import the contents from the `dialogflow_assets/` folder.

2. **Define Intents and Entities**:
   - **Intents**: `OrderFood`, `CheckOrderStatus`, `CancelOrder`
   - **Entities**: Extract information such as `FoodItem`, `Quantity`, and `Location`.

3. **Contexts**:
   - Use contexts to maintain conversation state and handle follow-up queries.

## 📡 API Endpoints
| Method | Endpoint               | Description                     |
|--------|------------------------|---------------------------------|
| GET    | `/`                   | Welcome route                   |
| POST   | `/order`              | Place a new food order          |
| GET    | `/order/{order_id}`   | Retrieve the status of an order |
| DELETE | `/order/{order_id}`   | Cancel an existing order        |

## 📊 AI Agent Techniques Used

### 1. Natural Language Understanding (NLP)
The chatbot uses **Dialogflow** to process user inputs, detect intents, and extract entities like food items and delivery addresses.

### 2. Context Management
By leveraging **contexts**, the chatbot maintains conversation flow, enabling it to handle follow-up questions seamlessly.

### 3. Autonomous Decision-Making
The backend API processes user inputs and makes autonomous decisions, such as recommending popular dishes or adjusting orders based on availability.

## 🛠 Database Setup

1. **Create a MySQL database**:
```sql
CREATE DATABASE food_delivery;
```
2. **Import the database dump** using MySQL Workbench or the command line:
```bash
mysql -u root -p food_delivery < db/food_delivery_dump.sql
```
3. **Update database connection details** in `backend/database.py`:
```python
DATABASE_CONFIG = {
    "user": "your_username",
    "password": "your_password",
    "host": "localhost",
    "database": "food_delivery"
}
```

## 🤖 Example Interactions
**User**: "I want to order a pizza"
   - **Bot**: "What size would you like? Small, Medium, or Large?"
