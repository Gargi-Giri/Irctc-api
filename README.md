🚆 IRCTC API – Railway Reservation System

A simple and scalable railway reservation system built using Node.js, Express, and MySQL, mimicking core IRCTC functionalities. This API allows users to register, log in, search for trains, check seat availability, and book tickets. Admins can manage train data securely using API key-based protection.

🔧 Features

User Registration & Login (with token-based authentication)
Admin APIs (protected via API key):
Add new trains
Update seat availability
User APIs:
Search trains between two stations
Check seat availability
Book tickets
View booking details
Handles race conditions during booking to avoid double-booking seats
🛠️ Tech Stack

Backend: Node.js, Express.js
Database: MySQL
Authentication: JWT (JSON Web Tokens)
Security: API Key for admin-level operations
⚙️ Getting Started

1. Clone the repository
git clone https://github.com/Gargi-Giri/Irctc-api.git
cd Irctc-api
2. Install dependencies
npm install
3. Setup MySQL Database
Create a MySQL database (e.g., irctc_db)
Update the database credentials in db.js:
const db = mysql.createConnection({
  host: "localhost",
  user: "your_mysql_username",
  password: "your_mysql_password",
  database: "irctc_db"
});
Import the provided SQL file (schema.sql if you have one) to create the required tables, or refer to model files and manually create them.
🚀 Running the Application

node app.js
The server will start on http://localhost:3000

🔐 Environment Setup

Create a .env file in the root directory with:

PORT=3000
JWT_SECRET=your_jwt_secret
ADMIN_API_KEY=your_secure_admin_api_key
📬 API Endpoints

✅ Public
POST /register – Register a new user
POST /login – Login and receive JWT token
🔒 Admin (Requires API Key in headers)
POST /add-train – Add a new train
Headers: x-api-key: ADMIN_API_KEY
👤 User (JWT Required)
GET /trains?source=SRC&destination=DEST – Get trains between stations
GET /availability/:trainId?source=SRC&destination=DEST – Check seat availability
POST /book/:trainId – Book a seat
GET /booking/:bookingId – Get booking details
📦 Sample Admin API Key Usage

POST /add-train
Headers:
  x-api-key: your_admin_api_key
Body:
{
  "name": "Rajdhani Express",
  "source": "Delhi",
  "destination": "Mumbai",
  "totalSeats": 100
}
🧪 Optional: Testing

Use Postman or any API testing tool to hit the endpoints. Include tokens/API keys where necessary.

❗ Assumptions Made

Users are authenticated using JWT.
Admin operations are protected using a static API key passed in headers.
Trains follow a linear route (source to destination).
Booking race conditions are managed using database-level atomic transactions.
🤝 Contributing

Found a bug or want to improve something? Feel free to fork the repo and open a pull request!

📄 License

This project is licensed under the MIT License.
