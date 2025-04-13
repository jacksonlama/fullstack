FROM node:18-alpine
# Use a small Node.js image

WORKDIR /app
# Set working directory inside the container

COPY package*.json ./
# Copy only package files for better layer caching
RUN npm install
# Install backend dependencies

COPY . .
# Copy the backend app files (like index.js)

EXPOSE 5000
# Tell Docker this app uses port 5000

CMD ["node", "index.js"]
# Start the backend server
