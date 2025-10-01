# Stage 1: Build the React application
# LTS Node.js version
FROM node:22.20.0-alpine3.22 AS builder

WORKDIR /app

ARG VITE_API_URL
ENV VITE_API_URL=${VITE_API_URL}

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build

# Stage 2: Production runtime with Vite preview
FROM node:22.20.0-alpine3.22

WORKDIR /app

RUN npm install vite

COPY --from=builder /app/dist ./dist

RUN addgroup -g 1001 -S app && \
    adduser -S -D -H -u 1001 -h /app -s /sbin/nologin -G app app && \
    chown -R app:app /app

USER app

EXPOSE 5173

HEALTHCHECK --interval=30s --timeout=3s --start-period=10s --retries=3 \
  CMD wget --quiet --tries=1 --spider http://localhost:5173 || exit 1

CMD ["npx", "vite", "preview", "--host", "0.0.0.0", "--port", "5173"]