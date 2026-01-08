# Stage 1: Build Vite app
FROM node:20-alpine AS build

WORKDIR /app

# Copy dependency files first (for caching)
COPY package.json package-lock.json* ./

# Install dependencies
RUN npm install

# Copy the source code
COPY . .

# Build production files (outputs to /app/dist)
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:alpine

# Remove default files
RUN rm -rf /usr/share/nginx/html/*

# Copy Vite build files
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
