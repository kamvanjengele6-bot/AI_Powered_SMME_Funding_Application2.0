🚀 FundFinder – AI-Powered SMME Funding Matcher
A full-stack web application that helps Small, Medium, and Micro Enterprises (SMMEs) discover, match, and apply for funding opportunities using Google Gemini AI for intelligent matching and content generation.
🔗 Live Demo: https://smmesfundfinder.netlify.app/

📌 Overview
FundFinder was built to address the challenge of limited access to relevant funding opportunities for SMMEs.
The platform enables businesses to:
- Discover funding opportunities tailored to their profile
- Automatically generate application content (summaries, motivation letters)
- Track application progress in real-time
Funders can:
- Manage funding programmes
- Define eligibility criteria
- Review and update application statuses

🧠 Key Features
👤 SMME Users
- Create and manage business profiles (sector, region, revenue, etc.)
- Search and view funding opportunities
- AI-powered matching using Gemini
- Auto-generated:
- Project summaries
- Motivation letters
- Submit and track applications (Pending → Approved → Rejected)
🏢 Funder / Agency Users
- Create and manage funding programmes
- Define eligibility criteria
- Review submitted applications
- Approve or reject applications

🤖 AI Functionality
- Gemini-powered NLP matching between SMME profiles and funding criteria
- Intelligent ranking of funding opportunities
- Auto-fill of application content (summaries, letters)
- Basic input correction (spelling variations, multilingual input)
- Fallback rule-based matching when Gemini is unavailable

🧱 Tech Stack
Frontend
- HTML
- CSS
- JavaScript
Backend / Database
- Supabase (PostgreSQL)
- RESTful API integration
AI Integration
- Google Gemini API (generative AI for matching & content)
Deployment
- Netlify (Frontend hosting)

🗂 Database Design
Core entities:
- Users (SMME & Funder roles)
- SMMEs (business profiles)
- Funders (organisation profiles)
- Funding Opportunities (programmes with criteria)
- Applications (submitted funding requests with status tracking)
Includes:
- Foreign key relationships
- Role-based access structure
- JSONB fields for flexible AI-driven matching

⚙️ Core Functionality
- Multi-user role system (SMME & Funder)
- Gemini-driven matching and ranking logic
- Dynamic application generation
- Real-time status tracking
- CRUD operations across all entities

🧪 How It Works
- SMME creates a profile and submits business details
- System retrieves available funding opportunities
- Gemini evaluates compatibility using structured criteria
- Opportunities are ranked and displayed
- User selects a programme
- Gemini generates application content
- Application is submitted and tracked
- Funder reviews and updates status

👨‍💻 Author
Developed by [Kamva Njengele & Ayanda Luthuli]
