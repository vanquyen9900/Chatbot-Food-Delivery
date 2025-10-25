# 🍜 Chatbot Food Delivery (Vietnamese Cuisine)

A conversational AI chatbot for Vietnamese food ordering — built using **Dialogflow ES**, **FastAPI**, and **MySQL**.  
The bot can take new orders, modify existing ones, and track delivery status in real time.

---

## 🚀 Features

- 💬 Natural conversation flow using **Dialogflow ES**
- 🍽️ Handles intents like:
  - `new.order` – start a new food order
  - `order.add` – add menu items with quantity
  - `order.remove` – remove items from order
  - `order.complete` – finalize the order
  - `track.order` – track existing orders
- 🧠 Webhook fulfillment with **FastAPI**
- 🗄️ Menu and orders stored in **MySQL**
- 🇻🇳 Adapted for **Vietnamese dishes** and prices

---

## 🍲 Menu (Vietnamese Dishes)

| Item ID | Dish Name               | Price (USD) |
|----------|------------------------|--------------|
| 1 | Pho | 7.00 |
| 2 | Banh Mi | 4.50 |
| 3 | Bun Cha | 6.50 |
| 4 | Com Tam | 6.00 |
| 5 | Bun Bo Hue | 7.50 |
| 6 | Goi Cuon | 4.00 |
| 7 | Banh Xeo | 5.50 |
| 8 | Hu Tieu | 6.00 |
| 9 | Vietnamese Iced Coffee | 3.50 |

---

## 🧩 Project Structure

```
Chatbot_Food_Delivery/
│
├── main.py                 # FastAPI webhook server
├── requirements.txt        # Python dependencies
├── pandeyji_eatery_vietnamese.sql  # Database schema + data
├── templates/
│   ├── index.html          # Chat UI for testing
│   └── script.js           # Handles frontend interactions
├── static/
│   ├── css/
│   └── images/
│
└── README.md
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/<your-username>/Chatbot_Food_Delivery.git
cd Chatbot_Food_Delivery
```

### 2️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 3️⃣ Import Database
Use MySQL Workbench or CLI to import:
```bash
source pandeyji_eatery_vietnamese.sql;
```

### 4️⃣ Run FastAPI Server
```bash
uvicorn main:app --reload
```
Server will start at:  
👉 `http://127.0.0.1:8000`

### 5️⃣ (Optional) Connect to Dialogflow
- Go to [Dialogflow Console](https://dialogflow.cloud.google.com)
- Create an **agent**
- Enable **Fulfillment webhook**
- Set the webhook URL:
  ```
  https://<your-ngrok-url>/webhook
  ```
- Enable **Webhook Call** for each intent.

---

## 🧠 Webhook Example

### Sample Request (Dialogflow → Webhook)
```json
{
  "queryResult": {
    "intent": { "displayName": "order.add" },
    "parameters": {
      "food-item": ["Pho"],
      "number": [2]
    }
  }
}
```

### Sample Response (Webhook → Dialogflow)
```json
{
  "fulfillmentText": "Added 2 Pho to your order!"
}
```

---

## 🧱 Technologies Used

| Component | Technology |
|------------|-------------|
| Backend | FastAPI (Python) |
| Database | MySQL |
| AI Engine | Dialogflow ES |
| Frontend | HTML, CSS, JS |
| Tunneling | Ngrok |

---

## 🐞 Common Issues

| Issue | Solution |
|-------|-----------|
| `500 Internal Server Error` on Dialogflow | Check your webhook logs (`print(payload)`), ensure JSON fields match Dialogflow format |
| CORS Error on web demo | Add `app.add_middleware(CORSMiddleware, allow_origins=["*"], allow_methods=["*"], allow_headers=["*"])` |
| MySQL not connecting | Verify credentials in `main.py` and ensure MySQL service is running |

---

## 🎨 Preview

### 🍱 Sample Menu
![Vietnamese Menu](assets/menu_vietnamese.jpg)

### 💬 Chat Demo
![Chat Demo](assets/chat_ui.jpg)

---
