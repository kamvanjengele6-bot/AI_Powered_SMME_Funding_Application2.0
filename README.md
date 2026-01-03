# AI_Powered_SMME_Funding_Application

A system that helps Small, Medium, and Micro Enterprises (SMMEs) automatically find funding, match opportunities, auto-fill applications, and track status using AI + Supabase + JavaScript.

Live Demo: https://smmesfundfinder.netlify.app/

🚀 1. Project Overview

The AI-Powered SMME Funding Application is a web-based platform built for the Eastern Cape Hackathon 2025.
It enables:

For SMMEs

Create a business profile

Upload project details

Search funding opportunities

AI automatically matches your business with suitable funders

Auto-fill applications using AI

View application history

Track application status (Pending → Approved → Rejected)

For Funders / Agencies

Login and manage funding programmes

View SMME applications

Update status (Approve / Reject)

Upload/update funding criteria

AI Functions

NLP-based opportunity matching

Auto-fill forms (motivation letter, project summary, etc.)

Smart ranking of best funding programmes

Assistance when SMME enters wrong spelling

Multi-language input friendly

🗂 2. System Users

There are 2 user types:

🧑‍💼 1. SMME User

Creates a profile, finds funding, submits applications.

🏢 2. Funder/Agency User

Creates funding programmes, reviews applications, updates status.

Stored inside the same users table, with a role:

SMME ↠ "smme"
FUNDER ↠ "funder"

🧱 3. Database Schema (Supabase)

Below is your final optimized schema.

🔹 users Table

Stores login credentials for both SMMEs and Funders.

create table users (
id uuid primary key default gen_random_uuid(),
email text unique not null,
password_hash text not null,
role text check (role in ('smme','funder')) not null,
created_at timestamptz default now(),
updated_at timestamptz default now()
);

Trigger for auto-updated timestamp:

create or replace function moddatetime()
returns trigger
language plpgsql
as $$
begin
NEW.updated_at = now();
return NEW;
end;

$$
;

create trigger update_users_timestamp
before update on public.users
for each row
execute procedure moddatetime();

🔹 smmes Table

Stores SMME business profile and project details.

create table smmes (
    id uuid primary key default gen_random_uuid(),
    user_id uuid references users(id) on delete cascade,

    business_name text not null,
    owner_name text,
    registration_number text,
    business_sector text,
    region text,
    years_in_operation int,
    annual_revenue numeric,
    number_of_employees int,
    business_description text,
    project_description text,
    fund_usage text,

    created_at timestamptz default now(),
    updated_at timestamptz default now()
);


Trigger:

create trigger update_smmes_timestamp
before update on public.smmes
for each row
execute procedure moddatetime();

🔹 funders Table

Stores Funder/Agency profiles.

create table funders (
    id uuid primary key default gen_random_uuid(),
    user_id uuid references users(id) on delete cascade,

    organisation_name text not null,
    sector_focus text,
    region_focus text,
    contact_person text,
    contact_email text,

    created_at timestamptz default now(),
    updated_at timestamptz default now()
);


Trigger included.

🔹 funding_opportunities Table

Stores all funding programmes loaded by Funders.

❗ Includes AI-friendly JSONB for flexible matching.
create table funding_opportunities (
    id uuid primary key default gen_random_uuid(),
    funder_id uuid references users(id),

    title text not null,
    amount_range text,
    sector text,
    region text,
    requirements text,
    description text,

    -- AI flexible matching field
    ai_criteria jsonb default '{}'::jsonb,

    created_at timestamptz default now(),
    updated_at timestamptz default now()
);


Examples stored in ai_criteria:

{
  "min_amount": 50000,
  "max_amount": 300000,
  "required_sector": ["Agriculture", "ICT"],
  "min_years": 1,
  "region": "Eastern Cape"
}

🔹 applications Table

Stores submitted funding applications.

create table applications (
    id uuid primary key default gen_random_uuid(),
    smme_id uuid references users(id),
    funding_id uuid references funding_opportunities(id),

    requested_amount numeric,
    project_summary text,
    motivation_letter text,

    status text check (status in ('pending','approved','rejected'))
        default 'pending',

    created_at timestamptz default now(),
    updated_at timestamptz default now()
);


Trigger added.

🧠 4. AI Workflow (Using OpenAI or LangChain)
Step 1: SMME enters business + project details

AI extracts entities like: sector, region, revenue, years, project need…

Step 2: System fetches all funding opportunities from Supabase

AI creates a similarity score:

score = AI.compare(smme_profile, funding.ai_criteria)

Step 3: Sorting & Ranking

Top matches displayed first.

Step 4: Auto-fill application form

AI generates:

Project summary

Motivation letter

Explanation of match reasons

Estimated requested amount

Step 5: Funders view applications and update status

SMME sees updates instantly.

🎨 5. Frontend (HTML + CSS + JavaScript)
Main Screens

Login/Register

SMME Dashboard

Funder Dashboard

Funding Search

Application Form (AI-generated)

Status Tracking

Funder Review Panel

☁️ 6. Deployment

Supabase → Database + Auth + API

JS / HTML / CSS → Static hosting (Netlify / Vercel / Firebase)

OpenAI API → AI Matching + Auto-fill

🏁 7. Conclusion

This system is light, fast, and hackathon-friendly — but still powerful enough to demonstrate:

AI Matching

NLP

Intelligent Auto-Fill

Multi-user System

Real Database Structure

CRUD + Status Tracking
$$
