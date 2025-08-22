# 📝 MERN NoteTaking App

A full-stack note-taking application built with the MERN stack (MongoDB, Express.js, React, Node.js) featuring a modern UI, rate limiting, and real-time operations.

## ✨ Features

- **📝 Create Notes**: Add new notes with title and content
- **📖 Read Notes**: View all notes in a responsive grid layout
- **✏️ Update Notes**: Edit existing notes seamlessly
- **🗑️ Delete Notes**: Remove notes you no longer need
- **🔄 Real-time Updates**: Instant feedback for all operations
- **🚦 Rate Limiting**: Prevents API abuse with Upstash Redis
- **📱 Responsive Design**: Works perfectly on all devices
- **🎨 Modern UI**: Built with TailwindCSS and DaisyUI
- **⚡ Fast Performance**: Optimized with Vite for lightning-fast development

## 🛠️ Tech Stack

### Frontend
- **React 19** - UI library
- **Vite** - Build tool and development server
- **TailwindCSS** - Utility-first CSS framework
- **DaisyUI** - Component library for TailwindCSS
- **React Router** - Client-side routing
- **Axios** - HTTP client for API requests
- **React Hot Toast** - Beautiful notifications
- **Lucide React** - Modern icons

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **Upstash Redis** - Rate limiting and caching
- **CORS** - Cross-origin resource sharing
- **dotenv** - Environment variable management

## 📋 Prerequisites

Before running this application, make sure you have the following installed:

- **Node.js** (v16 or higher)
- **npm** (v7 or higher)
- **MongoDB** (local installation or MongoDB Atlas account)
- **Upstash Redis** account (for rate limiting)

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/Dheenadhayalan12/mern_NoteTaking.git
cd mern_NoteTaking
```

### 2. Environment Setup

Create a `.env` file in the `backend` directory:

```env
# MongoDB Connection
MONGO_URI=mongodb://localhost:27017/notetaking
# or for MongoDB Atlas:
# MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/notetaking

# Upstash Redis (for rate limiting)
UPSTASH_REDIS_REST_URL=your_upstash_redis_url
UPSTASH_REDIS_REST_TOKEN=your_upstash_redis_token

# Server Configuration
PORT=5001
NODE_ENV=development
```

### 3. Install Dependencies and Build

```bash
# Install all dependencies and build the project
npm run build
```

This command will:
- Install backend dependencies
- Install frontend dependencies
- Build the frontend for production

### 4. Start the Application

```bash
# Start the backend server
npm start
```

The application will be available at `http://localhost:5001`

## 🔧 Development Mode

For development with hot reloading:

### Start Backend (Development)
```bash
cd backend
npm run dev
```

### Start Frontend (Development)
```bash
cd frontend
npm run dev
```

The frontend development server will run on `http://localhost:5173`

## 📚 API Documentation

### Base URL
```
http://localhost:5001/api
```

### Endpoints

#### Get All Notes
```http
GET /api/notes
```
**Response:**
```json
[
  {
    "_id": "note_id",
    "title": "Note Title",
    "content": "Note content...",
    "createdAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
]
```

#### Get Note by ID
```http
GET /api/notes/:id
```

#### Create New Note
```http
POST /api/notes
Content-Type: application/json

{
  "title": "My New Note",
  "content": "This is the content of my note..."
}
```

#### Update Note
```http
PUT /api/notes/:id
Content-Type: application/json

{
  "title": "Updated Title",
  "content": "Updated content..."
}
```

#### Delete Note
```http
DELETE /api/notes/:id
```

### Rate Limiting

The API implements rate limiting with the following rules:
- **100 requests per 60 seconds** per IP address
- Rate limit status: `429 Too Many Requests`

## 📁 Project Structure

```
mern_NoteTaking/
├── backend/
│   ├── src/
│   │   ├── config/
│   │   │   ├── db.js          # MongoDB connection
│   │   │   └── upstash.js     # Redis configuration
│   │   ├── controllers/
│   │   │   └── notesController.js  # CRUD operations
│   │   ├── middleware/
│   │   │   └── rateLimiter.js # Rate limiting middleware
│   │   ├── models/
│   │   │   └── Note.js        # Note schema
│   │   ├── routes/
│   │   │   └── notesRoutes.js # API routes
│   │   └── server.js          # Express server setup
│   └── package.json
├── frontend/
│   ├── src/
│   │   ├── assets/           # Static assets
│   │   ├── component/        # React components
│   │   │   ├── Navbar.jsx
│   │   │   ├── NoteCard.jsx
│   │   │   ├── NotesNotFound.jsx
│   │   │   └── RateLimitedUI.jsx
│   │   ├── lib/
│   │   │   └── axios.js      # Axios configuration
│   │   ├── pages/            # Page components
│   │   │   ├── HomePage.jsx
│   │   │   ├── CreatePage.jsx
│   │   │   └── NoteDetailPage.jsx
│   │   ├── App.jsx           # Main app component
│   │   └── main.jsx          # App entry point
│   ├── index.html
│   ├── package.json
│   ├── tailwind.config.js
│   └── vite.config.js
├── package.json              # Root package.json
└── README.md
```

## 🎨 UI Components

### Pages
- **HomePage**: Displays all notes in a responsive grid
- **CreatePage**: Form to create new notes
- **NoteDetailPage**: View and edit individual notes

### Components
- **Navbar**: Navigation header with app branding
- **NoteCard**: Individual note display card
- **NotesNotFound**: Empty state when no notes exist
- **RateLimitedUI**: Displays when rate limit is exceeded

## 🌐 Deployment

### Environment Variables for Production

```env
NODE_ENV=production
MONGO_URI=your_production_mongodb_uri
UPSTASH_REDIS_REST_URL=your_upstash_redis_url
UPSTASH_REDIS_REST_TOKEN=your_upstash_redis_token
PORT=5001
```

### Deploy to Heroku

1. Create a Heroku app
2. Set environment variables in Heroku dashboard
3. Connect your GitHub repository
4. Deploy from the main branch

### Deploy to Vercel/Netlify

1. Build the project: `npm run build`
2. The frontend build files are in `frontend/dist`
3. Deploy the backend separately to services like Railway, Render, or Heroku

## 🧪 Testing

### Frontend Linting
```bash
cd frontend
npm run lint
```

### Build Verification
```bash
npm run build
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📝 License

This project is licensed under the ISC License.

## 🐛 Known Issues

- None currently reported

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/Dheenadhayalan12/mern_NoteTaking/issues) page
2. Create a new issue with detailed description
3. Include error messages and steps to reproduce

## 🙏 Acknowledgments

- [MongoDB](https://www.mongodb.com/) for the database
- [Express.js](https://expressjs.com/) for the backend framework
- [React](https://reactjs.org/) for the frontend library
- [TailwindCSS](https://tailwindcss.com/) for styling
- [DaisyUI](https://daisyui.com/) for UI components
- [Upstash](https://upstash.com/) for Redis services

---

**Happy Note Taking! 📝✨**