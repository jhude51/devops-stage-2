#Stage 0
FROM node:20 AS builder

WORKDIR /app

COPY package*.json /app/

RUN npm install

COPY ./ /app/

#ARG VITE_API_URL=http://localhost:8000

EXPOSE 5173

RUN npm run build

# Stage 1
FROM nginx:alpine

COPY --from=builder /app/dist/ /usr/share/nginx/html

COPY ./nginx.conf /etc/nginx/conf.d/default.conf
COPY ./nginx-not-found.conf /etc/nginx/extra-conf.d/backend-not-found.conf
