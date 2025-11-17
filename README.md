# HouseHunt - Rental Marketplace

**HouseHunt** is a full-stack web application designed to simplify the rental process by directly connecting tenants with property owners. It features a robust backend API for managing users and properties, and a responsive frontend interface for easy navigation and searching.

## 🚀 Features

### For Tenants

  * **Advanced Search:** Search properties by city, neighborhood, or ZIP code.
  * **Smart Filters:** Filter by budget, BHK, amenities, parking, and more.
  * **View Details:** High-quality image galleries and detailed property descriptions.
  * **Tools:** Integrated Budget Calculator and Area Converter.

### For Landlords (Owners)

  * **Property Management:** Post new listings with images, details, and location.
  * **Dashboard:** Manage published listings and update occupancy status (Available/Occupied).
  * **Direct Connection:** No middlemen—tenants contact owners directly.

### For Admins

  * **User Management:** View, block, or delete users.
  * **Property Oversight:** Monitor and moderate property listings.
  * **Statistics:** View platform analytics.

-----

## 🛠️ Tech Stack

### Frontend

  * **Core:** HTML5, CSS3, Vanilla JavaScript (ES6+)
  * **Styling:** Custom CSS variables, responsive Grid/Flexbox layouts.
  * **Deployment:** Static hosting (e.g., Netlify/Vercel or standard web server).

### Backend

  * **Runtime:** Node.js
  * **Framework:** Express.js
  * **Database:** MongoDB (via Mongoose)
  * **Authentication:** JWT (JSON Web Tokens) & Bcrypt
  * **Image Storage:** Cloudinary
  * **Validation:** Joi
  * **Security:** Helmet, CORS, Express Rate Limit

-----

## 📂 Project Structure

```text
House_Hunt_Fullstack/
├── House_Hunt-Backend/         # Node.js API Server
│   ├── config/                 # DB connection
│   ├── controllers/            # Route logic
│   ├── middleware/             # Auth, Upload, Validation
│   ├── models/                 # Mongoose Schemas (User, Property)
│   ├── routes/                 # API Endpoints
│   ├── utils/                  # Cloudinary, JWT helpers
│   ├── validators/             # Joi schemas
│   └── server.js               # Entry point
│
└── house_hunt_frontend/        # Static Client
    ├── index.html              # Landing page
    ├── search.html             # Search results page
    ├── addProperty.html        # Listing creation
    ├── css/                    # Stylesheets
    └── js/                     # Frontend logic & API service
```

-----

## ⚙️ Installation & Setup

### Prerequisites

  * [Node.js](https://nodejs.org/) (v14+ recommended)
  * [MongoDB](https://www.mongodb.com/) (Local or Atlas)
  * [Cloudinary Account](https://cloudinary.com/) (For image uploads)

### 1\. Backend Setup

1.  Navigate to the backend directory:
    ```bash
    cd House_Hunt-Backend
    ```
2.  Install dependencies:
    ```bash
    npm install
    ```
3.  Create a `.env` file in the root of `House_Hunt-Backend` and add the following variables:
    ```env
    PORT=5000
    MONGO_URI=your_mongodb_connection_string
    JWT_SECRET=your_strong_jwt_secret
    JWT_EXPIRES_IN=7d

    # Cloudinary Configuration
    CLOUDINARY_CLOUD_NAME=your_cloud_name
    CLOUDINARY_API_KEY=your_api_key
    CLOUDINARY_API_SECRET=your_api_secret
    ```
4.  Start the server:
    ```bash
    # For development (requires nodemon)
    npm run dev

    # For production
    npm start
    ```
    *The server should run on `http://localhost:5000`.*

### 2\. Frontend Setup

1.  Navigate to the frontend directory:
    ```bash
    cd house_hunt_frontend
    ```
2.  **Configure API URL:**
    Open `config.js`. By default, it might point to a production URL. For local development, update `BASE_URL`:
    ```javascript
    // house_hunt_frontend/config.js
    const API_CONFIG = {
      BASE_URL: 'http://localhost:5000/api', // Update this to your local backend
      // ...
    };
    ```
3.  **Run the app:**
    Since the frontend is static HTML/JS, you can use **Live Server** (VS Code Extension) or `http-server` to serve the files.
      * Open `index.html` in your browser.

-----

## 📡 API Endpoints

### Authentication

  * `POST /api/auth/signup` - Register a new user (Tenant/Owner)
  * `POST /api/auth/login` - Login and receive JWT
  * `GET /api/auth/me` - Get current user profile

### Properties

  * `GET /api/properties` - Get all properties (supports query filters: `city`, `price`, `bhk`, etc.)
  * `GET /api/properties/:id` - Get single property details
  * `POST /api/properties` - Create listing (Owner only, Mult-part form data)
  * `PUT /api/properties/:id` - Update listing (Owner only)
  * `DELETE /api/properties/:id` - Delete listing (Owner only)

### Admin

  * `GET /api/admin/users` - View all users
  * `PUT /api/admin/users/:id/block` - Block/Unblock user
  * `GET /api/admin/stats` - View dashboard statistics

-----

## 👥 Contributors

  * **Harshit Bhatnagar** - Frontend & UI/UX Developer
  * **Sarim Hussain** - Backend Developer
  * **Gaurav Sharma** - Backend Integration

-----

