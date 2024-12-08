FROM node:16 AS builder
WORKDIR /app
COPY package*.json ./ 
RUN npm install
COPY . .
# RUN ls -R /app
RUN npx tsc

FROM node:16-alpine 
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY package*.json ./
RUN npm install --only=production
CMD ["node", "dist/index.js"]