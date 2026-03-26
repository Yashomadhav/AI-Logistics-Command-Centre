# 🚚 **AI Logistics Command Center**

**Enterprise Operations Intelligence Platform** for logistics teams to monitor delivery stations, predict risks, manage incidents, and get AI-powered recommendations.

[![Next.js](https://img.shields.io/badge/Next.js-14-black.svg)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.5-blue.svg)](https://typescriptlang.org)
[![Prisma](https://img.shields.io/badge/Prisma-5.15-4FD1C7.svg)](https://prisma.io)
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3.4-38bdf8.svg)](https://tailwindcss.com)

## 🎯 **Business Problem**

Logistics operations teams struggle with:
- **Fragmented data** from scheduling sheets, delay logs, route summaries
- **Reactive firefighting** - discover staffing gaps or delays too late
- **No AI insights** - manual analysis of risks/root causes/recommendations
- **Poor visibility** across stations/regions for managers/analysts

**This platform solves it** with real-time dashboards, predictive risk scoring, AI copilot, and automated data ingestion.

## ✨ **Key Features**

| Feature | Description |
|---------|-------------|
| **Executive Dashboard** | KPIs (OTD %, incidents, staffing risks), trend charts, priority alerts |
| **Station Management** | List/detail w/ metrics trends, incidents timeline, AI summaries |
| **Incident Management** | CRUD w/ severity/status/assignment, categorization |
| **Risk Analysis** | Staffing gaps, route congestion, dispatch delays w/ heatmaps |
| **Data Upload** | CSV/Excel drag-drop, template validation, preview, normalized storage |
| **AI Copilot** | Natural language queries → structured insights (mock→real LLM) |
| **Alerts & Reports** | Auto-generated notifications, exportable summaries |
| **Role-Based Access** | Admin/Manager/Analyst permissions |

## 🏗️ **Architecture**

```
├── app/                 # Next.js 14 App Router
│   ├── api/auth/        # NextAuth routes
│   ├── dashboard/       # Protected routes (upload, copilot...)
│   └── layout.tsx       # Providers + theme
├── prisma/              # Normalized logistics schema
│   ├── schema.prisma    # Time-series metrics, relationships
│   └── seed.ts          # 10 stations + realistic data
├── lib/                 # Services
│   ├── db.ts           # Prisma singleton
│   ├── auth.ts         # NextAuth config
│   ├── ai-service.ts   # Mock AI → OpenAI/Groq
│   └── upload-service.ts # CSV/XLSX parser
├── components/          # Shadcn + custom
│   ├── ui/             # Button/Card/Badge...
│   └── dashboard/      # KpiCard...
```

**Data Flow**: Upload → Parse/Validate → UploadRow → Metrics → AI Analysis → Dashboard/Alerts

## 🛠️ **Tech Stack**

- **Frontend**: Next.js 14 (App Router), TypeScript, TailwindCSS, Shadcn/UI, Recharts prep
- **Backend**: Prisma ORM, PostgreSQL, NextAuth (Credentials/JWT)
- **AI**: Mock service (OpenAI/Groq ready)
- **Upload**: PapaParse/XLSX, Zod validation
- **State**: React Hook Form, TanStack prep
- **Deploy**: Vercel/ Railway (Postgres Neon)

## 🚀 **Quick Start**

### 1. Local Development
```bash
# Postgres (Docker)
docker run --name ai-logistics-db -e POSTGRES_PASSWORD=password -p 5432:5432 -d postgres:15

# Setup
cp .env.example .env
# Edit DATABASE_URL=postgresql://postgres:password@localhost:5432/postgres

npm install
npx prisma generate
npx prisma db push
npx prisma db seed  # 10 stations, users, data!

npm run dev
```

### 2. Demo Credentials
```
admin@logistics.com    / admin     → Admin
manager@logistics.com  / manager   → Operations Manager
analyst@logistics.com  / analyst   → Analyst
```

**Live Flow**: Login → Dashboard KPIs → Upload CSV → Preview → AI Copilot → Reports

## 📱 **Screenshots**
*(Add after deploy)*
- Dashboard w/ gradient KPIs, sidebar
- Upload drag-drop + preview table  
- AI structured insights cards

## 🔮 **Future Improvements**

Phase 2:
```
[ ] Real-time WebSockets (alerts/metrics)
[ ] TanStack Table for stations/incidents (filters/pagination)
[ ] Recharts dashboards (OTD trends, risk heatmaps)
[ ] Real LLM integration (OpenAI/Groq)
[ ] PDF/CSV export (reports)
[ ] Mobile PWA
[ ] Multi-tenant (companies)
```

## 📄 **License**
MIT - Built by BLACKBOXAI for logistics excellence!

**Deploy to Vercel**: Connect repo → Postgres Neon → Live in 2min 🚀
