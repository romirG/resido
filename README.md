# ResiDo 🏠

**A full-stack property buy-sell platform for the Indian real estate market.**

ResiDo lets buyers browse verified property listings, schedule site visits, chat with an AI assistant, and explore homes through immersive 360° virtual tours — while owners get a dedicated dashboard to list, manage, and track their properties.

---

## Pages & Features

### Buyer Side
| Page | What it does |
|------|-------------|
| **Home** (`LuxuryHomePage`) | Hero with featured properties, discover carousel, stats, luxury project grid |
| **Browse Properties** (`LuxuryBrowseProperties`) | Grid / map view toggle, real-time search, filter panel (city, price, bedrooms, pet-friendly, bachelor-friendly), GSAP card animations |
| **Property Detail** (`LuxuryPropertyDetail`) | Full property info, image gallery, Leaflet map with street view modal, review section, schedule visit modal, wishlist toggle |
| **Virtual Tour** (`VirtualTour`) | Marzipano-powered 360° panorama viewer — seeded per property ID so rooms are consistent, keyboard & drag navigation, zoom controls |
| **Wishlist** (`WishlistPage`) | Saved properties with remove / view actions |
| **Messages** (`MessagesPage`) | Inbox for buyer-seller conversations |
| **Market Analytics** (`MarketAnalytics`) | City price trends (2020–2025), YoY growth, investment scores, city comparison (up to 3), forecast charts (2026–2027), buyer preference donuts — 100% frontend, no backend dependency |
| **EMI Calculator** (`EMICalculatorPage`) | Interactive loan calculator — PMAY, SBI, HDFC, ICICI, LIC schemes, Section 80C/24b/80EE/80EEA tax breakdown, affordability checker, joint loan support |
| **Property News** (`PropertyNews`) | Real estate news fetched from backend, auto-refreshed every 4 hours via cron |
| **About Us** (`AboutUs`) | Team page |

### Owner Side
| Page | What it does |
|------|-------------|
| **Owner Landing** (`OwnerLanding`) | Marketing page for property owners |
| **Owner Login** (`OwnerLogin`) | Email/password + Firebase auth |
| **Owner Dashboard** (`OwnerDashboard`) | View own listings, track inquiries, manage visits |
| **Add Property Wizard** (`AddPropertyWizard`) | Multi-step form: details → location → amenities → images (Cloudinary upload) |

### Shared
- **AI Chat Widget** (`ChatWidget`) — Groq LLM assistant on browse page; extracts search intent and returns matching property IDs from DB
- **Auth** — Dual auth: JWT (email/password) + Firebase (Google sign-in), session management, password reset flow

---

## Tech Stack

### Frontend
| Package | Purpose |
|---------|---------|
| React 18 + Vite | UI framework & build tool |
| Vanilla CSS | Custom dark/gold luxury theme (`luxury-theme.css`) |
| GSAP + ScrollTrigger | Card entrance animations on browse page |
| Marzipano | 360° panorama viewer for virtual tours |
| Leaflet.js + leaflet.markercluster | Interactive property maps |
| Mapillary JS | Street view imagery on property detail |
| Firebase | Google sign-in client SDK |

### Backend
| Package | Purpose |
|---------|---------|
| Express.js | REST API server |
| Sequelize + PostgreSQL | ORM & database (`pg`, `pg-hstore`) |
| Firebase Admin SDK | Server-side token verification |
| JWT + bcryptjs | Email/password auth |
| Helmet + express-rate-limit | Security headers & rate limiting |
| Multer + Cloudinary | Image uploads to CDN |
| Groq SDK | LLM for AI chat assistant |
| node-cron | Scheduled news fetch (every 4 hours) |
| express-validator | Input validation |

---

## Project Structure

```
resido/
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── LuxuryHomePage.jsx
│   │   │   ├── LuxuryBrowseProperties.jsx
│   │   │   ├── LuxuryPropertyDetail.jsx
│   │   │   ├── VirtualTour.jsx          # Marzipano 360° viewer
│   │   │   ├── MarketAnalytics.jsx      # Frontend-only analytics dashboard
│   │   │   ├── EMICalculatorPage.jsx    # Loan + tax calculator
│   │   │   ├── WishlistPage.jsx
│   │   │   ├── MessagesPage.jsx
│   │   │   ├── PropertyNews.jsx
│   │   │   ├── AboutUs.jsx
│   │   │   └── owner/
│   │   │       ├── OwnerLanding.jsx
│   │   │       ├── OwnerLogin.jsx
│   │   │       ├── OwnerDashboard.jsx
│   │   │       └── AddPropertyWizard.jsx
│   │   ├── components/
│   │   │   ├── PropertyMap.jsx          # Leaflet map with clustering
│   │   │   ├── ChatWidget.jsx           # AI chat floating widget
│   │   │   ├── ReviewSection.jsx
│   │   │   ├── ScheduleVisitModal.jsx
│   │   │   ├── StreetViewModal.jsx      # Mapillary street view
│   │   │   ├── TrustBadge.jsx
│   │   │   └── analytics/              # Chart components for Market Analytics
│   │   ├── services/
│   │   │   └── api.js                  # Axios service layer
│   │   ├── context/
│   │   │   └── AuthContext.jsx         # JWT + Firebase auth state
│   │   ├── data/
│   │   │   └── marketAnalyticsData.js  # Static analytics dataset
│   │   ├── styles/
│   │   │   └── luxury-theme.css        # CSS variables & global theme
│   │   └── utils/
│   │       └── analyticsUtils.js
│   ├── public/
│   │   └── panoramas/                  # 360° panorama images (27 rooms)
│   ├── .env.example
│   └── vercel.json
│
├── backend/
│   ├── routes/
│   │   ├── authEnhanced.js    # JWT + Firebase auth, sessions, password reset
│   │   ├── properties.js      # CRUD for listings
│   │   ├── inquiries.js       # Buyer-seller inquiries
│   │   ├── messages.js        # Direct messages
│   │   ├── reviews.js         # Property reviews + owner responses
│   │   ├── wishlist.js        # Save/remove properties
│   │   ├── visits.js          # Schedule & manage site visits
│   │   ├── chat.js            # Groq-powered AI chat
│   │   ├── upload.js          # Cloudinary image uploads
│   │   ├── prediction.js      # Price prediction endpoint
│   │   ├── fraud.js           # Fraud/spam detection
│   │   └── news.js            # Property news feed
│   ├── controllers/           # Business logic layer
│   ├── models/                # Sequelize models
│   ├── middleware/
│   │   └── auth.js            # JWT & Firebase token middleware
│   ├── services/
│   │   ├── groqService.js     # LLM intent extraction & response generation
│   │   └── newsService.js     # News fetching & caching
│   ├── config/
│   │   └── database.js        # Sequelize PostgreSQL config
│   ├── seeds/
│   │   └── seedDatabase.js    # DB seed script
│   ├── Dockerfile
│   ├── .env.example
│   └── server.js
│
└── database/
    └── schema.sql
```

---

## API Reference

### Auth — `POST /api/auth/*`
| Endpoint | Description |
|----------|-------------|
| `POST /register` | Register with email + password |
| `POST /login` | Login, returns JWT |
| `POST /firebase-sync` | Sync Firebase Google user with DB |
| `POST /firebase-register` | Register via Firebase UID |
| `POST /forgot-password` | Request password reset email |
| `POST /reset-password` | Reset with token |
| `POST /change-password` | Change password (auth required) |
| `POST /upgrade-to-owner` | Upgrade buyer account to owner |
| `GET /sessions` | Active sessions (auth required) |
| `POST /logout-all` | Invalidate all sessions |

### Properties — `/api/properties`
| Endpoint | Description |
|----------|-------------|
| `GET /` | List all (supports `city`, `min_price`, `max_price`, `property_type`, `listing_type`, `bedrooms`, `pet_friendly`, `bachelor_friendly` query params) |
| `GET /:id` | Single property |
| `POST /` | Create listing (owner auth) |
| `PUT /:id` | Update listing (owner auth) |
| `DELETE /:id` | Delete listing (owner auth) |

### Other Endpoints
| Endpoint | Description |
|----------|-------------|
| `GET /api/reviews/property/:id` | Get property reviews |
| `POST /api/reviews/property/:id` | Add review (auth) |
| `POST /api/reviews/:id/respond` | Owner responds to review |
| `POST /api/wishlist/:id` | Add to wishlist |
| `DELETE /api/wishlist/:id` | Remove from wishlist |
| `GET /api/wishlist/check/:id` | Check if wishlisted |
| `POST /api/visits` | Schedule visit (auth) |
| `GET /api/visits/owner` | Owner's incoming visits |
| `GET /api/visits/my-visits` | Buyer's own visits |
| `PATCH /api/visits/:id/status` | Confirm/decline visit |
| `POST /api/messages` | Send message |
| `GET /api/messages` | Get inbox |
| `POST /api/chat` | AI chat (Groq) |
| `GET /api/chat/history/:token` | Chat session history |
| `POST /api/upload` | Upload image to Cloudinary |
| `GET /api/news` | Get property news |
| `POST /api/predict-price` | Price prediction |

---

## Setup

### Prerequisites
- Node.js 18+
- PostgreSQL 15+
- Cloudinary account
- Firebase project (for Google auth)
- Groq API key (for AI chat)

### Installation

```bash
git clone https://github.com/romirG/resido.git
cd resido

# Frontend
cd frontend && npm install

# Backend
cd ../backend && npm install
```

### Environment Variables

**`backend/.env`** (see `backend/.env.example`):
```env
DB_HOST=localhost
DB_PORT=5432
DB_NAME=resido
DB_USER=your_db_user
DB_PASSWORD=your_db_password
JWT_SECRET=your_jwt_secret
CLOUDINARY_CLOUD_NAME=...
CLOUDINARY_API_KEY=...
CLOUDINARY_API_SECRET=...
GROQ_API_KEY=...
FRONTEND_URL=http://localhost:3000
PORT=5000
NODE_ENV=development
```

**`frontend/.env`** (see `frontend/.env.example`):
```env
VITE_API_URL=http://localhost:5000/api
```

### Running

```bash
# Terminal 1 — Backend (http://localhost:5000)
cd backend
npm run dev

# Terminal 2 — Frontend (http://localhost:3000)
cd frontend
npm run dev

# Seed the database (optional)
cd backend
npm run seed
```

### Docker (Backend only)

```bash
cd backend
docker build -t resido-backend .
docker run -p 5000:5000 --env-file .env resido-backend
```

---

## Deployment

| Service | Purpose |
|---------|---------|
| Vercel | Frontend (`vercel.json` already configured) |
| Render.com | Backend (Dockerfile included) |
| Render PostgreSQL | Managed database |
| Cloudinary | Image CDN |
