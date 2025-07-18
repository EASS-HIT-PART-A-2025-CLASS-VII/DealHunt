# DealHunt 🛒

[Watch the DealHunt demo on YouTube]
https://youtu.be/99P_Yjv_fFc

> A modern, full-stack e-commerce price comparison platform that helps you find the best deals across multiple marketplaces like AliExpress and eBay through intelligent search, wishlist management, and comprehensive product tracking.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![React](https://img.shields.io/badge/React-18.3.1-blue.svg)](https://reactjs.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115.5-green.svg)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python-3.12+-blue.svg)](https://www.python.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-7.0+-green.svg)](https://www.mongodb.com/)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)](https://www.docker.com/)

## Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Setup](#environment-setup)
  - [Running the Application](#running-the-application)
- [API Documentation](#api-documentation)
- [Usage Guide](#usage-guide)
- [Development](#development)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About the Project

DealHunt is a comprehensive price comparison platform that aggregates products from multiple e-commerce marketplaces including AliExpress and eBay. Built with modern web technologies, it offers an intuitive interface for discovering deals, managing wishlists, and tracking product prices across different platforms.

### Architecture Overview

```
┌─────────────────┐     ┌─────────────────┐    ┌─────────────────┐
│   React Frontend│◄──► │  FastAPI Backend│◄──►│   MongoDB Local │
│   (JavaScript)  │     │    (Python)     │    │   (Database)    │
└─────────────────┘     └─────────────────┘    └─────────────────┘
         │                       │                       │
         │              ┌─────────────────┐              │
         └─────────────►│ AliExpress API  │◄─────────────┘
                        │    eBay API     │
                        └─────────────────┘
```

**Key Design Principles:**

- **Microservices Architecture**: Separate frontend, backend, and database services
- **Real-time Data**: Live product data from multiple marketplace APIs
- **Price Comparison**: Intelligent aggregation and comparison across platforms
- **Responsive Design**: Mobile-first approach with modern UI/UX
- **Secure Authentication**: JWT tokens with Google OAuth2 integration

## Features

### 🎯 Core Features

- **Multi-Platform Search** - Find products across AliExpress, eBay, and more
- **Price Comparison** - Compare prices and find the best deals
- **Advanced Filtering** - Filter by marketplace, price range, condition, and more
- **User Wishlist Management** - Save and track favorite products
- **Product Details** - Comprehensive product information with images and specifications
- **Real-time Updates** - Live price tracking and availability status

### 🔐 Authentication & Security

- **JWT Authentication** - Secure token-based authentication
- **Google OAuth2** - Sign in with Google integration
- **Email Verification** - Account verification and password reset
- **Protected Routes** - Secure access to user-specific features

### 🎨 User Experience

- **Responsive Design** - Works seamlessly on desktop and mobile
- **Modern UI** - Clean interface with smooth animations
- **Loading States** - Skeleton loading and comprehensive error handling
- **Toast Notifications** - Real-time feedback for user actions
- **Image Magnification** - Detailed product image viewing

### 🛠️ Developer Features

- **Docker Containerization** - Easy deployment and development setup
- **API Documentation** - Auto-generated FastAPI/OpenAPI docs
- **Error Handling** - Comprehensive error management across the stack
- **Code Organization** - Clean architecture with separation of concerns

## Tech Stack

### Frontend

- **React 18.3.1** - Modern React with Hooks and Context
- **Vite 5.4.10** - Fast build tool and dev server
- **Tailwind CSS 3.4.14** - Utility-first CSS framework
- **React Router 6.28.0** - Client-side routing
- **Axios** - HTTP client for API requests

### Backend

- **FastAPI 0.115.5** - Modern Python web framework
- **Python 3.12+** - Latest Python features
- **Pydantic 2.10.3** - Data validation and settings management
- **PyJWT 2.10.1** - JSON Web Token implementation
- **Passlib 1.7.4** - Password hashing utilities
- **Motor** - Async MongoDB driver

### Database & External Services

- **MongoDB 7.0** - Document database for user and product data
- **AliExpress API** - Product data from AliExpress marketplace
- **eBay API** - Product data from eBay marketplace
- **Gmail SMTP** - Email service for notifications

### DevOps & Tools

- **Docker & Docker Compose** - Containerization and orchestration
- **Nginx** - Reverse proxy and static file serving
- **Uvicorn** - ASGI server for FastAPI

## Project Structure

```
DealHunt/
├── backend/
│   ├── app/
│   │   ├── routers/
│   │   │   ├── auth.py
│   │   │   ├── products.py
│   │   │   └── users.py
│   │   ├── models/
│   │   │   ├── user.py
│   │   │   └── product.py
│   │   ├── services/
│   │   │   ├── auth_service.py
│   │   │   ├── product_service.py
│   │   │   └── email_service.py
│   │   ├── config.py
│   │   ├── database.py
│   │   └── main.py
│   ├── Dockerfile
│   └── requirements.txt
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── auth/
│   │   │   ├── common/
│   │   │   ├── product/
│   │   │   └── layout/
│   │   ├── contexts/
│   │   │   ├── AuthContext.js
│   │   │   └── WishlistContext.js
│   │   ├── pages/
│   │   │   ├── HomePage.jsx
│   │   │   ├── SearchResultsPage.jsx
│   │   │   ├── ProductDetailPage.jsx
│   │   │   ├── LoginPage.jsx
│   │   │   ├── RegisterPage.jsx
│   │   │   ├── ProfilePage.jsx
│   │   │   ├── WishlistPage.jsx
│   │   │   ├── TermsPage.jsx
│   │   │   └── PrivacyPolicyPage.jsx
│   │   ├── utils/
│   │   ├── api/
│   │   └── hooks/
│   ├── Dockerfile
│   ├── nginx.conf
│   └── package.json
├── docker-compose.yml
├── DEPLOYMENT_GUIDE.md
└── README.md
```

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Docker** (20.10+) and **Docker Compose** (2.0+)
- **Git** for cloning the repository
- **AliExpress API Credentials** - Get from AliExpress Partner Platform
- **eBay API Credentials** - Get from eBay Developer Program
- **Google OAuth Credentials** - Set up at [Google Cloud Console](https://console.cloud.google.com/)
- **Gmail App Password** - For email notifications (optional)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/EASS-HIT-PART-A-2025-CLASS-VII/DealHunt.git
   cd DealHunt
   ```

2. **Create environment files**

   ```bash
   # Create backend environment file
   touch backend/.env
   ```

### Environment Setup

#### Backend Environment (`backend/.env`)

```bash
# ── AliExpress credentials ────────────────────────────────────────────────
APP_KEY=your_aliexpress_app_key
APP_SECRET=your_aliexpress_app_secret
TRACKING_ID=your_tracking_id

# ── eBay credentials ────────────────────────────────────────────────
EBAY_TOKEN=your_ebay_access_token
EBAY_CAMPAIGN_ID=your_campaign_id
EBAY_CLIENT_ID=your_ebay_client_id
EBAY_CLIENT_SECRET=your_ebay_client_secret
EBAY_REFRESH_TOKEN=your_ebay_refresh_token

# ── MongoDB credentials ────────────────────────────────────────────────
MONGODB_URI=mongodb://admin:password123@mongodb:27017/dealhunt?authSource=admin

# ── JWT settings ──────────────────────────────────────────────
SECRET_KEY=your_super_secure_secret_key_for_jwt_tokens

# ── Google OAuth credentials ────────────────────────────────────────────────
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

# ── Email configuration for password reset ────────────────────────────────────────────────
MAIL_USERNAME=your_email@gmail.com
MAIL_PASSWORD=your_gmail_app_password
MAIL_FROM=your_email@gmail.com
FRONTEND_URL=http://localhost:3000
```

#### Environment Variables Guide

| Variable               | Required    | Description                | How to Obtain                                                            |
| ---------------------- | ----------- | -------------------------- | ------------------------------------------------------------------------ |
| `APP_KEY`              | ✅ Yes      | AliExpress API key         | [AliExpress Partner Platform](https://portals.aliexpress.com/)           |
| `APP_SECRET`           | ✅ Yes      | AliExpress API secret      | [AliExpress Partner Platform](https://portals.aliexpress.com/)           |
| `EBAY_CLIENT_ID`       | ✅ Yes      | eBay API client ID         | [eBay Developer Program](https://developer.ebay.com/)                    |
| `EBAY_CLIENT_SECRET`   | ✅ Yes      | eBay API client secret     | [eBay Developer Program](https://developer.ebay.com/)                    |
| `SECRET_KEY`           | ✅ Yes      | JWT signing secret         | Generate: `openssl rand -hex 32`                                         |
| `GOOGLE_CLIENT_ID`     | ⚠️ OAuth    | Google OAuth client ID     | [Google Cloud Console](https://console.cloud.google.com/)                |
| `GOOGLE_CLIENT_SECRET` | ⚠️ OAuth    | Google OAuth client secret | [Google Cloud Console](https://console.cloud.google.com/)                |
| `MAIL_PASSWORD`        | 🔧 Optional | Gmail app password         | [Gmail App Passwords](https://support.google.com/accounts/answer/185833) |

## Running the Application

### **1. Start all services**

```bash
docker-compose up --build
```

### **2. Access the application**

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8000
- **API Documentation**: http://localhost:8000/docs
- **MongoDB**: localhost:27017

The application will automatically:

- Build and start the React frontend on port 3000
- Launch the FastAPI backend on port 8000
- Initialize MongoDB container with authentication
- Configure all necessary services and dependencies

### **3. Create required directories**

```bash
# Create data directories for MongoDB persistence
mkdir -p data/db data/configdb
```

## API Documentation

### **Authentication Endpoints**

| Method | Endpoint                | Description               | Auth Required |
| ------ | ----------------------- | ------------------------- | ------------- |
| `POST` | `/auth/register`        | Create new user account   | ❌            |
| `POST` | `/auth/login`           | Login with credentials    | ❌            |
| `GET`  | `/auth/google/login`    | Initiate Google OAuth     | ❌            |
| `GET`  | `/auth/google/callback` | Google OAuth callback     | ❌            |
| `POST` | `/auth/forgot-password` | Request password reset    | ❌            |
| `POST` | `/auth/reset-password`  | Reset password with token | ❌            |
| `GET`  | `/auth/verify-email`    | Verify email address      | ❌            |
| `POST` | `/auth/refresh`         | Refresh access token      | ❌            |

### **Product Search & Discovery**

| Method | Endpoint                    | Description              | Auth Required |
| ------ | --------------------------- | ------------------------ | ------------- |
| `GET`  | `/products/search`          | Search products          | ❌            |
| `GET`  | `/products/featured`        | Get featured products    | ❌            |
| `GET`  | `/products/{id}`            | Get product details      | ❌            |
| `GET`  | `/products/recommendations` | Get recommended products | ❌            |
| `GET`  | `/products/categories`      | Get product categories   | ❌            |

### **User Management**

| Method   | Endpoint                    | Description          | Auth Required |
| -------- | --------------------------- | -------------------- | ------------- |
| `GET`    | `/users/profile`            | Get user profile     | ✅            |
| `PUT`    | `/users/profile`            | Update user profile  | ✅            |
| `GET`    | `/users/wishlist`           | Get user wishlist    | ✅            |
| `POST`   | `/users/wishlist`           | Add to wishlist      | ✅            |
| `DELETE` | `/users/wishlist/{item_id}` | Remove from wishlist | ✅            |

### Example API Usage

```bash
# Search for products
curl "http://localhost:8000/products/search?q=smartphone&marketplace=aliexpress&page=1"

# Get product details
curl "http://localhost:8000/products/12345?marketplace=ebay"

# Login (get access token)
curl -X POST "http://localhost:8000/auth/login" \
  -H "Content-Type: application/json" \
  -d '{"email":"user@example.com","password":"yourpassword"}'

# Get user profile (authenticated)
curl "http://localhost:8000/users/profile" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"

# Add product to wishlist
curl -X POST "http://localhost:8000/users/wishlist" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"product_id":"12345","marketplace":"aliexpress"}'
```

## Usage Guide

### 1. User Registration & Authentication

1. **Sign Up**: Create an account with email and password
2. **Email Verification**: Check your email and click the verification link
3. **Login**: Access your account with credentials or Google OAuth

### 2. Discovering Products

- **Search**: Find products across multiple marketplaces
- **Filter**: Use advanced filters for price, marketplace, condition, and shipping
- **Categories**: Browse by product categories
- **Featured Deals**: Explore trending and featured products

### 3. Managing Your Wishlist

- **Add to Wishlist**: Save products for later purchase
- **Price Tracking**: Monitor price changes on saved items
- **Remove Items**: Manage your wishlist by removing unwanted products
- **Compare Prices**: View price differences across marketplaces

### 4. Product Details

- **Product Information**: View detailed specifications and descriptions
- **Price Comparison**: See prices across different marketplaces
- **Seller Information**: Check seller ratings and shipping details
- **Product Images**: Browse through product photos with magnification
- **Reviews**: Read customer reviews and ratings

### 5. User Profile Management

- **Profile Settings**: Update personal information and preferences
- **Password Management**: Change password and security settings
- **Wishlist History**: View and manage saved products
- **Order History**: Track your activity and preferences

## Development

### Local Development Setup

1. **Frontend Development**

   ```bash
   cd frontend
   npm install
   npm run dev
   ```

2. **Backend Development**

   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
   ```

3. **Database Setup (Local MongoDB)**
   ```bash
   docker run -d --name mongodb -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password123 mongo:7.0
   ```

## Deployment

### Docker Deployment (Recommended)

The project includes comprehensive Docker configuration for easy deployment:

1. **Production Build**

   ```bash
   docker-compose -f docker-compose.prod.yml up --build -d
   ```

2. **Environment Configuration**
   - Update environment variables for production
   - Configure SSL certificates
   - Set up domain routing

### Manual Deployment

For manual deployment, refer to the detailed [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) included in the repository.

## Contributing

We welcome contributions! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Commit changes**: `git commit -m 'Add amazing feature'`
4. **Push to branch**: `git push origin feature/amazing-feature`
5. **Open a Pull Request**

### Development Guidelines

- Follow existing code style and conventions
- Write meaningful commit messages
- Add documentation for new features
- Ensure all functionality works before submitting PR
- Test across different marketplaces and scenarios

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

**Project Team**: EASS HIT Class VII

- GitHub: [EASS-HIT-PART-A-2025-CLASS-VII](https://github.com/EASS-HIT-PART-A-2025-CLASS-VII)
- Project Link: [https://github.com/EASS-HIT-PART-A-2025-CLASS-VII/DealHunt](https://github.com/EASS-HIT-PART-A-2025-CLASS-VII/DealHunt)

---

**Built with ❤️ using React, FastAPI, and MongoDB**

_DealHunt - Your gateway to the best deals across the internet_
