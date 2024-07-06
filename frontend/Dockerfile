FROM node:20

WORKDIR /app

COPY package*.json /app/

RUN npm install

COPY ./ /app/

ARG VITE_API_URL=http://localhost:8000

RUN npm run build
