# Use the official Node.js LTS image as the base
FROM node:20-alpine

# Set working directory in the container
WORKDIR /app

# Install system dependencies
RUN apk add --no-cache \
    git \
    openssh-client \
    bash

# Install Angular CLI globally
RUN npm install -g @angular/cli

# Copy package.json and package-lock.json
COPY package*.json ./

# Install project dependencies
RUN npm ci

# Copy the rest of the project files
COPY . .

# Expose the default Angular development server port
EXPOSE 4200

# Set the default command to start the Angular development server
# CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "4200"]
CMD ["tail", "-f", "/dev/null"]