# Use Node.js LTS version
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./

RUN npm install

# Copy all frontend files
COPY frontend .

# Build frontend for production
RUN npm run build

# Serve with a lightweight server
RUN npm install -g serve

EXPOSE 3000
CMD ["serve", "-s", "build", "-l", "3000"]
