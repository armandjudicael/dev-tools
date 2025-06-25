# Use Ubuntu 22.04 as base image
FROM ubuntu:22.04

# Set working directory
WORKDIR /app

# Install curl, gnupg, ca-certificates first to add NodeSource repo securely
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    ca-certificates \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Add Node.js 20 repo and install Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get update && apt-get install -y nodejs && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install build-essential and other system deps
RUN apt-get update && apt-get install -y \
    git \
    nano \
    unzip \
    wget \
    python3 \
    make \
    g++ \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install global npm dev tools
RUN npm install -g \
    npm \
    yarn \
    pnpm \
    typescript \
    eslint \
    prettier \
    vite \
    webpack \
    webpack-cli \
    parcel \
    rollup \
    sass \
    less \
    stylus \
    @angular/cli \
    @vue/cli \
    create-react-app \
    react-scripts \
    tailwindcss \
    postcss \
    serve \
    http-server \
    live-server \
    degit \
    nodemon \
    concurrently \
    eslint-plugin-react \
    eslint-plugin-vue \
    eslint-plugin-angular \
    eslint-config-prettier \
    @nestjs/cli

# Optional: Install bun (experimental JS runtime)
RUN curl -fsSL https://bun.sh/install | bash

# Expose common dev ports
EXPOSE 3000 4200 5173 8080 5000 3001 3333

# Default shell
CMD ["bash"]
