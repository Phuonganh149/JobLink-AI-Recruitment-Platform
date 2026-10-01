# JobLink-AI-Recruitment-Platform

# 🚀 JobLink – Nền Tảng Tuyển Dụng Nhân Sự Tích Hợp AI

![JobLink Banner](https://img.shields.io/badge/JobLink-AI%20Recruitment%20Platform-0056b3?style=for-the-badge&logo=rocket)
![Version](https://img.shields.io/badge/version-1.0.0-green?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/status-Production--Ready-brightgreen?style=for-the-badge)

> **JobLink** là nền tảng tuyển dụng nhân sự toàn diện, kết nối thông minh giữa **Ứng viên**, **Doanh nghiệp** và **Quản trị viên**, tích hợp hệ sinh thái AI microservice giúp tự động hóa quá trình xử lý hồ sơ và gợi ý việc làm.

---

## 📌 Bảng Mục Lục
1. [Tính Năng Nổi Bật](#-tính-năng-nổi-bật)
2. [Kiến Trúc Hệ Thống](#-kiến-trúc-hệ-thống)
3. [Công Nghệ Sử Dụng](#-công-nghệ-sử-dụng)
4. [Cấu Trúc Thư Mục](#-cấu-trúc-thư-mục)
5. [Hướng Dẫn Cài Đặt & Chạy Cục Bộ](#-hướng-dẫn-cài-đặt--chạy-cục-bộ)
6. [Quy Trình Phát Triển Git & Phân Công](#-quy-trình-phát-triển-git--phân-công)
7. [Đóng Góp & Giấy Phép](#-đóng-góp--giấy-phép)

---

## ✨ Tính Năng Nổi Bật

### 👤 1. Dành Cho Ứng Viên (Candidate)
* **Quản lý Tài khoản & Hồ sơ:** Đăng ký/đăng nhập an toàn, cập nhật hồ sơ năng lực cá nhân, upload CV dạng PDF/DOCX và avatar.
* **Tìm kiếm & Ứng tuyển:** Tìm kiếm, lọc công việc nâng cao, lưu việc làm yêu thích và ứng tuyển nhanh chóng.
* **Theo dõi Realtime:** Cập nhật trạng thái hồ sơ ứng tuyển theo thời gian thực.

### 🏢 2. Dành Cho Doanh Nghiệp (Company)
* **Định danh & Đăng tin:** Quản lý hồ sơ doanh nghiệp, chủ động đăng, sửa, đóng tin tuyển dụng.
* **Applicant Pipeline:** Quản lý quy trình tuyển dụng theo 4 giai đoạn: `Mới ứng tuyển` ➔ `Đang xem xét` ➔ `Phỏng vấn` ➔ `Kết quả`.
* **Kho CV & Dịch vụ:** Tìm kiếm kho CV tiềm năng; tích hợp thanh toán VietQR cho các gói dịch vụ (Free, Basic, Pro, Enterprise).

### 🛡️ 3. Dành Cho Quản Trị Viên (Admin Control Panel)
* **Kiểm duyệt & Giám sát:** Phê duyệt/từ chối doanh nghiệp mới; khóa/mở khóa tài khoản vi phạm.
* **Dữ liệu & Thống kê:** Quản lý tin tuyển dụng và danh mục 8 ngành nghề cốt lõi; báo cáo tổng quan số lượng ứng viên, doanh nghiệp, tin đăng.

### 🤖 4. Hệ Sinh Thái AI Microservice
* **AI Matching:** Chấm điểm độ phù hợp giữa CV và Job Description (0 - 100%) dựa trên thuật toán TF-IDF.
* **CV Analyzer:** Tự động trích xuất và phân tích kỹ năng, kinh nghiệm từ file CV gốc.
* **Recommendation System:** Thuật toán gợi ý việc làm được cá nhân hóa cho từng ứng viên.
* **AI Chatbot (RAG):** Trợ lý ảo tư vấn tự động dựa trên FAQ nội bộ và dữ liệu Database.

---

## 🏗 Kiến Trúc Hệ Thống

Hệ thống được thiết kế theo kiến trúc Microservice đa tầng (Zone-based Architecture):

```text
+-----------------------------------------------------------------------+
|  Zone 1: Client                                                       |
|  - Frontend: Responsive HTML5 / CSS3 / JavaScript thuần               |
+------------------------------------+----------------------------------+
                                     | REST API
                                     v
+------------------------------------+----------------------------------+
|  Zone 2: Core Server (Port 3000)                                      |
|  - Node.js + Express Framework (JWT Authentication, bcrypt)           |
+------------------+---------------------------------+------------------+
                   |                                 |
                   v                                 v
+------------------+------------------+   +----------+------------------+
| Zone 3: Database & Storage          |   | Zone 4: AI Microservice     |
| - Supabase PostgreSQL Database      |   |   (Port 5000)                |
| - Cloud Storage (CV/Avatar files)   |   | - Flask AI Engine            |
+-------------------------------------+   | - Groq Cloud API (LLM)     |
                                          +-----------------------------+
---

#** 🛠 Công Nghệ Sử Dụng**
- Frontend: HTML5, CSS3, JavaScript (Vanilla JS - No Framework).

- Backend Core: Node.js, Express.js, JWT, bcrypt.

- AI Engine: Python, Flask, Groq Cloud API (LLM Provider), TF-IDF Algorithm.

- Database & Storage: Supabase PostgreSQL, Cloud Storage (Signed URLs).

- Version Control & CI/CD: Git, GitHub / GitLab, Hosting Free Tier.

# JobLink-AI-Recruitment-Platform/
├── core-server/             # Node.js Express Backend (Zone 2)
│   ├── config/              # Cấu hình Database & Environment
│   ├── controllers/         # Logic điều hướng API
│   ├── middlewares/         # JWT Auth & Upload middleware
│   ├── models/              # Truy vấn dữ liệu Supabase PostgreSQL
│   ├── routes/              # Khai báo REST API endpoints
│   └── server.js            # Entry point chính của Core Server
├── ai-service/              # Flask AI Microservice (Zone 4)
│   ├── app.py               # Entry point ứng dụng Flask
│   ├── modules/
│   │   ├── matching.py      # Thuật toán TF-IDF AI Matching
│   │   ├── analyzer.py      # Trích xuất dữ liệu CV
│   │   └── chatbot_rag.py   # AI Chatbot RAG với Groq Cloud API
│   └── requirements.txt     # Các thư viện Python cần thiết
├── client/                  # Frontend Web Interface (Zone 1)
│   ├── css/                 # Style sheets (responsive)
│   ├── js/                  # Client-side scripts & API calls
│   ├── candidate.html       # Portal Ứng viên
│   ├── company.html         # Portal Doanh nghiệp
│   ├── admin.html           # Admin Control Panel
│   └── index.html           # Trang chủ JobLink
├── .gitignore
├── LICENSE
└── README.md

---
# ⚡ Hướng Dẫn Cài Đặt & Chạy Cục Bộ
1. Yêu Cầu Tiền Đề
Node.js: v18.x trở lên

Python: v3.9 trở lên

Git
# 2. Cài Đặt Core Server (Node.js)
Bash
cd core-server
npm install
# Tạo file .env và điền thông số cấu hình Supabase, JWT Secret
npm start
Server sẽ chạy tại: http://localhost:3000

3. Cài Đặt AI Microservice (Flask)
Bash
cd ai-service
python -m venv venv
# On Windows: venv\Scripts\activate
# On macOS/Linux: source venv/bin/activate
pip install -r requirements.txt
python app.py
