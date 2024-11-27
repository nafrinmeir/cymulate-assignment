# Stage 1
FROM node:20-alpine AS builder
WORKDIR /app
COPY package.json .
RUN npm install

# Stage 2
FROM node:20-alpine
RUN apk --no-cache add bash vim curl && \
    adduser -D -u 1500 -h /home/user user
USER user
WORKDIR /home/user
COPY --from=builder /app/node_modules ./node_modules
COPY docker-test.js k8s-test.js cymulate-assignment-index.html ./
COPY start.sh ./
USER root
RUN chmod +x /home/user/start.sh
USER user
ENTRYPOINT ["sh", "start.sh"]
