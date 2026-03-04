# Use simple official Node image
FROM node:20

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Expose service port (change if needed)
EXPOSE 50051

# Start application
CMD ["node", "index.js"]
