FROM node:20-alpine

WORKDIR /app

# Copy dependency manifests
COPY package.json package-lock.json* ./

# Install dependencies
RUN npm install

# Copy application source code
COPY . .

# Build the React application
RUN npm run build

# Expose frontend port (serve -s build runs on port 3000 by default)
EXPOSE 3000

# Start frontend using serve
CMD ["npm", "start"]
