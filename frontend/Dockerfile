FROM node:20 AS builder

WORKDIR /app

COPY package*.json /app/

RUN npm install

COPY ./ /app/

ARG VITE_API_URL=http://localhost:8000

RUN npm run dev

