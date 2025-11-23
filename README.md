# 🎯 Dev-Events

> **The Hub For Every Dev Event You Can't Miss**

A modern, full-stack event management platform built with Next.js 16, designed specifically for developers to discover, explore, and book tech events including hackathons, meetups, and conferences.

![Next.js](https://img.shields.io/badge/Next.js-16.0-black?style=for-the-badge&logo=next.js)
![React](https://img.shields.io/badge/React-19.2-blue?style=for-the-badge&logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-green?style=for-the-badge&logo=mongodb)
![TailwindCSS](https://img.shields.io/badge/Tailwind-CSS-38B2AC?style=for-the-badge&logo=tailwind-css)

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Environment Variables](#-environment-variables)
- [Running the Application](#-running-the-application)
- [Project Structure](#-project-structure)
- [API Routes](#-api-routes)
- [Database Models](#-database-models)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [License](#-license)

---

## ✨ Features

### Core Functionality
- 🎪 **Event Discovery** - Browse and explore curated tech events
- 🔍 **Event Details** - Comprehensive event information with agenda, organizer details, and more
- 📅 **Event Booking** - Simple email-based registration system
- 🏷️ **Smart Recommendations** - Get similar event suggestions based on tags
- 🌐 **Multi-Mode Support** - Online, offline, and hybrid event types
- 📱 **Responsive Design** - Seamless experience across all devices

### Technical Features
- ⚡ **Server-Side Rendering (SSR)** - Fast initial page loads
- 🔄 **Static Site Generation (SSG)** - Pre-rendered pages for optimal performance
- 💾 **Smart Caching** - Next.js cache strategies with revalidation
- 🎨 **Beautiful UI** - Custom animations and interactive light effects
- 📊 **Analytics Integration** - PostHog for user behavior tracking
- ☁️ **Image Optimization** - Cloudinary integration for media management
- 🔐 **Type Safety** - Full TypeScript implementation
- 🗃️ **NoSQL Database** - MongoDB with Mongoose ODM

---

## 🛠 Tech Stack

### Frontend
- **Framework:** Next.js 16.0.1 (App Router)
- **UI Library:** React 19.2
- **Styling:** TailwindCSS 4.0
- **Animations:** Custom OGL-based light rays, tw-animate-css
- **Icons:** Lucide React
- **Utilities:** clsx, tailwind-merge, class-variance-authority

### Backend
- **Runtime:** Node.js
- **Database:** MongoDB with Mongoose 8.20
- **Image Storage:** Cloudinary
- **Analytics:** PostHog

### Development
- **Language:** TypeScript 5
- **Linting:** ESLint 9
- **Package Manager:** npm

---

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18.0 or higher)
- **npm** or **yarn** or **pnpm**
- **MongoDB** (local installation or MongoDB Atlas account)
- **Git**

### Required Accounts
- MongoDB Atlas account (or local MongoDB instance)
- Cloudinary account (for image uploads)
- PostHog account (optional, for analytics)

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Abhay-0103/Dev-Events.git
cd Dev-Events
```

### 2. Install Dependencies

```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. Set Up Environment Variables

Create a `.env.local` file in the root directory:

```bash
touch .env
```

Add the following environment variables (see [Environment Variables](#-environment-variables) section for details):

```env
# Database
MONGODB_URI=your_mongodb_connection_string

# Application
NEXT_PUBLIC_BASE_URL=http://localhost:3000

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# PostHog (Optional)
NEXT_PUBLIC_POSTHOG_KEY=your_posthog_key
NEXT_PUBLIC_POSTHOG_HOST=https://app.posthog.com
```

---

## 🔐 Environment Variables

### Required Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `MONGODB_URI` | MongoDB connection string | `mongodb+srv://user:pass@cluster.mongodb.net/devevents` |
| `NEXT_PUBLIC_BASE_URL` | Your application URL | `http://localhost:3000` (dev) or `https://yourdomain.com` (prod) |
| `CLOUDINARY_CLOUD_NAME` | Cloudinary cloud name | `your_cloud_name` |
| `CLOUDINARY_API_KEY` | Cloudinary API key | `123456789012345` |
| `CLOUDINARY_API_SECRET` | Cloudinary API secret | `your_api_secret` |

### Optional Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `NEXT_PUBLIC_POSTHOG_KEY` | PostHog API key for analytics | `phc_xxxxxxxxxxxxx` |
| `NEXT_PUBLIC_POSTHOG_HOST` | PostHog host URL | `https://app.posthog.com` |

### Getting Your Credentials

#### MongoDB Atlas
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a new cluster (free tier available)
3. Click "Connect" → "Connect your application"
4. Copy the connection string and replace `<password>` with your database user password

#### Cloudinary
1. Sign up at [Cloudinary](https://cloudinary.com/)
2. Go to Dashboard
3. Copy your Cloud Name, API Key, and API Secret

#### PostHog
1. Sign up at [PostHog](https://posthog.com/)
2. Create a new project
3. Copy your Project API Key from Settings

---

## 🏃 Running the Application

### Development Mode

```bash
npm run dev
```

The application will start on `http://localhost:3000`

### Production Build

```bash
# Build the application
npm run build

# Start production server
npm start
```

### Linting

```bash
npm run lint
```

---

## 📁 Project Structure

```
Dev-Events/
├── app/                          # Next.js App Router
│   ├── api/                      # API Routes
│   │   └── events/              
│   │       ├── route.ts          # GET all events, POST new event
│   │       └── [slug]/          
│   │           └── route.ts      # GET event by slug
│   ├── events/                   
│   │   └── [slug]/              
│   │       └── page.tsx          # Event details page
│   ├── layout.tsx                # Root layout
│   ├── page.tsx                  # Home page
│   └── globals.css               # Global styles
│
├── components/                   # React Components
│   ├── BookEvent.tsx             # Event booking form
│   ├── EventCard.tsx             # Event card component
│   ├── EventDetails.tsx          # Event details display
│   ├── ExploreBtn.tsx            # Explore button with animation
│   ├── LightRays.tsx             # Custom light effect animation
│   └── Navbar.tsx                # Navigation bar
│
├── database/                     # Database Models
│   ├── booking.model.ts          # Booking schema
│   ├── event.model.ts            # Event schema
│   └── index.ts                  # Model exports
│
├── lib/                          # Utility Functions
│   ├── actions/                  # Server Actions
│   │   ├── booking.actions.ts    # Booking operations
│   │   └── event.actions.ts      # Event operations
│   ├── constants.ts              # App constants
│   ├── mongodb.ts                # MongoDB connection
│   └── utils.ts                  # Helper functions
│
├── public/                       # Static Assets
│   ├── icons/                    # Icon files
│   └── images/                   # Image files
│
├── .next/                        # Next.js build output
├── components.json               # shadcn/ui config
├── eslint.config.mjs             # ESLint configuration
├── next.config.ts                # Next.js configuration
├── package.json                  # Dependencies
├── postcss.config.mjs            # PostCSS configuration
├── tailwind.config.ts            # Tailwind configuration
└── tsconfig.json                 # TypeScript configuration
```

---

## 🔌 API Routes

### Events

#### GET `/api/events`
Fetch all events

**Response:**
```json
{
  "message": "Event fetched successfully",
  "events": [...]
}
```

#### GET `/api/events/[slug]`
Fetch event by slug

**Parameters:**
- `slug` (string) - Event slug

**Response:**
```json
{
  "message": "Event fetched successfully",
  "event": {...}
}
```

#### POST `/api/events`
Create a new event

**Content-Type:** `multipart/form-data`

**Body:**
```json
{
  "title": "string",
  "description": "string",
  "overview": "string",
  "image": "file",
  "venue": "string",
  "location": "string",
  "date": "string (YYYY-MM-DD)",
  "time": "string (HH:MM)",
  "mode": "online | offline | hybrid",
  "audience": "string",
  "agenda": ["string"],
  "organizer": "string",
  "tags": ["string"]
}
```

---

## 🗄 Database Models

### Event Model

```typescript
{
  title: string;           // Event title (max 100 chars)
  slug: string;            // Auto-generated URL-friendly slug
  description: string;     // Event description (max 1000 chars)
  overview: string;        // Brief overview (max 500 chars)
  image: string;          // Cloudinary image URL
  venue: string;          // Venue name
  location: string;       // Physical/virtual location
  date: string;           // Event date (ISO format)
  time: string;           // Event time (HH:MM)
  mode: string;           // "online" | "offline" | "hybrid"
  audience: string;       // Target audience
  agenda: string[];       // Array of agenda items
  organizer: string;      // Organizer information
  tags: string[];         // Event tags for categorization
  createdAt: Date;        // Auto-generated
  updatedAt: Date;        // Auto-generated
}
```

### Booking Model

```typescript
{
  eventId: ObjectId;      // Reference to Event
  slug: string;           // Event slug
  email: string;          // User email
  createdAt: Date;        // Booking timestamp
}
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit your changes**
   ```bash
   git commit -m 'Add some amazing feature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

### Development Guidelines

- Follow TypeScript best practices
- Maintain consistent code style (use ESLint)
- Write meaningful commit messages
- Update documentation for new features
- Test thoroughly before submitting PR

---


## 👨‍💻 Author

**Abhay Singh**
- GitHub: [@Abhay-0103](https://github.com/Abhay-0103)

---

## 🙏 Acknowledgments

- Next.js team for the amazing framework
- MongoDB for the flexible database
- Cloudinary for image management
- All contributors and supporters

---

## 📧 Support

If you have any questions or run into issues, please:
- Open an issue on GitHub
- Check existing issues for solutions
- Reach out via GitHub discussions

---

<div align="center">

**⭐ Star this repo if you find it helpful!**

Made with ❤️ and ☕

</div>