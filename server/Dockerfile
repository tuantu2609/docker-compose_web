# Dockerfile  
FROM node:14  

# Thiết lập thư mục làm việc
WORKDIR /app  

# Sao chép package.json và package-lock.json (nếu có)
COPY package.json package-lock.json ./

# Cài đặt dependencies
RUN npm install
RUN npm rebuild bcrypt --build-from-source

# Sao chép mã nguồn
COPY . .

# Mở cổng
EXPOSE 3001  

# Chạy ứng dụng
CMD ["npm", "start"]
