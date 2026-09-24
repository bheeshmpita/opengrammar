FROM node:20-alpine

WORKDIR /app

# Install the official compiled server package
RUN npm install -g opengrammar-server

EXPOSE 8787
ENV PORT=8787
ENV NODE_ENV=production

# Run the standalone service
CMD ["opengrammar-server", "--port", "8787"]
