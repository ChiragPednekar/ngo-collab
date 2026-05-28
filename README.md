NGO Hub - SaaS Platform for NGO & Volunteer Collaboration
NGO Hub is a multi-tenant SaaS application designed to connect Non-Governmental Organizations (NGOs) with passionate volunteers, facilitate compliance and verification procedures, and streamline collaboration between NGOs on large-scale social projects.

🚀 Project Overview
NGO Hub simplifies the operations of non-profits and volunteers by providing a unified workspace:

For Volunteers: An interactive workspace with skill-based profile setup, points-based gamification, and automated digital certificate generation upon completing volunteer work.
For NGOs: A management console to host events, coordinate with team members, propose partnerships with other NGOs, track volunteer applications, and complete legal verification procedures.
For Admins: A centralized dashboard to verify new organizations and manage overall platform integrity.
✨ Features
🔐 1. Authentication & Custom Role Dashboards
Role-Based Access Control (RBAC): Tailored views and controls for Volunteers, NGOs, and Admins.
Secure registration and login workflows utilizing JWT authentication and Bcrypt hashing.
📋 2. Compliance & Verification Workflows
Legal Form Checklists: Step-by-step workflows to register as a Trust, Society, or Section 8 Company.
Aadhaar e-KYC Verification: Built-in simulated e-KYC flow for validating volunteer profiles.
Document Manager: Secure legal document upload and verification tracking for admin approval.
📅 3. Event & Volunteer Lifecycle Management
Event Creation: NGOs can publish events detailing location, required skills, dates, and volunteer requirements.
Application Flow: Volunteers apply to events → NGOs approve/reject candidates → Attend events → Log volunteer hours.
Smart Attendance: NGOs record volunteer attendance to award points and auto-generate certificates.
🤝 4. NGO-to-NGO Collaboration Hub
Dedicated workflow for sending and receiving collaboration proposals for joint campaigns.
Status tracker for all ongoing, pending, and past partnerships.
💬 5. Direct Messaging System
Secure live chat module allowing volunteers and NGO representatives to communicate, clarify event details, or negotiate project partnerships.
📢 6. Social Feed & Engagement
Interactive community feed where verified NGOs can publish text/image updates.
Comment threads and NGO-following mechanism to keep volunteers updated.
📊 7. Analytics Dashboard
Platform-wide statistics for administrators.
Detailed metrics for NGOs showing active events, total volunteers engaged, and total logged volunteer hours.
🛠️ Tech Stack
Frontend
Framework: Next.js (v16.2) (App Router)
Library: React (v19)
Styling: Tailwind CSS (v4) with PostCSS
State Management: Zustand
Data Fetching: TanStack React Query (v5) & Axios
Icons: Lucide React
Backend
Framework: NestJS (v11)
ORM: Prisma ORM (v6)
Database: PostgreSQL
Authentication: Passport.js (JWT Strategy) & Bcrypt
File Upload: Multer
⚙️ Installation & Setup
Ensure you have Node.js (v18+), npm (v9+), and Docker installed on your system.

Option A: The Quick Way (Monorepo Workspace Scripts)
You can run and seed everything directly from the root directory:

Install Dependencies (installs all packages for both frontend & backend):

bash


npm install
Start the Database:

bash


npm run db:up
Initialize Schema & Seed Database: This runs database migrations, generates the Prisma client, and seeds test accounts:

bash


npm run db:setup
Run the Development Servers: Launches both Next.js frontend (on port 3002) and NestJS backend (on port 3001) concurrently:

bash


npm run dev
Option B: Manual Setup (Step-by-Step)
If you prefer running services in separate terminals:

1. Setup the Database
bash


docker-compose up -d
2. Setup & Run the Backend
bash


cd backend
npm install
npx prisma db push
npx prisma generate
npm run prisma:seed
npm run start:dev
The Backend API will be available at http://localhost:3001

3. Setup & Run the Frontend
bash


cd ../frontend
npm install
npm run dev
The Frontend Web App will be available at http://localhost:3002

🔑 Pre-Seeded Test Accounts
You can log in to the platform using these pre-seeded roles to explore different workflows:

Role	Email	Password
Admin	admin@ngohub.com	password123
NGO Profile	ngo@example.com	password123
Volunteer Profile	volunteer@example.com	password123
📸 Screenshots
Screenshot assets can be saved under frontend/public/screenshots/ or assets/ and linked as follows:

markdown


![Landing Page](frontend/public/screenshots/landing.png)
![NGO Dashboard](frontend/public/screenshots/dashboard.png)
![Community Feed](frontend/public/screenshots/feed.png)
![Direct Messages](frontend/public/screenshots/chat.png)
📦 Folder Structure


ngo-collab/
├── backend/                  # NestJS API Server
│   ├── prisma/               # Database Schema, Migrations, and Seeds
│   │   ├── migrations/       # SQL Migrations
│   │   ├── schema.prisma     # Prisma Models
│   │   └── seed.ts           # Seeding Script for Initial Data
│   ├── src/                  # NestJS Source Code
│   │   ├── analytics/        # Platform & NGO Analytics module
│   │   ├── auth/             # Authentication & Guards
│   │   ├── certificates/     # Digital Certificate Issuance
│   │   ├── chat/             # Direct Chat controllers & services
│   │   ├── collaborations/   # NGO-to-NGO partnership logic
│   │   ├── events/           # Events & Volunteer Applications
│   │   ├── feed/             # Community social posts & comments
│   │   ├── legal/            # Legal drafting compliance checks
│   │   ├── ngo/              # NGO profiles & verification state
│   │   ├── notifications/    # Notifications & Alerts
│   │   ├── prisma/           # Prisma client instantiation
│   │   ├── team/             # NGO team management
│   │   └── users/            # Profile endpoints
│   └── package.json          # Backend Node scripts & dependencies
├── frontend/                 # Next.js Web App
│   ├── app/                  # Next.js App Router folders
│   │   ├── (auth)/           # Authentication layout & pages (Login, Register)
│   │   ├── (dashboard)/      # User dashboards (analytics, events, team, legal)
│   │   ├── certificate/      # Dynamic Certificate Viewer page
│   │   ├── chat/             # Chat UI and WebSocket/HTTP client
│   │   ├── feed/             # Community feed
│   │   ├── ngo/              # NGO details view
│   │   ├── ngos/             # Directory list of all NGOs
│   │   ├── pricing/          # Subscription pricing options
│   │   ├── profile/          # User profile view and settings
│   │   └── lib/              # Client API configurations (Axios Interceptors)
│   ├── components/           # Reusable UI Components
│   └── package.json          # Frontend Node scripts & dependencies
├── docker-compose.yml        # PostgreSQL service definition
├── package.json              # Monorepo Workspace & unified dev commands
└── README.md                 # Project README
🔮 Future Improvements
WebSockets Integration: Transition the direct message chat and notification pipelines to WebSockets (NestJS Gateways & Socket.io) for real-time instantaneous responses.
Real e-KYC Sandbox Integration: Replace simulated Aadhaar checks with authentic government sandboxes or Digilocker SDKs.
Interactive Maps: Render interactive Leaflet or Google maps showing NGO hubs and locations of volunteering events nearby.
QR Code Verification: Include verifiable cryptographic QR codes on volunteer certificates to permit verification by employers/universities.
Secure Payment Gateway: Add Stripe or Razorpay for subscriptions or micro-donations directly targeting specific causes.
AI-driven Recommendations: Implement matchmaking algorithms matching volunteer skills and location details directly to nearby high-priority events.
