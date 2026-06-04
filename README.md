<div align="center">

# NU SEED (ระบบติดตามโครงการ)

A comprehensive Project & Facility Management Platform built with React, Node.js, and PostgreSQL.

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![React](https://img.shields.io/badge/React_18-61DAFB?logo=react&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?logo=tailwindcss&logoColor=white)

</div>

---

## What is this?

**NU SEED** เป็นระบบติดตามโครงการ (Project Management System) ที่ออกแบบมาเพื่อบริหารจัดการกิจกรรม โครงการ และเอกสารต่างๆ ภายในมหาวิทยาลัยนเรศวร โดยมีระบบจัดการสิทธิ์ผู้ใช้งาน (Role-based) ที่แบ่งแยกพอร์ทัลการใช้งานอย่างชัดเจนสำหรับผู้บริหาร พนักงาน (ผู้รับผิดชอบโครงการ) และผู้เข้าร่วมโครงการ

โปรเจกต์นี้ถูกพัฒนาขึ้นเพื่อให้เห็นภาพรวมของการจัดการงาน (Tasks), การติดตามความคืบหน้าของโครงการ, การจัดการทีม, และการประเมินผลโครงการจบในที่เดียว

## 🔐 Role-Based Portals

ระบบถูกแบ่งออกเป็น 3 Workspace หลักตามสิทธิ์การเข้าใช้งาน:

| Role | Access Level | Description |
|------|--------|-------------|
| **Executive** | `/executive/*` | ผู้บริหาร — ดูภาพรวมสถิติโครงการทั้งหมด ผลตอบรับ (Feedback) และงบประมาณ |
| **Employee** | `/employee/*` | พนักงาน/ผู้รับผิดชอบโครงการ — สร้างและจัดการกิจกรรม แจกจ่ายงาน จัดการทีมและผู้เข้าร่วม และตรวจสอบเอกสาร |
| **Participant**| `/participant/*` | ผู้เข้าร่วมโครงการ — ดูรายละเอียดโครงการที่เข้าร่วม อัปโหลดเอกสาร ติดตามงานของตนเอง และส่งแบบประเมิน |

## 🚀 Features

### สำหรับพนักงาน (Employee / PM)
- **Dashboard** — สรุปจำนวนโครงการที่รับผิดชอบ, ความคืบหน้า, ผู้เข้าร่วม และงานเร่งด่วน
- **Activity & Project Management** — สร้างกิจกรรมใหม่, กำหนดช่วงเวลา, และติดตามสถานะ (เปิดรับสมัคร, กำลังดำเนินการ, ฯลฯ)
- **Task Assignment** — แตกงานย่อย (Tasks), มอบหมายให้ทีม, กำหนดความสำคัญ (Priority) และวันครบกำหนด
- **Document Management** — ระบบจัดการเอกสารแนบโครงการและเอกสารที่ผู้เข้าร่วมอัปโหลด
- **Team & Participants** — จัดการกลุ่มผู้เข้าร่วมโครงการ อนุมัติและตรวจสอบสถานะ

### สำหรับผู้เข้าร่วม (Participant)
- **My Projects** — ดูโครงการที่ตนเองลงทะเบียนไว้และติดตามความคืบหน้าของทีม
- **Task Board** — รับทราบงานที่ต้องทำ ส่งงาน และอัปเดตสถานะงาน
- **Document Hub** — อัปโหลดเอกสารที่จำเป็นสำหรับโครงการ
- **Feedback** — ทำแบบประเมินผลหลังจบโครงการ

### สำหรับผู้บริหาร (Executive)
- **Executive Dashboard** — ดูสถิติรวมของมหาวิทยาลัย โครงการที่กำลังดำเนินอยู่ และอัตราการเข้าร่วม
- **Feedback & Insights** — สรุปผลความพึงพอใจและข้อเสนอแนะจากผู้เข้าร่วมโครงการ

## 💻 Tech Stack

| Layer | Technology |
|-------|------|
| **Frontend** | React 18, Vite, React Router |
| **Styling** | Tailwind CSS, Lucide Icons |
| **Backend** | Node.js, Express.js |
| **Database** | PostgreSQL (รันผ่าน Docker) |
| **Authentication**| JWT (JSON Web Tokens), bcryptjs |

## ⚙️ Getting Started (Local Development)

### Prerequisites
- [Node.js](https://nodejs.org/) (v18 หรือใหม่กว่า)
- [Docker Desktop](https://docs.docker.com/get-docker/) (สำหรับรันฐานข้อมูล)

### Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Nokpednam/nu-seed-facility-management.git
   cd nu-seed-facility-management
   ```

2. **รันระบบผ่าน Script** (แนะนำสำหรับเริ่มต้นครั้งแรก)
   รันคำสั่งสำหรับติดตั้ง Dependencies ทั้งหมด, จำลองฐานข้อมูล PostgreSQL, และสตาร์ทเซิร์ฟเวอร์
   ```bash
   ./start.sh
   ```

3. **ข้อมูลสำหรับล็อกอิน (Demo Data)**
   รหัสผ่านสำหรับทุกบัญชีคือ: `password123`
   - **Executive**: `exec@demo.nu.seed` 
   - **Employee**: `somchai@demo.nu.seed`
   - **Participant**: `piya@demo.nu.seed`

## 📦 Manual Setup (กรณีไม่ใช้ Script)

หากต้องการรันคำสั่งทีละขั้นตอน:

```bash
# 1. จำลองฐานข้อมูล
docker compose up -d

# 2. ตั้งค่า Backend
cd backend
cp .env.example .env
npm install
node scripts/init-demo-db.js  # สร้างตารางและข้อมูลจำลอง
npm run start                 # รัน Backend (Port 5000)

# 3. ตั้งค่า Frontend
cd ../frontend
cp .env.example .env
npm install
npm run dev                   # รัน Frontend (Port 5173)
```

## 🏗 Architecture & Scripts

ระบบประกอบไปด้วยโฟลเดอร์หลักดังนี้:
- `frontend/` — โค้ดส่วนหน้าเว็บแอปพลิเคชัน (React)
- `backend/` — API เซิร์ฟเวอร์ (Express)
- `database/` — ไฟล์ SQL สำหรับการสร้างตารางและ Seed ข้อมูลเดโม
- `scripts/` — สคริปต์สำหรับนักพัฒนาเพื่อรันทดสอบระบบและจัดการฐานข้อมูล
