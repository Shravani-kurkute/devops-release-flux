FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci

# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Give ownership of /app to appuser
RUN chown -R appuser:appgroup /app

# Switch to non-root user
USER appuser

# Copy with correct ownership
COPY --chown=appuser:appgroup . .

# Build the Next.js app
RUN npm run build

EXPOSE 3000

CMD ["npm", "start"]