# 🏡 ResiDo - Modern Property Discovery & Management Platform

> **A comprehensive real estate platform combining property discovery, virtual tours, and owner management**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![React](https://img.shields.io/badge/React-18.3.1-61DAFB?logo=react)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-336791?logo=postgresql)](https://www.postgresql.org/)

---

## 📖 Overview

**ResiDo** is a cutting-edge property management and discovery platform that revolutionizes how buyers, sellers, and property owners interact with real estate. Built with modern web technologies, ResiDo provides an immersive, transparent, and efficient property browsing experience.

### 🎯 Key Features

- **🌐 Virtual Tours & 360° Views** - Explore properties with immersive Mapillary street-level imagery
- **🗺️ Interactive Map Integration** - Browse properties on an intuitive map with clustering and filters
- **🔍 Advanced Search & Filtering** - Find your perfect property with powerful search capabilities
- **🔐 Secure Authentication** - JWT-based authentication with Firebase integration
- **📊 Owner Dashboard** - Comprehensive property management for owners and brokers
- **⭐ Reviews & Ratings** - Community-driven property reviews and ratings
- **💰 Smart Price Analytics** - Price comparisons and market insights
- **💬 Real-Time Messaging** - Direct communication between buyers and sellers
- **❤️ Wishlist System** - Save and track your favorite properties
- **📱 Mobile-First Design** - Fully responsive across all devices
- **🏦 EMI Calculator** - Built-in loan calculator for buyers
- **📰 Property News** - Stay updated with latest real estate trends

---

## 🚀 Tech Stack

### Frontend
- **React 18.3.1** - Modern component-based UI framework
- **Vite** - Lightning-fast build tool and dev server
- **GSAP** - Professional-grade animations
- **Leaflet & Leaflet.markercluster** - Interactive mapping
- **Mapillary-js** - Street-level imagery and virtual tours
- **Marzipano** - 360° panoramic viewer
- **Firebase** - Authentication and real-time features

### Backend
- **Node.js & Express** - RESTful API server
- **PostgreSQL** - Robust relational database
- **Sequelize** - Modern ORM for database operations
- **JWT** - Secure token-based authentication
- **bcryptjs** - Password hashing
- **Multer** - File upload handling
- **Cloudinary** - Cloud-based image storage
- **Helmet** - Security middleware
- **Express Rate Limit** - API rate limiting
- **GROQ SDK** - AI-powered features

### DevOps & Tools
- **Docker** - Containerization
- **Node-cron** - Scheduled tasks
- **Nodemon** - Development hot-reload
- **ESLint** - Code quality and consistency

---

## 🛠️ Installation

### Prerequisites

- **Node.js** (v16 or higher)
- **PostgreSQL** (v12 or higher)
- **npm** or **yarn**
- **Git**

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/romirG/resido.git
   cd resido
   ```

2. **Backend Setup**
   ```bash
   cd backend
   npm install
   
   # Create .env file with the following variables:
   cp .env.example .env
   # Edit .env with your configuration
   ```

   **Required Environment Variables:**
   ```env
   DB_HOST=localhost
   DB_USER=postgres
   DB_PASSWORD=your_password
   DB_NAME=resido
   DB_PORT=5432
   JWT_SECRET=your_jwt_secret
   FRONTEND_URL=http://localhost:5173
   CLOUDINARY_CLOUD_NAME=your_cloud_name
   CLOUDINARY_API_KEY=your_api_key
   CLOUDINARY_API_SECRET=your_api_secret
   ```

3. **Database Setup**
   ```bash
   # Create PostgreSQL database
   createdb resido
   
   # Run migrations (if available)
   npm run migrate
   
   # Seed sample data (optional)
   npm run seed
   ```

4. **Frontend Setup**
   ```bash
   cd ../frontend
   npm install
   
   # Create .env.local file
   cp .env.example .env.local
   # Configure with your API endpoints
   ```

   **Frontend Environment Variables:**
   ```env
   VITE_API_BASE_URL=http://localhost:3000
   VITE_FIREBASE_API_KEY=your_firebase_key
   VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
   VITE_FIREBASE_PROJECT_ID=your_project_id
   ```

5. **Start Development Servers**
   ```bash
   # Terminal 1 - Backend
   cd backend
   npm run dev
   
   # Terminal 2 - Frontend
   cd frontend
   npm run dev
   ```

6. **Access the Application**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:3000

---

## 📁 Project Structure

```
resido/
├── backend/                      # Node.js/Express Backend
│   ├── config/                   # Configuration files
│   │   └── database.js          # PostgreSQL connection
│   ├── controllers/              # Request handlers
│   ├── middleware/               # Express middleware
│   │   └── auth.js              # JWT authentication
│   ├── models/                   # Sequelize models
│   ├── routes/                   # API routes
│   ├── scripts/                  # Utility scripts
│   ├── seeds/                    # Database seeders
│   ├── services/                 # Business logic
│   ├── server.js                # Entry point
│   └── package.json
│
├── frontend/                     # React Frontend
│   ├── public/                   # Static assets
│   ├── src/
│   │   ├── components/          # Reusable components
│   │   ├── config/              # Frontend configuration
│   │   ├── context/             # React context providers
│   │   ├── data/                # Static data
│   │   ├── pages/               # Page components
│   │   │   ├── owner/          # Owner-specific pages
│   │   │   ├── LuxuryHomePage.jsx
│   │   │   ├── LuxuryBrowseProperties.jsx
│   │   │   ├── LuxuryPropertyDetail.jsx
│   │   │   ├── VirtualTour.jsx
│   │   │   ├── AboutUs.jsx
│   │   │   ├── WishlistPage.jsx
│   │   │   └── MessagesPage.jsx
│   │   ├── services/            # API service layer
│   │   ├── styles/              # Global styles
│   │   ├── utils/               # Helper functions
│   │   ├── App.jsx              # Main app component
│   │   └── main.jsx             # Entry point
│   ├── index.html
│   ├── vite.config.js
│   └── package.json
│
├── database/                     # Database schemas
├── docs/                         # Documentation
├── dev_images/                   # Development images
├── Property_Description_Images/ # Property assets
└── README.md
```

---

## 🔌 API Endpoints

### Authentication
```
POST   /api/auth/register          - User registration
POST   /api/auth/login             - User login
POST   /api/auth/logout            - User logout
GET    /api/auth/me                - Get current user
```

### Properties
```
GET    /api/properties             - Get all properties (with filters)
GET    /api/properties/:id         - Get single property
POST   /api/properties             - Create property (owner only)
PUT    /api/properties/:id         - Update property (owner only)
DELETE /api/properties/:id         - Delete property (owner only)
```

### Users
```
GET    /api/users/:id              - Get user profile
PUT    /api/users/:id              - Update user profile
GET    /api/users/:id/properties   - Get user's properties
```

### Wishlist
```
GET    /api/wishlist               - Get user wishlist
POST   /api/wishlist               - Add to wishlist
DELETE /api/wishlist/:id           - Remove from wishlist
```

### Messages
```
GET    /api/messages               - Get user messages
POST   /api/messages               - Send message
PUT    /api/messages/:id           - Update message status
```

---

## 💡 Usage Guide

### For Property Buyers

1. **Browse Properties** - Explore listings with advanced filters
2. **Virtual Tours** - Take immersive 360° tours of properties
3. **Save Favorites** - Add properties to your wishlist
4. **Contact Sellers** - Send inquiries directly to property owners
5. **Calculate EMI** - Use the built-in loan calculator

### For Property Owners

1. **Create Account** - Sign up as a property owner
2. **List Properties** - Add your properties with photos and details
3. **Manage Listings** - Update, edit, or remove properties
4. **Track Analytics** - View property views and inquiries
5. **Respond to Buyers** - Communicate with interested buyers

---

## 🎨 Features in Detail

### Virtual Tours & 360° Views
Experience properties as if you're physically present with Mapillary integration and panoramic imagery. Users can virtually "walk through" properties, examining every corner before scheduling physical visits.

### Interactive Map Integration
Browse properties on an intuitive Leaflet-powered map with marker clustering, real-time filters, and neighborhood information. See exactly where properties are located relative to amenities and landmarks.

### Advanced Search & Filtering
Find properties that match your exact criteria with filters for:
- Location (city, neighborhood, landmark proximity)
- Price range and budget
- Property type (flat, villa, apartment, commercial)
- Size and layout (bedrooms, bathrooms, square footage)
- Amenities and features
- Availability status

### Owner Dashboard
Comprehensive property management interface for owners including:
- Property listing management (CRUD operations)
- Analytics and insights (views, inquiries, engagement)
- Inquiry management and messaging
- Price comparison with market trends
- Property status tracking

### Smart Price Analytics
Get market insights with:
- Price comparison with similar properties
- Neighborhood price trends
- Historical price data
- Market demand indicators

---

## 👥 Team

**ResiDo** is developed by passionate students from IIIT Bangalore:

| Name | Role | Email | Contact |
|------|------|-------|---------|
| **Ridwan Umar** | Developer | ridwan.umar@iiitb.ac.in | +91 8882451901 |
| **Kshiteej Tiwari** | Developer | kshiteej.tiwari@iiitb.ac.in | +91 7030333308 |
| **Srijan Gupta** | Developer | srijan.gupta@iiitb.ac.in | +91 9179646803 |

### Institution
**International Institute of Information Technology Bangalore (IIIT-B)**  
26/C, Opposite Infosys Gate 10  
Electronics City Phase 1, Hosur Road  
Bengaluru - 560100  
Karnataka, India

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow the existing code style
- Write meaningful commit messages
- Add tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting PR

---

## 🔒 Security

- JWT-based authentication
- Password hashing with bcryptjs
- Helmet.js for HTTP security headers
- CORS protection
- Rate limiting on API endpoints
- Input validation and sanitization
- SQL injection prevention via Sequelize ORM

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Mapillary** - For street-level imagery API
- **OpenStreetMap** - For mapping data
- **Unsplash** - For sample property images
- **Firebase** - For authentication services
- **Cloudinary** - For image hosting and optimization

---

## 📞 Support

For support, email any of the team members or open an issue in the repository.

---

## 🗺️ Roadmap

- [ ] Mobile application (React Native)
- [ ] AI-powered property recommendations
- [ ] Virtual staging for empty properties
- [ ] Augmented reality property visualization
- [ ] Blockchain-based property verification
- [ ] Multi-language support
- [ ] Payment gateway integration
- [ ] Advanced analytics dashboard
- [ ] Property comparison tool
- [ ] Mortgage calculator with bank integration

---

**Made with ❤️ by the ResiDo Team at IIIT Bangalore**