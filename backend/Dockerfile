FROM node:24-alpine AS build

WORKDIR /app

# Copy and install dependencies
COPY package*.json .
COPY tsconfig*.json .
RUN npm install

COPY src ./src

RUN npm run build

FROM node:24-alpine

WORKDIR /app

ENV NODE_ENV=production

COPY --from=build /app/dist ./dist
COPY --from=build /app/node_modules ./node_modules

EXPOSE 5000

CMD ["node", "dist/server.js"]
