# Stage 1: Build the app
FROM node:18-alpine AS build
# Use a small Node.js image for faster builds

WORKDIR /app
# Set the working directory inside the container

COPY package*.json ./
# Copy only package files first (helps with caching Docker layers)
RUN npm install
# Install dependencies

COPY . .
# Copy the rest of the app files (src/, public/, etc.)

RUN npm run build
# Build the React app into static files (output goes to dist/)

# Stage 2: Serve the built files with NGINX
FROM nginx:alpine
# Use a tiny, efficient web server to serve the static files

COPY --from=build /app/dist /usr/share/nginx/html
# Copy the built frontend from the previous stage

EXPOSE 80
# Let Docker know this container listens on port 80

CMD ["nginx", "-g", "daemon off;"]
# Start NGINX in the foreground so the container keeps running
