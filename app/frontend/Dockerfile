# =========================
# Stage 1 - Build React App
# =========================
FROM node:16-alpine AS builder

WORKDIR /app
   
# Copy package files  
COPY package*.json ./    
  
# Install dependencies   
RUN npm install
 
# Copy source code
COPY . .
# Build arg passed during docker build
ARG REACT_APP_BACKEND_URL
ENV REACT_APP_BACKEND_URL=$REACT_APP_BACKEND_URL
# Build production app
RUN npm run build

# =========================
# Stage 2 - Serve Using Nginx
# =========================
FROM nginx:stable-alpine
  
# Remove default nginx content
RUN rm -rf /usr/share/nginx/html/*

# Copy React build files
COPY --from=builder /app/build /usr/share/nginx/html

# Expose nginx port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
