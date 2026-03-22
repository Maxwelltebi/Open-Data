# Open Data Platform

An open data platform designed for researchers, NGOs, governments, and startups to access and share data.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React.js |
| Backend | Express.js / Node.js |
| Database | MongoDB |
| Search | Elasticsearch |
| Storage | Cloudinary |
| Auth | Email/password with verification, hashing, encryption |

## Architecture

Three-tier, microservices-style:
- **Client** → React.js frontend
- **API** → Express.js / Node.js backend
- **Data** → MongoDB + Elasticsearch + Cloudinary

## Features

> This section is updated as each feature is built.

### Authentication
- [ ] Sign up
- [ ] Sign in
- [ ] Email verification
- [ ] Password hashing & encryption

### User
- [ ] User profile
- [ ] Profile image upload (Cloudinary)
- [ ] Account management

### Data
- [ ] Dataset upload
- [ ] Dataset listing
- [ ] Dataset search (Elasticsearch)
- [ ] Dataset detail view

### Access & Roles
- [ ] Role-based access (researcher, NGO, govt, startup)
- [ ] Public / private dataset visibility

## Dataset Categories

### From Research Document
| Category | Subcategories |
|----------|--------------|
| **Healthcare** | Disease surveillance, Hospital infrastructure, Medical research |
| **Agriculture** | Crop yields, Food security, Climate data |
| **Economics** | GDP, Trade, Inflation, Labor markets |
| **Education** | School performance, Literacy rates, University data |
| **Climate** | Weather, Environmental monitoring, Satellite imagery |
| **Transport** | Traffic patterns, Infrastructure data |
| **Finance** | Banking access, Remittances, Microfinance, Currency data |

### Additional Relevant Categories
| Category | Subcategories |
|----------|--------------|
| **Governance & Politics** | Election data, Policy documents, Public spending, Corruption indices |
| **Demographics & Population** | Census data, Migration, Urbanization, Birth/death rates |
| **Energy** | Power grid coverage, Renewable energy, Electrification rates, Oil & gas |
| **Water & Sanitation** | Access to clean water, Sanitation infrastructure, Drought data, Flood zones |
| **Land & Natural Resources** | Land use, Mining, Deforestation, Soil data, Mineral reserves |
| **Conflict & Security** | Conflict zones, Displacement, Peacekeeping, Refugee data |
| **Technology & Connectivity** | Internet penetration, Mobile usage, Digital infrastructure, Fintech |
| **Trade & Logistics** | Cross-border trade, Port activity, Supply chains, Import/export data |
| **Public Health** | Vaccination rates, Maternal health, Malnutrition, Disease outbreaks |
| **Biodiversity & Wildlife** | Species tracking, Conservation areas, Poaching, Marine ecosystems |
| **Housing & Urban Development** | Housing prices, Slum data, City planning, Infrastructure gaps |
| **Gender & Social Inclusion** | Gender equality indices, Women in leadership, Child labour, Disability data |
| **Labour & Employment** | Unemployment rates, Informal economy, Wage data, Skills gaps |
| **Justice & Human Rights** | Court data, Prison statistics, Human rights violations, Legal access |
| **Media & Communication** | Press freedom, Broadcast data, Language distribution, Telecommunications |
| **Tourism & Culture** | Visitor statistics, Heritage sites, Cultural events, Arts economy |
| **Science & Research** | Academic publications, R&D spending, Patent filings, Innovation indices |
| **Food & Nutrition** | Hunger indices, Food prices, Supply chains, Dietary data |
| **Disaster & Risk** | Natural disaster records, Emergency response, Climate risk maps |
| **Sports & Youth** | Youth population data, Sports infrastructure, Athletic performance |

---

## Major Components

### 1. Users & Organizations
- **Users** — data scientists, researchers, students, journalists, AI startups, admins
- **Organizations** — universities, government agencies, NGOs, tech companies

### 2. Dataset System
- **Datasets** — the central entity of the platform
- **Dataset Files** — multiple files per dataset (CSV, JSON, Parquet, GeoJSON, images, satellite data)
- **Dataset Metadata** — source, geographic scope, temporal coverage, data dictionary
- **Dataset Versions** — versioned history with change logs
- **Dataset Tags** — health, agriculture, climate, economics, finance, education, transport

### 3. Engagement & Discovery
- **Dataset Reviews** — ratings + comments by users
- **Dataset Likes** — user engagement tracking
- **Dataset Downloads** — download tracking per user/country
- **Search System** — Elasticsearch indexing by title, tags, country, domain, organization

### 4. Community
- **Discussions** — forum threads per dataset
- **Comments** — threaded replies within discussions

### 6. Data Infrastructure
- **Dataset Ingestion Pipeline** — upload → validate → extract metadata → quality score → store → index
- **Dataset Quality Engine** — scores completeness, documentation, format, freshness
- **Storage** — Cloudinary
- **API Keys** — per-user API access with rate limiting

### 7. Governance & Moderation
- **Moderation System** — submitted → under review → approved/rejected
- **Data Governance** — ownership, licensing, ethical use compliance

### 8. Analytics
- **Platform Analytics** — downloads, popular datasets, country trends, user activity

---

## Component Relationships

```
Users ──────────────── uploads ──────────────▶ Datasets
Users ──────────────── belongs to ───────────▶ Organizations
Users ──────────────── writes ────────────────▶ Reviews → Datasets
Users ──────────────── likes ─────────────────▶ Datasets
Users ──────────────── downloads ─────────────▶ Datasets (logged in Dataset_Downloads)
Users ──────────────── starts ────────────────▶ Discussions → Datasets
Users ──────────────── posts ─────────────────▶ Comments → Discussions
Users ──────────────── has ───────────────────▶ API_Keys

Datasets ───────────── has many ──────────────▶ Dataset_Files
Datasets ───────────── has ───────────────────▶ Dataset_Metadata
Datasets ───────────── has many ──────────────▶ Dataset_Versions
Datasets ───────────── tagged with ───────────▶ Dataset_Tags
Datasets ───────────── goes through ──────────▶ Moderation → approved/rejected
Datasets ───────────── indexed in ────────────▶ Elasticsearch (Search System)
Datasets ───────────── stored in ─────────────▶ Cloudinary (Storage)
Organizations ────────── owns ────────────────▶ Datasets

API_Keys ─────────────── grants access to ────▶ Dataset APIs → Datasets

Ingestion Pipeline ───── feeds ───────────────▶ Quality Engine → Storage → Search Index
```

---

## Project Files

| File | Description |
|------|-------------|
| `Flow Chart.jpeg` | System architecture diagram |
| `Research Document.docx` | Project research and requirements |
