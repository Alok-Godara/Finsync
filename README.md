# 💸 FinSync – Startup Expense Management Web App

**FinSync** is a responsive, collaborative expense and fund management web application designed for **startups, small teams, or any group managing shared finances**.  
It allows users to **create or join companies**, **submit and manage expenses**, **add funds**, and **track reimbursements** — all synchronized in real time using **Supabase**.

---

## 🚀 Features

- 🔐 **Authentication** using **Supabase Auth** (Email/Password)
- 🏢 **Company Management**
  - Create, update, and delete companies  
  - Join or leave a company anytime  
- 💰 **Expense Management**
  - Add, edit, or delete expenses with receipt upload  
  - Filter and view expenses by user or company  
- 💵 **Fund Management**
  - Add and update total funds for each company  
  - Track available balance and fund inflow  
- ✅ **Reimbursement Tracking**
  - Mark expenses as `pending`, `approved`, or `reimbursed`  
- 📊 **Dashboard**
  - Real-time analytics for total funds, expenses, and categories  
- 📱 **Responsive Design**
  - Fully optimized for mobile, tablet, and desktop devices  
- ☁️ **Built with Supabase**
  - PostgreSQL (Database), Auth, and Storage for images and receipts  

---

## 🧠 Project Goals

- Simplify fund and expense management for small teams and startups  
- Maintain transparency and accountability in reimbursements  
- Provide a mobile-compatible web solution with real-time synchronization  

---

## 🧾 Tech Stack

| Layer | Technology |
|-------|-------------|
| **Frontend** | React.js, HTML5, CSS3 (Responsive Design) |
| **Backend / Database** | Supabase (PostgreSQL, Realtime, Storage, Auth) |
| **Authentication** | Supabase Auth (Email/Password) |
| **Version Control** | Git & GitHub |
| **Deployment (Optional)** | Netlify / Vercel |

---

## 🗄️ Simplified Database Schema (Supabase)

```
-- USERS
create table users (
  id uuid primary key default uuid_generate_v4(),
  name text,
  email text unique
);

-- COMPANIES
create table companies (
  id uuid primary key default uuid_generate_v4(),
  name text,
  owner_id uuid references users(id)
);

-- EXPENSES
create table expenses (
  id uuid primary key default uuid_generate_v4(),
  user_id uuid references users(id),
  company_id uuid references companies(id),
  amount numeric,
  category text,
  description text,
  image_url text,
  status text check (status in ('pending', 'approved', 'reimbursed')) default 'pending',
  created_at timestamp default now()
);

-- FUNDS
create table funds (
  id uuid primary key default uuid_generate_v4(),
  company_id uuid references companies(id),
  amount numeric,
  created_at timestamp default now()
);
```

## 🖼️ Image Upload

- Receipts and bills are stored in **Supabase Storage**.  
- Public bucket access allows secure URL-based image preview.

---

## 🔐 Setup Instructions

1. Clone the repository  
   ```bash
   git clone https://github.com/your-username/finsync.git
   ```
2. Create a .env file with your Supabase credentials
     ```bash
     VITE_SUPABASE_URL=your-supabase-url
     VITE_SUPABASE_ANON_KEY=your-anon-key
     ```
3. Install dependencies and start the app
   ```bash
   npm install
   npm run dev
   ```
## 📈 Future Enhancements

- Automated reimbursements via payment APIs  
- Monthly and category-based financial reports  
- Role-based permissions (Admin, Employee)  
- Export data to CSV/PDF  
- AI-based expense categorization and anomaly detection  

---

## 🧩 Project Philosophy

> “Every rupee accountable, every expense visible.”  
> FinSync promotes **financial transparency and trust** in teams by combining simplicity with real-time data synchronization.

---

## 🤝 Contributing

Feel free to fork, suggest improvements, or raise issues via GitHub.
