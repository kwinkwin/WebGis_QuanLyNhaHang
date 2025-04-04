# Hướng dẫn chạy project WebGis

## 1. Cài đặt Node.js

Nếu đã cài rồi thì bỏ qua bước này.

## 2. Cài đặt, set up database (MySQL)

- Mở file `.env` và kiểm tra xem các thông số về database có giống với `DATABASE_URL` (username, password, host, port, database) không.
- Nếu chưa có database thì tạo database mới và đặt tên là `gis`.
- Mở terminal trong VSCode và chạy các lệnh sau:
  ```sh
  npm install -g @vue/cli  # Cài đặt Vue CLI - trình quản lý package của Node.js
  npx prisma db push       # Update db (tạo các bảng theo yêu cầu trong database gis)
  ```
- Sau khi đã có các bảng, tiến hành import dữ liệu từ file `.sql` lần lượt theo thứ tự:
  1. User
  2. Profile
  3. Projection
  4. Location
  5. MapView
  6. MapLayer
  7. Feature
- Để kiểm tra dữ liệu, có thể dùng MySQL hoặc mở Prisma Studio bằng lệnh:
  ```sh
  npx prisma studio
  ```
  _(Prisma Studio cung cấp giao diện trực quan để quản lý và kiểm tra dữ liệu, nhưng không bắt buộc.)_

## 3. Set up để chạy cả FE và BE cùng lúc

- Mở terminal trong VSCode và chạy lệnh:
  ```sh
  npm install concurrently --save-dev  # Cài đặt concurrently để chạy nhiều lệnh cùng lúc
  ```
- Mở file `package.json` và thêm vào cuối phần `scripts`:
  ```json
  "start:all": "concurrently \"npm run dev\" \"npm start\""
  ```
- Để chạy cả frontend và backend, sử dụng lệnh:
  ```sh
  npm run start:all
  ```
- URL truy cập:
  - Backend (Swagger API docs): [http://localhost:3000/api-docs/#/](http://localhost:3000/api-docs/#/)
  - Frontend: [http://localhost:9000](http://localhost:9000)
