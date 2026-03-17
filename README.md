# 🚀 AI-Powered SMME Funding Application Matcher

A full-stack web application that helps Small, Medium, and Micro Enterprises (SMMEs) discover, match, and apply for funding opportunities using AI-driven logic and automated workflows.

🔗 **Live Demo:** https://smmesfundfinder.netlify.app/

---

## 📌 Overview

This system was developed for the Eastern Cape Hackathon 2025 to address the challenge of limited access to relevant funding opportunities for SMMEs.

The platform enables businesses to:

* Discover funding opportunities tailored to their profile
* Automatically generate application content
* Track application progress in real-time

Funders can:

* Manage funding programmes
* Review applications
* Update application statuses

---

## 🧠 Key Features

### 👤 SMME Users

* Create and manage business profiles
* Search and view funding opportunities
* AI-powered matching based on business data
* Auto-generated:

  * Project summaries
  * Motivation letters
* Submit and track applications (Pending → Approved → Rejected)

### 🏢 Funder / Agency Users

* Create and manage funding programmes
* Define eligibility criteria
* Review submitted applications
* Approve or reject applications

---

## 🤖 AI Functionality

* NLP-based matching between SMME profiles and funding criteria
* Intelligent ranking of funding opportunities
* Auto-fill of application content using AI
* Basic input correction (handling spelling variations)
* Multi-language friendly input handling

---

## 🔄 AI Engine Evolution

This project initially used Google Gemini for AI-powered matching and text generation.

It was later upgraded to use the OpenAI API (GPT-based NLP) to improve:

* Matching accuracy
* Natural language generation quality
* Flexibility in prompt engineering

This reflects an iterative development approach and evaluation of AI model performance.

---

## 🧱 Tech Stack

**Frontend**

* HTML
* CSS
* JavaScript

**Backend / Database**

* Supabase (PostgreSQL)
* RESTful API integration

**AI Integration**

* OpenAI API (GPT-based NLP)

**Deployment**

* Netlify (Frontend hosting)

---

## 🗂 Database Design

The system uses a relational database with the following core entities:

* **Users** (SMME & Funder roles)
* **SMMEs** (business profiles)
* **Funders** (organisation profiles)
* **Funding Opportunities** (programmes with criteria)
* **Applications** (submitted funding requests with status tracking)

Includes:

* Foreign key relationships
* Role-based access structure
* JSONB fields for flexible AI-driven matching

---

## ⚙️ Core Functionality

* Multi-user role system (SMME & Funder)
* AI-driven matching and ranking logic
* Dynamic application generation
* Real-time status tracking
* CRUD operations across all entities

---

## 🧪 How It Works

1. SMME creates a profile and submits business details
2. System retrieves available funding opportunities
3. AI evaluates compatibility using structured criteria
4. Opportunities are ranked and displayed
5. User selects a programme
6. AI generates application content
7. Application is submitted and tracked
8. Funder reviews and updates status

---

## 👨‍💻 Author

Developed by [Kamva Njengele & Ayanda Luthuli]

