# -------- Stage 1: Build --------
FROM node:18 AS build

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Build for production
RUN npm run build


# -------- Stage 2: Production --------
FROM node:18-alpine

WORKDIR /app

# Install lightweight static server
RUN npm install -g serve

# Copy build files from previous stage
COPY --from=build /app/build ./build

EXPOSE 3000

CMD ["serve", "-s", "build", "-l", "3000"]
