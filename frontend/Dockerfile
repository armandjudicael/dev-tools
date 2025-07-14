# Use Ubuntu 22.04 as base image
FROM ubuntu:22.04

# Set environment variables for non-interactive apt and Bun installation
ENV DEBIAN_FRONTEND=noninteractive
ENV BUN_INSTALL="/root/.bun"

# Set working directory
WORKDIR /app

# Install initial dependencies: curl, gnupg, ca-certificates, and add NodeSource repo
# Combine these commands for better caching and smaller image layers.
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    curl \
    gnupg \
    ca-certificates && \
    curl -fsSL https://deb.nodesource.com/setup_22.x | bash - && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install Node.js and essential build tools for npm packages
# Combine with the previous step if you want to further reduce layers,
# but keeping them separate can be clearer for Node.js specific setup.
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    nodejs \
    git \
    nano \
    unzip \
    wget \
    python3 \
    make \
    g++ && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install global npm dev tools
# Prioritize specific versions if stability is key, like create-react-app.
# Use '--no-fund --no-audit' to speed up installation and reduce log noise if not needed.
RUN npm install -g \
    npm@latest \
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
    create-react-app@5.0.1 \
    react-scripts@5.0.1 \
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
    @nestjs/cli \
    --no-fund --no-audit

# Optional: Install Bun (experimental JS runtime) and add to PATH
# The Bun installation script automatically adds it to BUN_INSTALL/bin.
# We set BUN_INSTALL as an ENV variable earlier and then add it to PATH.
RUN curl -fsSL https://bun.sh/install | bash

# Add bun to PATH (ensures it's available for subsequent commands and when the container runs)
ENV PATH="${BUN_INSTALL}/bin:${PATH}"

# Expose common dev ports
EXPOSE 3000 4200 5173 8080 5000 3001 3333

# Default shell
# Consider ENTRYPOINT for more robust container execution patterns if you always
# want a specific command to run when the container starts. For a dev image, CMD bash is fine.
CMD ["bash"]