# Build stage
FROM node:24-alpine AS build

# Set working directory
WORKDIR /app

# Copy and install dependencies
COPY package*.json .
COPY tsconfig*.json .
RUN npm install

# Copy source code
COPY . .

# Build app
RUN npm run build

# Production stage
FROM nginx:alpine

# Copy files for built app
COPY --from=build /app/dist /usr/share/nginx/html

# Serve app in exposed port 80
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
