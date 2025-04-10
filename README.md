# 📁 GitHub Projects CRM Backend

This is a simple Express-based backend with SQLite used for storing public GitHub repositories per authenticated user.

## 🚀 Features

- ✅ Save or update repositories linked to a user’s email  
- 📬 Retrieve all repositories for a specific user  
- ❌ Remove a repository by specifying owner, name, and email  
- 💾 Store detailed repo info: stars, forks, issues, and creation timestamp

## ⚙️ Setup

### 1. Clone & install

```bash
git clone https://github.com/Ostrynska/gh-projects-manager-api.git
cd gh-projects-manager-api
npm install
```

### 2. Create .env
```bash
PORT=''
```

### 3. Run server
```bash
node server.js
```

### 📡 API Endpoints

####  `GET /api/user-projects?email=...`
Returns all GitHub repositories associated with the given user's email.

#### `PATCH /api/save-projects`
Saves or updates GitHub repositories for a given user.

**Request Body**:
```json
{
  "email": "user@example.com",
  "projects": [
    {
      "owner": "facebook",
      "name": "react",
      "url": "https://github.com/facebook/react",
      "stars": 212000,
      "forks": 45000,
      "issues": 1000,
      "createdAt": 1712351234123
    }
  ]
}
```

####  `DELETE /api/delete-project`
Deletes a specific repository from the user's project list.
```json
{
  "email": "user@example.com",
  "owner": "facebook",
  "name": "react"
}
```

## 🗃️ Database

Stored in projects.db file and uses a single table user_projects:
| Field      | Type     | Description             |
|------------|----------|-------------------------|
| `id`       | integer  | Primary key (autoincrement) |
| `email`    | text     | User's email address    |
| `owner`    | text     | GitHub repository owner |
| `name`     | text     | GitHub repository name  |
| `url`      | text     | URL of the repository   |
| `stars`    | number   | Number of stars         |
| `forks`    | number   | Number of forks         |
| `issues`   | number   | Number of open issues   |
| `createdAt`| number   | Creation timestamp (in ms) |

## 🛡️ CORS & JSON

CORS and JSON parsing enabled by default:
```bash
app.use(cors());
app.use(express.json());
```

## 🧪 Test API locally

You can test endpoints using Postman or Insomnia. The default base URL is:
```bash
http://localhost:3001
```
