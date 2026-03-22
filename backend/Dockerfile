FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci

# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Switch to non-root user
USER appuser

# Copy rest of the code
COPY . .

EXPOSE 8000

CMD ["node", "src/server.js"]