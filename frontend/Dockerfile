# ----------------------------
# 🔹 Stage 1: Build Stage
# ----------------------------
FROM node:21 AS frontend-builder

# Set the working directory
WORKDIR /app

# Copy only package files to install dependencies
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Optional: Build the frontend if needed (React/Vite/Next etc.)
# RUN npm run build


# ----------------------------
# 🔹 Stage 2: Final Stage
# ----------------------------
FROM node:21-slim

# Set the working directory
WORKDIR /app

# Copy all files from builder stage
COPY --from=frontend-builder /app .

# Copy env file (optional, ensure the file exists)
COPY .env.docker .env.local

# Expose the frontend port (e.g., 3000 for React/Vite)
EXPOSE 3000

# Start the frontend app
CMD ["npm", "start"]
