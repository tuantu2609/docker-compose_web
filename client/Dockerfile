# Bước 1: Sử dụng hình ảnh Node để xây dựng ứng dụng
FROM node:14 AS build

# Bước 2: Đặt thư mục làm việc bên trong container
WORKDIR /app

# Bước 3: Sao chép các tệp package.json và package-lock.json
COPY package*.json ./

# Bước 4: Cài đặt các phụ thuộc
RUN npm install

# Bước 5: Sao chép phần còn lại của mã nguồn ứng dụng
COPY . .

# Bước 6: Xây dựng ứng dụng
RUN npm run build

# Bước 7: Sử dụng Nginx để phục vụ các tệp đã xây dựng
FROM nginx:alpine

# Bước 8: Sao chép các tệp đã xây dựng vào thư mục của nginx
COPY --from=build /app/build /usr/share/nginx/html

# Bước 9: Expose cổng 80 mà nginx sẽ chạy
EXPOSE 80

# Bước 10: Khởi động máy chủ nginx
CMD ["nginx", "-g", "daemon off;"]
