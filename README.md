# Signalist - แพลตฟอร์มติดตามตลาดหุ้นแบบเรียลไทม์

โปรเจกต์นี้เป็นแพลตฟอร์มติดตามตลาดหุ้นที่ทันสมัย พัฒนาด้วย Next.js 15 และ TypeScript ช่วยให้ผู้ใช้งานสามารถติดตามราคาหุ้นแบบเรียลไทม์ ตั้งค่าการแจ้งเตือนส่วนตัว และวิเคราะห์ข้อมูลบริษัทได้อย่างครบถ้วน

## ✨ ฟีเจอร์หลัก

- 🔐 **ระบบ Authentication** - ระบบล็อกอินและสมัครสมาชิกที่ปลอดภัยด้วย Better Auth
- 📊 **แดชบอร์ดตลาดหุ้น** - แสดงภาพรวมตลาด, Heatmap, และข่าวสารตลาดหุ้นแบบเรียลไทม์
- 🔍 **ค้นหาหุ้น** - ค้นหาหุ้นด้วย Command Palette (⌘K / Ctrl+K)
- 📈 **รายละเอียดหุ้น** - แสดงกราฟแบบต่างๆ, การวิเคราะห์ทางเทคนิค, โปรไฟล์บริษัท และข้อมูลการเงิน
- ⭐ **Watchlist** - เพิ่มหุ้นที่สนใจเข้า Watchlist ส่วนตัว
- 🔔 **การแจ้งเตือน** - ตั้งค่าการแจ้งเตือนราคาหุ้น (Coming Soon)
- 📱 **Responsive Design** - ใช้งานได้ลื่นไหลทุกอุปกรณ์
- 🌙 **Dark Mode** - รองรับธีมมืดโดยค่าเริ่มต้น

## 🛠️ เทคโนโลยีที่ใช้

### Frontend
- **Next.js 15** - React Framework รุ่นล่าสุด
- **TypeScript** - Type-safe JavaScript
- **Tailwind CSS v4** - Utility-first CSS Framework
- **Radix UI** - Accessible UI Components
- **React Hook Form** - Form Management
- **Sonner** - Toast Notifications

### Backend & Database
- **MongoDB** - NoSQL Database
- **Mongoose** - MongoDB Object Modeling
- **Better Auth** - Modern Authentication

### External APIs
- **TradingView Widgets** - กราฟและข้อมูลตลาดหุ้นแบบเรียลไทม์
- **Finnhub API** - ข้อมูลหุ้นและข่าวสาร
- **Inngest** - Event-driven Background Jobs

## 📋 ข้อกำหนดเบื้องต้น

- Node.js 18+ 
- MongoDB Database
- Finnhub API Key (ฟรี)
- Inngest Account (สำหรับ Background Jobs)

## 🚀 การติดตั้ง

1. **Clone Repository**
```bash
git clone <repository-url>
cd signalist
```

2. **ติดตั้ง Dependencies**
```bash
npm install
# หรือ
yarn install
# หรือ
pnpm install
```

3. **ตั้งค่า Environment Variables**

สร้างไฟล์ `.env.local` และเพิ่มค่าต่อไปนี้:

```env
# Database
MONGODB_URI=your_mongodb_connection_string

# Better Auth
BETTER_AUTH_SECRET=your_secret_key_here
BETTER_AUTH_URL=http://localhost:3000

# Finnhub API
NEXT_PUBLIC_FINNHUB_API_KEY=your_finnhub_api_key

# Inngest
INNGEST_EVENT_KEY=your_inngest_event_key
INNGEST_SIGNING_KEY=your_inngest_signing_key
```

4. **ทดสอบการเชื่อมต่อ Database**
```bash
node scripts/test-db.mjs
```

5. **เริ่มต้น Development Server**
```bash
npm run dev
```

6. **เปิดเบราว์เซอร์**
```
http://localhost:3000
```

## 📁 โครงสร้างโปรเจกต์

```
signalist/
├── app/                          # Next.js App Router
│   ├── (auth)/                   # Authentication Routes
│   │   ├── sign-in/             # หน้าเข้าสู่ระบบ
│   │   └── sign-up/             # หน้าสมัครสมาชิก
│   ├── (root)/                   # Protected Routes
│   │   ├── page.tsx             # หน้าแดชบอร์ด
│   │   └── stocks/[symbol]/     # หน้ารายละเอียดหุ้น
│   ├── api/                      # API Routes
│   └── globals.css              # Global Styles
├── components/                   # React Components
│   ├── forms/                   # Form Components
│   ├── ui/                      # UI Components (shadcn/ui)
│   ├── Header.tsx
│   ├── SearchCommand.tsx
│   ├── TradingViewWidget.tsx
│   └── WatchlistButton.tsx
├── database/                     # Database Configuration
│   ├── models/                  # Mongoose Models
│   └── mongoose.ts              # Database Connection
├── hooks/                        # Custom React Hooks
├── lib/                          # Utility Functions
│   ├── actions/                 # Server Actions
│   ├── better-auth/             # Auth Configuration
│   ├── inngest/                 # Background Jobs
│   └── constants.ts             # Constants
├── types/                        # TypeScript Type Definitions
└── middleware.ts                 # Next.js Middleware
```

## 🎯 การใช้งาน

### การสมัครสมาชิก
1. คลิกที่ "Sign Up" บนหน้าแรก
2. กรอกข้อมูลส่วนตัวและความสนใจในการลงทุน
3. ยืนยัน Email (ถ้าเปิดใช้งาน)

### การค้นหาหุ้น
- กด `⌘K` (Mac) หรือ `Ctrl+K` (Windows/Linux) 
- หรือคลิกที่ "Search" ในเมนู
- พิมพ์ชื่อหุ้นหรือสัญลักษณ์ที่ต้องการ

### การเพิ่มหุ้นเข้า Watchlist
1. ไปที่หน้ารายละเอียดหุ้นที่สนใจ
2. คลิกปุ่ม "Add to Watchlist"
3. ดูรายการหุ้นที่บันทึกไว้ได้ที่เมนู "Watchlist"

### การตั้งค่าการแจ้งเตือน (Coming Soon)
1. ไปที่หน้า Watchlist
2. คลิก "Add Alert" ที่หุ้นที่ต้องการ
3. ตั้งค่าเงื่อนไขการแจ้งเตือน
4. รับการแจ้งเตือนทาง Email

## 🎨 การปรับแต่ง Theme

โปรเจกต์ใช้ Tailwind CSS v4 พร้อม Custom Color Palette:

```css
--color-gray-900: #050505
--color-gray-800: #141414
--color-blue-600: #5862FF
--color-yellow-400: #FDD458
--color-teal-400: #0FEDBE
```

แก้ไขได้ที่ไฟล์ `app/globals.css`

## 🔧 สคริปต์ที่มีให้ใช้

```bash
# Development
npm run dev          # เริ่ม dev server พร้อม Turbopack
npm run build        # Build สำหรับ production
npm run start        # เริ่ม production server
npm run lint         # ตรวจสอบ code ด้วย ESLint

# Database Testing
node scripts/test-db.mjs  # ทดสอบการเชื่อมต่อ MongoDB
```

## 📦 การ Deploy

### Vercel (แนะนำ)
1. Push โค้ดขึ้น GitHub
2. เชื่อมต่อ Repository กับ Vercel
3. ตั้งค่า Environment Variables
4. Deploy!

### Docker
```bash
# Coming Soon
```

## 🤝 การมีส่วนร่วม

หากต้องการมีส่วนร่วมในการพัฒนา:

1. Fork Repository
2. สร้าง Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit การเปลี่ยนแปลง (`git commit -m 'Add some AmazingFeature'`)
4. Push ไปยัง Branch (`git push origin feature/AmazingFeature`)
5. เปิด Pull Request

## 🙏 เครดิต

- **Tutorial**: [JavaScript Mastery - YouTube](https://youtu.be/gu4pafNCXng?si=EISr1w8Z3U4nBcBy)
- **UI Components**: [shadcn/ui](https://ui.shadcn.com/)
- **Icons**: [Lucide React](https://lucide.dev/)
- **Market Data**: [TradingView](https://www.tradingview.com/) & [Finnhub](https://finnhub.io/)
