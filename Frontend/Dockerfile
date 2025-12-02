FROM node:lts-alpine as builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Lệnh BUILD tạo ra file tĩnh, giả sử vào thư mục /app/dist
RUN npm run build
