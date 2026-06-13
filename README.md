# ResiDo 🏠

**Property Buy-Sell & Owner Management Platform**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-brightgreen)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18-blue)](https://reactjs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue)](https://postgresql.org/)

A modern property marketplace for buying and selling homes directly from verified owners. Built with a sleek neon green & black UI featuring interactive maps, advanced filtering, and a floating 3D mascot.

> 🚀 **Live Demo:** _Coming Soon_ | 📖 **[API Docs](#-api-endpoints)**

---

## ✨ Features

- **Property Listings** — Browse flats, homes, villas, plots, and commercial properties
- **Owner Dashboard** — Manage listings with analytics and inquiry tracking
- **Verified Badges** — Trust system for verified owners & brokers
- **Advanced Filters** — Search by location, price, property type, amenities, and lifestyle preferences
- **Interactive Maps** — Property locations powered by Leaflet.js + OpenStreetMap
- **Contact System** — Direct messaging between buyers and sellers
- **Market Analytics** — Price trends, neighbourhood insights, and investment data
- **3D Mascot** — Floating Spline-powered mascot companion
- **Responsive Design** — Mobile-first approach

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|------------|---------|
| React 18 + Vite | UI framework & build tool |
| Vanilla CSS | Custom neon green/black theme |
| Spline | 3D mascot |
| Leaflet.js | Interactive maps |

### Backend
| Technology | Purpose |
|------------|---------|
| Node.js + Express.js | REST API server |
| PostgreSQL + Sequelize ORM | Database & ORM |
| JWT | Authentication |
| Multer | File uploads |
| Cloudinary | Image CDN |

### Deployment
| Service | Purpose |
|---------|---------|
| Vercel | Frontend hosting |
| Render.com | Backend hosting |
| Render PostgreSQL | Managed database |

---

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- PostgreSQL 15+
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/romirG/resido.git
cd resido

# Install frontend dependencies
cd frontend
npm install

# Install backend dependencies
cd ../backend
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your credentials (see Environment Variables section below)
```

### Running Development Servers

```bash
# Terminal 1 — Frontend (http://localhost:3000)
cd frontend
npm run dev

# Terminal 2 — Backend (http://localhost:5000)
cd backend
npm run dev
```

---

## ⚙️ Environment Variables

### Backend (`backend/.env`)

```env
# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=resido
DB_USER=your_db_user
DB_PASSWORD=your_db_password

# Auth
JWT_SECRET=your_super_secret_key

# Cloudinary (image uploads)
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Server
PORT=5000
NODE_ENV=development
```

### Frontend (`frontend/.env`)

```env
VITE_API_URL=http://localhost:5000
```

See `backend/.env.example` and `frontend/.env.example` for the full list.

---

## 📁 Project Structure

```
resido/
├── frontend/               # React + Vite app
│   ├── public/            # Static assets (logo, hero images)
│   ├── src/
│   │   ├── components/    # Reusable React components
│   │   ├── pages/         # Page components
│   │   ├── services/      # API service layer
│   │   ├── App.jsx        # Main app component
│   │   └── index.css      # Global styles (neon theme)
│   ├── vercel.json        # Vercel deployment config
│   └── package.json
│
├── backend/                # Node.js + Express API
│   ├── routes/            # API route handlers
│   ├── controllers/       # Business logic
│   ├── models/            # Sequelize models
│   ├── middleware/        # Auth & validation middleware
│   ├── config/            # Database config
│   ├── seeds/             # Database seed data
│   ├── Dockerfile         # Container config
│   └── server.js          # Entry point
│
├── database/               # SQL schemas
│   └── schema.sql
│
└── README.md
```

---

## 📊 Database Schema

Key tables:
- `users` — Buyers, owners, brokers
- `properties` — Listings with geo-coordinates
- `images` — Property photos (Cloudinary URLs)
- `reviews` — User ratings & comments
- `inquiries` — Buyer-seller messages
- `wishlist` — Saved properties

See [`database/schema.sql`](database/schema.sql) for the full schema.

---

## 🔗 API Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| `POST` | `/api/auth/register` | User signup | — |
| `POST` | `/api/auth/login` | User login | — |
| `GET` | `/api/properties` | List properties (with filters) | — |
| `GET` | `/api/properties/:id` | Get single property | — |
| `POST` | `/api/properties` | Create listing | ✅ Owner |
| `PUT` | `/api/properties/:id` | Update listing | ✅ Owner |
| `DELETE` | `/api/properties/:id` | Delete listing | ✅ Owner |
| `POST` | `/api/inquiries` | Send inquiry | ✅ User |
| `GET` | `/api/users/:id/listings` | Owner's properties | ✅ Owner |

---

## 🐳 Docker (Backend)

```bash
cd backend
docker build -t resido-backend .
docker run -p 5000:5000 --env-file .env resido-backend
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👥 Team

Built with 💚 for property seekers everywhere.

---

*Last Updated: June 2026*
