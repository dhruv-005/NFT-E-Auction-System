<h1 align="center">
  NFT E-Auction System 
</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python" />
  <img src="https://img.shields.io/badge/GUI-Tkinter-orange" />
  <img src="https://img.shields.io/badge/Database-SQLite-green" />
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg" />
  <img src="https://img.shields.io/badge/Status-Active-success" />
  <img src="https://img.shields.io/badge/Platform-Desktop-lightgrey" />
</p>


---

## 📖 Introduction

The **NFT E-Auction System** is a **Python-based desktop application** built using **Tkinter**, designed to simulate a real-world **NFT marketplace with auction capabilities**.

This project provides a complete ecosystem where users can:

- Create and manage NFTs  
- Buy and sell digital assets  
- Participate in real-time bidding auctions  
- Track wallet balances and transaction history  

The system integrates **GUI design, database management, and auction logic**, making it a powerful academic and practical implementation of modern digital asset trading systems.

It combines **GUI design, database management, and business logic**, making it ideal for **academic projects and real-world system understanding**.
---

## 🚀 Key Highlights

- 🎯 User Authentication (Signup/Login with hashing)  
- 💰 Wallet Management System  
- 🖼️ NFT Creation with Image Upload  
- 🔄 Buy & Sell Marketplace  
- 🏷️ Auction System with Real-Time Bidding  
- 📊 Transaction Tracking  
- 🧠 Clean Database Architecture  
- 🖥️ Interactive GUI using Tkinter  

---

## 🧠 System Architecture
```text
+--------------------------------------------------+
|                  User Interface                  |
|             (Tkinter GUI Application)            |
|--------------------------------------------------|
| - Login / Signup Screens                         |
| - NFT Marketplace (Buy / Sell)                   |
| - Auction Interface (Bidding System)             |
| - Wallet & Transaction Dashboard                 |
+--------------------------------------------------+
                        │
                        ▼
+--------------------------------------------------+
|              Application Logic Layer             |
|--------------------------------------------------|
| - User Authentication & Validation               |
| - NFT Management (Create, Delete, Display)       |
| - Auction Management (Start, Bid, End)           |
| - Wallet Operations (Balance, Profit/Loss)       |
| - Transaction Processing                         |
+--------------------------------------------------+
                        │
                        ▼
+--------------------------------------------------+
|              Database Management Layer           |
|--------------------------------------------------|
| - SQLite Database                                |
| - Tables: Users, NFTs, Wallets                   |
|   Transactions, Auctions, Bids                   |
| - Data Persistence & Retrieval                   |
+--------------------------------------------------+
                        │
                        ▼
+--------------------------------------------------+
|              File Storage Layer                  |
|--------------------------------------------------|
| - NFT Image Storage (Local Directory)            |
| - Image Handling using Pillow (PIL)              |
+--------------------------------------------------+
```
---

## ⚙️ Tech Stack

| Layer        | Technology Used |
|-------------|----------------|
| Frontend UI | Tkinter (Python GUI) |
| Backend     | Python |
| Database    | SQLite |
| Image Handling | PIL (Pillow) |
| Security    | SHA-256 Password Hashing |

---

## 🗄️ Database Schema

### 👤 Users Table
| Column Name | Data Type | Constraints                 |
| ----------- | --------- | --------------------------- |
| id          | INTEGER   | Primary Key, Auto Increment |
| email       | TEXT      | Unique, Not Null            |
| password    | TEXT      | Not Null                    |

### 🖼️ NFTs Table
| Column Name | Data Type | Constraints                      |
| ----------- | --------- | -------------------------------- |
| id          | INTEGER   | Primary Key, Auto Increment      |
| user_id     | INTEGER   | Foreign Key → users.id, Not Null |
| name        | TEXT      | Not Null                         |
| description | TEXT      | Optional                         |
| price       | REAL      | Not Null                         |
| image_path  | TEXT      | Optional                         |

### 💼 Wallets Table
| Column Name       | Data Type | Constraints                         |
| ----------------- | --------- | ----------------------------------- |
| user_id           | INTEGER   | Primary Key, Foreign Key → users.id |
| balance           | REAL      | Not Null                            |
| total_expenses    | REAL      | Not Null                            |
| total_profit_loss | REAL      | Not Null                            |

### 📜 Transactions Table
| Column Name | Data Type | Constraints                      |
| ----------- | --------- | -------------------------------- |
| id          | INTEGER   | Primary Key, Auto Increment      |
| user_id     | INTEGER   | Foreign Key → users.id, Not Null |
| nft_id      | INTEGER   | Foreign Key → nfts.id            |
| type        | TEXT      | Not Null (buy/sell)              |
| amount      | REAL      | Not Null                         |
| timestamp   | DATETIME  | Default CURRENT_TIMESTAMP        |

### 🏷️ Auctions Table
| Column Name    | Data Type | Constraints                             |
| -------------- | --------- | --------------------------------------- |
| id             | INTEGER   | Primary Key, Auto Increment             |
| nft_id         | INTEGER   | Unique, Foreign Key → nfts.id, Not Null |
| seller_id      | INTEGER   | Foreign Key → users.id, Not Null        |
| min_bid_price  | REAL      | Not Null                                |
| current_bid    | REAL      | Nullable                                |
| current_bidder | INTEGER   | Foreign Key → users.id                  |
| start_time     | DATETIME  | Default CURRENT_TIMESTAMP               |
| end_time       | DATETIME  | Optional                                |

### 🔨 Bids Table
| Column Name | Data Type | Constraints                         |
| ----------- | --------- | ----------------------------------- |
| id          | INTEGER   | Primary Key, Auto Increment         |
| auction_id  | INTEGER   | Foreign Key → auctions.id, Not Null |
| bidder_id   | INTEGER   | Foreign Key → users.id, Not Null    |
| bid_amount  | REAL      | Not Null                            |
| timestamp   | DATETIME  | Default CURRENT_TIMESTAMP           |


---
##  🔗 Relationships Overview
-  One User → Many NFTs
-  One User → One Wallet
-  One User → Many Transactions
-  One NFT → One Auction
-  One Auction → Many Bids
-  One User → Many Bids
  
---
## 🔄 Application Workflow

1. User signs up and logs in  
2. Wallet is initialized with default balance  
3. User creates NFTs (with image upload)  
4. NFTs appear in marketplace  
5. Users can:
   - Buy NFTs  
   - Sell NFTs  
   - Start auctions  
6. Other users place bids  
7. Auction ends:
   - Highest bidder gets NFT  
   - Wallets are updated  
8. Transactions are recorded  
---

## 📸 Screenshort
-  Signup
<img width="900" height="644" alt="Screenshot_2026-04-19_15_45_37" src="https://github.com/user-attachments/assets/460c140a-0997-46e4-b599-79596a9fd40d" />

-  Login
<img width="901" height="649" alt="Screenshot_2026-04-19_15_45_58" src="https://github.com/user-attachments/assets/380d2563-1055-491c-ad1c-26a2a78ee4e1" />

-  Dashboard
<img width="896" height="646" alt="Screenshot_2026-04-19_15_43_13" src="https://github.com/user-attachments/assets/2d8f5acc-3178-4077-bdf8-957e9cb90f30" />
<img width="901" height="649" alt="Screenshot_2026-04-19_15_43_23" src="https://github.com/user-attachments/assets/613f476a-098a-4dd0-8c16-acb465b6c29c" />

-  Auction
<img width="899" height="647" alt="Screenshot_2026-04-19_15_43_34" src="https://github.com/user-attachments/assets/2c4dff79-e789-4231-9adc-7bfa02612c63" />

-  Sell
<img width="894" height="646" alt="Screenshot_2026-04-19_15_44_05" src="https://github.com/user-attachments/assets/620060d3-c4f2-4eac-9541-4aa718bf78c9" />
<img width="897" height="646" alt="Screenshot_2026-04-19_15_44_12" src="https://github.com/user-attachments/assets/6f6ce48a-92fd-49e4-a0da-7f8dba33e258" />

-  Wallet
<img width="893" height="647" alt="Screenshot_2026-04-19_15_44_38" src="https://github.com/user-attachments/assets/7535d167-326f-4639-ba75-2de865889d5c" />

---

## 🔐 Security Features

- Password hashing using SHA-256  
- Input validation for all forms  
- Ownership checks before transactions  
- Secure wallet updates  

---

## 🖥️ Features Breakdown

### 🛒 Marketplace
- Browse all NFTs  
- Search functionality  
- Buy NFTs instantly  

### 💼 Wallet System
- Track balance  
- Monitor expenses  
- View profit/loss  
- Transaction history  

### 🔨 Auction System
- Start auction with minimum bid  
- Place bids dynamically  
- Auto validation of highest bid  
- Auction closing with ownership transfer  

### 🖼️ NFT Management
- Add NFTs with images  
- Remove NFTs  
- View NFT details  

---
## 📦 Installation & Setup

Follow the steps below to set up and run the **NFT E-Auction System** on your local machine.

---

### 🔧 Prerequisites

Make sure you have the following installed:

- Python 3.10 or higher  
- pip (Python package manager)  

> ⚠️ Tkinter usually comes pre-installed with Python.

---

### 📥 Clone the Repository

```bash
git clone https://github.com/your-username/nft-auction-system.git
cd nft-auction-system
```
---
### 📦 Install Dependencies
```bash
pip install pillow
```
---
### 📁 Project Setup
-  Ensure the following structure exists:
  ```bash
      nft-auction-system/
      │── main.py
      │── nft_users.db   (auto-created)
      │── nft_images/    (auto-created)
  ```
---
## ▶️ Run application
```bash
python main.py
```
---
## 📜 License

This project is licensed under the **MIT License**.

Copyright (c) 2026 Dhruv Sonani

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

---

## 👨‍💻 Author

**Dhruv Sonani**  
- 💼 Developer & Student  
- 🔗 GitHub: https://github.com/dhruv-005    

---
