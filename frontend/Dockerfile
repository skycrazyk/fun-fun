# syntax=docker/dockerfile:1
FROM node:18.4-alpine as base

WORKDIR /app

COPY package.json .
COPY package-lock.json .

RUN npm ci

COPY . . 

RUN npm run build

FROM nginx:1.23.0

COPY --from=base /app/build /usr/share/nginx/html 
