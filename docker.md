1.Docker one of software to create containers
2.Docker solves it works in my machine but not in other machine(server/teammates)
based on images and containers
3.fundamentals
      a.images and containers,
      b.data and volumes,
      c.Docker network
4.for mern app need 3 images 1.MongoDB 2.Node API 3.React (Frontend) have docker-compose.yml in root of project . run docker compose in root directory or use docker gui   

5.example of  yml file

"version: '3.8'

services:
  # 1. MongoDB Database Container
  database:
    image: mongo:latest
    ports:
      - "27017:27017"
    volumes:
      - mongo-data:/data/db

  # 2. Node.js API Container
  backend:
    build: ./backend # Points to the folder with your Backend Dockerfile
    ports:
      - "5000:5000"
    environment:
      - MONGO_URI=mongodb://database:27017/mydatabase # Uses the service name 'database' as the hostname
    depends_on:
      - database

  # 3. React Frontend Container
  frontend:
    build: ./frontend # Points to the folder with your Frontend Dockerfile
    ports:
      - "3000:3000"
    depends_on:
      - backend

volumes:
  mongo-data: # Ensures your database data isn't lost when containers stop
"
share the git or just yml file git for team dev and yml for tester..


