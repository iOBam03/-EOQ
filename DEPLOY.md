# ขั้นตอน Deploy EOQ Dashboard ขึ้น GitHub Pages

> URL ที่จะได้: `https://kittipong-yimlamai.github.io/eoq-dashboard/`

มี 3 ขั้นตอนหลัก ใช้เวลาประมาณ 5 นาที

---

## ขั้นตอนที่ 1 — สร้าง Repository บน GitHub (2 นาที)

1. เปิด https://github.com/new ในเบราว์เซอร์
2. ตั้งค่าดังนี้:
   - **Owner**: `kittipong-yimlamai` (เลือก account ของคุณ)
   - **Repository name**: `eoq-dashboard` (ตั้งตามนี้เป๊ะ)
   - **Description**: `EOQ Dashboard — การวิเคราะห์ปริมาณการสั่งซื้อที่เหมาะสม`
   - **Visibility**: ✅ **Public** (จำเป็นสำหรับ GitHub Pages ฟรี)
   - ❌ **ไม่ติ๊ก** "Add a README file"
   - ❌ **ไม่ติ๊ก** "Add .gitignore"
   - ❌ **ไม่ติ๊ก** "Choose a license"
3. กดปุ่ม **Create repository** (สีเขียว)

---

## ขั้นตอนที่ 2 — สร้าง Personal Access Token (PAT) (2 นาที)

1. เปิด https://github.com/settings/tokens?type=beta (GitHub Fine-grained tokens)
   - หรือไปที่ https://github.com/settings/tokens ถ้าใช้ classic tokens
2. กด **Generate new token** (เลือก Fine-grained หรือ Classic ก็ได้)

### ถ้าใช้ Fine-grained token (แนะนำ):
- **Token name**: `eoq-dashboard-deploy`
- **Expiration**: 7 days
- **Resource owner**: `kittipong-yimlamai`
- **Repository access**: `Only select repositories` → เลือก `eoq-dashboard`
- **Permissions → Repository permissions**:
  - `Contents`: **Read and write**
  - `Pages`: **Read and write** (สำหรับเปิด GitHub Pages)
  - `Metadata`: **Read-only** (default)
- กด **Generate token**
- **คัดลอก Token ที่ขึ้นต้นด้วย `github_pat_...` เก็บไว้** (จะแสดงครั้งเดียว)

### ถ้าใช้ Classic token (ง่ายกว่า):
- **Note**: `eoq-dashboard-deploy`
- **Expiration**: 7 days
- **Scopes**: ติ๊ก ✅ `repo` (อย่างเดียวพอ)
- กด **Generate token**
- **คัดลอก Token ที่ขึ้นต้นด้วย `ghp_...` เก็บไว้**

---

## ขั้นตอนที่ 3 — ส่ง Token กลับมา (1 นาที)

หลังจากได้ Token แล้ว ให้ **วาง Token กลับมาในแชท Claude** พร้อมข้อความ:

```
token: github_pat_xxxxxxxxxxxxxxxxx
```

ผมจะ:
1. Push โค้ดขึ้น repo ของคุณ
2. เปิด GitHub Pages อัตโนมัติ
3. รอ 1-2 นาทีให้ GitHub build
4. ส่ง **ลิงก์สาธารณะ** ที่พร้อมแชร์ให้คนอื่น

---

## หลัง Deploy เสร็จ

คุณจะได้ URL: **`https://kittipong-yimlamai.github.io/eoq-dashboard/`**

- ✅ แชร์ลิงก์นี้ให้ใครก็ได้ — เปิดได้ทุกที่ ไม่ต้องล็อกอิน
- ✅ ใช้งานได้บนมือถือ/แท็บเล็ต/คอม
- ✅ ไม่หายไปตราบเท่าที่ repo ยังอยู่
- ✅ ฟรี ไม่มีโฆษณา ไม่มี tracking
- ✅ ถ้าอยากอัปเดตไฟล์ → แก้ `index.html` แล้ว commit + push ใหม่ได้เลย

---

## ⚠️ ความปลอดภัย

- Token ที่ได้มีสิทธิ์แค่ write ไฟล์ใน repo `eoq-dashboard` (ถ้าใช้ Fine-grained)
- แนะนำให้ตั้ง expiration ไม่นาน (7 วัน) แล้วลบทิ้งหลัง deploy เสร็จ
- ลบ token ได้ที่ https://github.com/settings/tokens
