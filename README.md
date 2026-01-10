# VTEAM – local development setup

This repository contains a docker-compose setup to run:

- Backend (Node.js + MongoDB)
- Admin client (Vite + Nginx)
- User client (Vite + Nginx)

## Requirements
- Docker
- Docker Compose

## Setup
Clone the following repositories next to this repo:

- backend-vteam
- vteam-admin-client
- user-client

Folder structure:

vteam/
├── vteam-deploy
├── backend-vteam
├── vteam-admin-client
└── user-client

## Run
```bash
docker compose up --build
```

## Routes 
Admin: http://localhost:3001

User: http://localhost:3002

Backend: http://localhost:3000

## Environment variables

Create a `.env` file in the `backend-vteam` directory with the following content:

```env
PORT=3000

# MongoDB (used by docker-compose)
MONGO_DSN=mongodb://mongo:27017/vteam
NODE_ENV=development

# Optional test database
MONGO_DSN_TEST=mongodb://localhost:27017/test

# GitHub OAuth
GITHUB_CALLBACK_URL=http://localhost:3000/api/auth/github/callback
GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_client_secret
```

### GitHub OAuth (optional)
To enable GitHub login, create an OAuth App on GitHub:
https://github.com/settings/developers

Use the following callback URL:
http://localhost:3000/api/auth/github/callb