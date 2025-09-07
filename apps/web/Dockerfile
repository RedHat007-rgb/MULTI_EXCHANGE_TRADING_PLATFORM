# Use Node 18 Alpine
FROM node:18-alpine

# Install system dependencies
RUN apk update && apk add --no-cache libc6-compat bash git

# Set working directory
WORKDIR /app

# Install pnpm globally
RUN corepack enable pnpm

# Copy only what’s needed for web
COPY package.json pnpm-lock.yaml pnpm-workspace.yaml turbo.json ./
COPY apps/web ./apps/web
COPY packages ./packages

# Install dependencies
RUN pnpm install

# Expose Next.js default port
EXPOSE 3001

# Start Next.js dev server for web app
WORKDIR /app/apps/web
CMD ["pnpm", "dev"]
