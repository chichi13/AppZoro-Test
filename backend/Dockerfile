# LTS Node.js version
FROM node:22.20.0-alpine3.22

RUN apk add --no-cache python3 make g++

WORKDIR /app

COPY package*.json ./

RUN npm ci --only=production

COPY . .

RUN addgroup -g 1001 -S app && \
    adduser -S -D -H -u 1001 -h /app -s /sbin/nologin -G app app && \
    chown -R app:app /app

USER app

EXPOSE 5007

CMD ["npm", "start"]