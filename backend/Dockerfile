# --------------------------
# 🔹 Stage 1: Build Stage
# --------------------------
FROM node:21 AS backend-builder

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the application code
COPY . .

# Optional: build step (if using TypeScript or build tools)
# RUN npm run build

# --------------------------
# 🔹 Stage 2: Runtime Stage
# --------------------------
FROM node:21-slim

# Set working directory
WORKDIR /app

# Copy only the necessary files from the builder stage
COPY --from=backend-builder /app .

# Copy environment-specific file (make sure this file exists)
COPY .env.docker .env

# Expose port (change if your app runs on another port)
EXPOSE 5000

# Start the application
CMD ["npm", "start"]
