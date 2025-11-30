FROM node:24-alpine AS build

WORKDIR /app

# Copy and install dependencies
COPY package*.json .
COPY tsconfig*.json .
RUN npm install

COPY . .

RUN npm run build

EXPOSE 5000

CMD ["node", "dist/server.js"]
