# Build stage #
FROM node:16.9 AS build
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Serve stage #
FROM nginx:1.21.4-alpine
COPY --from=build /usr/src/app/dist/tlcfront /usr/share/nginx/html
