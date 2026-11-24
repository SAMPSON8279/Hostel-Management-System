# Baseline System Audit (`v1.0-baseline`)

## 1. Repository & Stack Overview
- **Upstream Source:** `Ananth1082/Hostel-Management-System`
- **Baseline Tag:** `v1.0-baseline`
- **Frontend:** React + TypeScript + Vite (`Frontend/`, port `5173`)
- **Backend:** Node.js + Express + JavaScript (`Backend/`, port `8080`)
- **Database:** PostgreSQL with Sequelize ORM (`Hostel Management System`)

## 2. Existing Functionalities (`v1.0`)
- **Authentication & Seed Data:** Pre-populated roles (`user`, `admin`, `mess-admin`, `clean-admin`), users, rooms (`101`–`122` across 4 floors), and weekly mess menus via `PopulateDB/init.js`.
- **Rooms Layout View (`/user/rooms`):** Interactive floor diagram displaying room numbers and a room details card.
- **Backend Route Modules:** Scaffolding exists for `auth`, `user`, `room`, `menu`, `coupon`, `attendance`, `notification`, and `roomservice`.

## 3. Identified Technical Debt & Defects
1. **Cross-Platform Import Bug:** `Frontend/src/Components/hostel-admin/RoomsLayout.tsx` imports `./RoomInfo` instead of `./Roominfo.tsx`, causing Vite compilation to fail on case-sensitive setups.
2. **Incomplete Frontend Views:** Secondary navigation pages render blank or lack wired UI workflows; leftover template labels (e.g., `+ Add Product`) appear in the Rooms view.
3. **Destructive Database Sync:** `Backend/server.js` executes `db.sequelize.sync({ force: true })` on startup, dropping and recreating all tables on every restart without versioned migrations.
4. **Hardcoded Secrets:** Database password and JWT secret are stored directly in `Backend/app/config/` instead of environment variables.
5. **Unfinished Author Backlog (`Backend/Note.txt`):** Explicitly notes remaining work: `Update roles`, `Create room-service`, and `filter feature`.
6. **Zero Automated Tests & Untyped Backend:** No unit/integration test suite exists, and backend controllers/models lack TypeScript type checking.

## 4. Baseline Metrics (`v1.0`)
- **Backend Language:** 100% untyped JavaScript
- **Automated Tests:** 0
- **Versioned DB Migrations:** 0
- **Dependency Audit:** 16 vulnerabilities in `Backend`, 32 in `Frontend`