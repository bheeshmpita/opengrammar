FROM node:20-alpine AS builder

WORKDIR /app

# Copy root package configurations and lockfiles if they exist
COPY package*.json ./
COPY tsconfig*.json ./

# Copy backend and shared source trees
COPY backend/package*.json ./backend/
COPY shared/ ./shared/
COPY backend/ ./backend/

WORKDIR /app/backend
RUN npm install --omit=dev --no-audit --no-fund

FROM node:20-alpine AS runner

WORKDIR /app

ENV NODE_ENV=production
ENV PORT=8787

# Copy installed dependencies and source
COPY --from=builder /app /app

WORKDIR /app/backend

EXPOSE 8787

CMD ["npm", "start"]
