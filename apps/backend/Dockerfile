FROM oven/bun:1 AS base
WORKDIR /app

# Copy workspace manifests
COPY package.json bun.lock ./
COPY apps/backend/package.json ./apps/backend/
COPY packages/shared/package.json ./packages/shared/

# Copy source DULU sebelum bun install (supaya prisma postinstall bisa akses schema)
COPY apps/backend ./apps/backend
COPY packages/shared ./packages/shared

RUN bun install

WORKDIR /app/apps/backend

RUN bunx prisma generate

EXPOSE 3000
CMD ["bun", "run", "src/index.ts"]