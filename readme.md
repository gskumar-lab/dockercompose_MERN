# 🚀 MERN Stack App with Docker Compose

This project is a full-featured **MERN (MongoDB, Express.js, React, Node.js)** application that runs entirely inside Docker containers. It includes frontend, backend, database, and Cypress end-to-end testing setup.

---

## 📁 Project Structure

```
.
├── docker-compose.yaml       # Defines all services
├── backend/                  # Express.js API
│   ├── Dockerfile            # Builds backend image
│   ├── db/                   # MongoDB connection
│   │   └── connection.js
│   ├── routes/               # API endpoints
│   │   └── record.js
│   ├── server.js             # Entry point for API
│   └── package*.json         # Dependencies
│
├── frontend/                 # React app with Tailwind
│   ├── Dockerfile            # Builds frontend image
│   ├── src/                  # App source code
│   │   ├── App.jsx
│   │   ├── components/
│   │   └── main.jsx
│   ├── public/               # Static assets
│   ├── cypress/              # End-to-end tests
│   ├── tailwind.config.js
│   ├── vite.config.js
│   └── package*.json         # Frontend dependencies

```

---

## 🐳 Dockerized Services

| Service    | Description           | Port (Host\:Container) |
| ---------- | --------------------- | ---------------------- |
| `frontend` | React app via Vite    | `5173:5173`            |
| `backend`  | Node.js + Express API | `5050:5050`            |
| `mongodb`  | MongoDB database      | `27017:27017`          |

---

## 🔧 Environment Variables

* **Backend**

  * `MONGO_URI`: `mongodb://mongo:27017/mydatabase`
* **Frontend**

  * `REACT_APP_API_URL`: `http://backend:5050`

These are injected automatically via `docker-compose.yaml`.

---

## ⚙️ Getting Started

### 1. Clone and Setup

```bash
git clone https://github.com/gskumar-lab/dockercompose_MERN.git
cd dockercompose_MERN
```

Ensure the following structure is preserved:

```
.
├── docker-compose.yaml
├── backend/
└── frontend/
```

### 2. Start the Application

```bash
docker-compose up --build
```

* React App → [http://localhost:5173](http://localhost:5173)
* API Server → [http://localhost:5050](http://localhost:5050)

MongoDB is accessible internally as `mongodb://mongo:27017`.

---

## 🗃️ MongoDB Persistence

MongoDB uses a named volume `mongo-data` to persist your data even after container restarts:

```yaml
volumes:
  mongo-data:
    driver: local
```

---

## 📦 Common Docker Commands

| Command                     | Description                          |
| --------------------------- | ------------------------------------ |
| `docker-compose up --build` | Build and run containers             |
| `docker-compose down`       | Stop all services                    |
| `docker-compose down -v`    | Stop all services and remove volumes |

---