FROM node:18

WORKDIR /workspaces/ClientApp

# Install build dependencies
RUN apt-get update && apt-get install -y \
    python3 \
    make \
    g++ \
    git \
    openssh-client \
    && rm -rf /var/lib/apt/lists/*

# Install Angular CLI globally
RUN npm install -g @angular/cli@latest

# Copy package files
COPY package.json ./

# Install dependencies with specific flags
RUN npm install \
    --no-optional \
    --legacy-peer-deps \
    --force && \
    npm install @rollup/rollup-linux-x64-gnu --force

# Copy the rest of the project files
COPY . .

# Expose port
EXPOSE 4200

# Start development server
CMD ["npx", "ng", "serve", "--host", "0.0.0.0", "--port", "4200"]

 