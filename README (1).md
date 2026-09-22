# MzanziFlow

*A South African Student Productivity & Collaboration Platform*

**Repository:** https://github.com/021Luvelle/MzanziFlow

## Academic Context

| | |
|---|---|
| **Student** | Smangaliso Ngalo |
| **Student Number** | ST10092489 |
| **Institution** | The Independent Institute of Education (IIE) |
| **Module** | Open Source Code |
| **Assessment** | Portfolio of Evidence — Part 2: App Prototype Development |

Part 1 (Research and Planning & Design) was completed and submitted previously and forms the approved specification for this build. This repository contains the Part 2 prototype work.

## Project Overview

MzanziFlow is a planned Android productivity and collaboration application for South African students, designed around task management, shared projects, habit tracking, and an offline-first architecture suited to intermittent connectivity (including load-shedding conditions). The full feature set and rationale are documented in `2_Planning_and_Design_Document.docx`.

## Project Objectives

Based on the approved Part 1 specification, the objectives of MzanziFlow are to:

- Give students a single place to manage tasks, deadlines, and group project work.
- Support collaboration between students on shared projects.
- Encourage consistent study habits through habit tracking.
- Remain usable when connectivity is unreliable, through an offline-first data layer that synchronises when a connection is available.
- Reflect South African student life specifically, rather than being a generic productivity app.

## Current Build Status

**This repository currently reflects Stage 1 of the Part 2 build: the offline-first data layer.** It is an honest, in-progress snapshot rather than a feature-complete prototype. The sections below are written to match what is actually in the repository at this stage.

### Implemented and Verified

| Area | Detail | Location |
|---|---|---|
| Android local data layer | Room entities, DAOs, and database class | `android/app/src/main/java/com/mzanziflow/data/local/` |
| Backend skeleton | Express app with MongoDB and Firebase Admin configuration | `server/` |
| Backend data layer | Mongoose models mirroring the Room entities | `server/src/models/` |
| API | `GET /api/health` — verified returning `200 OK` | `server/` |
| Data validation | Mongoose schema validation verified against valid and invalid input | `server/src/models/` |

### Not Yet Implemented

The following are specified in the Part 1 design but are **not yet built** in this repository:

- Authentication (Firebase Auth, JWT middleware, Login/Register screens)
- Task, Project, and Habit CRUD endpoints and corresponding UI screens
- Offline synchronisation (WorkManager, sync worker, conflict resolution)
- Settings screen, theming, and multi-language support
- Notifications (Firebase Cloud Messaging)
- Unit and instrumentation tests beyond schema validation
- GitHub Actions CI/CD
- A dashboard, navigation, or any other user-facing screen (there is currently no ViewModel or UI layer)

See `docs/traceability-matrix.md` for the full requirement-by-requirement status against the Part 1 specification.

## Key Features

Status key: ✅ Implemented · 🔶 Partially implemented · ⏳ Planned (not yet started)

| Feature | Status |
|---|---|
| Local offline-first data model (Room) | ✅ Implemented |
| Backend data model (Mongoose, mirrors Room) | ✅ Implemented |
| API health check | ✅ Implemented |
| Server-side input validation (schema level) | ✅ Implemented |
| User authentication | ⏳ Planned |
| Task management (create/read/update/delete) | ⏳ Planned |
| Shared projects & collaboration | ⏳ Planned |
| Habit tracking (UI + streak logic) | ⏳ Planned |
| Study Mode (Pomodoro timer) | ⏳ Planned |
| Load-shedding safe mode | ⏳ Planned |
| Offline synchronisation (WorkManager) | ⏳ Planned |
| Settings, theming, multi-language | ⏳ Planned |
| Push/local notifications | ⏳ Planned |

## Technology Stack

Only technologies actually present in the repository are listed here.

**Android**
- Kotlin
- Android Studio / Gradle
- Room (local database, DAOs, entities)

**Backend**
- Node.js
- Express.js
- Mongoose (MongoDB object modelling)
- Firebase Admin SDK (configuration present)

**Database**
- MongoDB Atlas (configured, connection expected via environment variable)

**Other**
- Git / GitHub for version control

Technologies specified in the Part 1 design but not yet present in the codebase (e.g. Retrofit, WorkManager, Firebase Authentication/FCM in the Android client, JWT middleware) are **not listed above** and are tracked instead under Future Enhancements.

## Architecture

The target architecture, per the Part 1 design, is:

```
Android App (MVVM)
     ↓
ViewModel
     ↓
Repository
     ↓
RoomDB (local) / Retrofit (remote)
     ↓
Node.js REST API
     ↓
MongoDB Atlas
```

**What currently exists:** the Room entity/DAO/database layer on the Android side, and the Express + Mongoose + Firebase Admin skeleton on the backend, with a working health-check endpoint. The ViewModel, Repository, Retrofit networking layer, and UI layer have not yet been built, so the architecture above is not yet connected end-to-end.

## Screens / User Interface

No UI layer has been implemented yet — there are currently no Activities, Fragments, Composables, or ViewModels in the Android project, so there are no application screens to screenshot at this stage.

Once screens are implemented, screenshots will be added under `docs/images/` (e.g. `login.png`, `dashboard.png`, `tasks.png`) and referenced here.

## Backend / API

**Verified endpoint:**

| Method | Endpoint | Status |
|---|---|---|
| GET | `/api/health` | ✅ Verified returning `200 OK` |

No other endpoints (task, project, habit, sync, or auth routes) currently exist in the codebase. The endpoint list in the Part 1 design (`/api/tasks`, `/api/projects`, `/api/habits`, `/api/sync`, etc.) represents the target API surface for later stages, not the current state.

## Database

- **Local (Android):** Room database with entities and DAOs mirroring the Part 1 data dictionary (User, Task, Project, Habit).
- **Remote (Backend):** MongoDB Atlas, accessed through Mongoose models that mirror the Room entity structure. Schema-level validation has been implemented and manually verified against both valid and invalid payloads.
- **Firebase:** Firebase Admin SDK is configured on the backend, but no authentication flow currently uses it.

## Offline-First Functionality

The offline-first *data layer* exists (Room on the client, a mirrored schema on the server), but the *synchronisation mechanism* connecting the two does not yet exist. There is no WorkManager sync worker, no `syncStatus` handling in a repository layer, and no conflict-resolution logic implemented yet. This is the next major piece of planned work.

## Testing

| Test type | Status |
|---|---|
| Mongoose schema validation (valid/invalid data) | ✅ Implemented and manually verified |
| API endpoint test (`GET /api/health`) | ✅ Manually verified (200 OK) |
| Android unit tests | ⏳ Not yet implemented |
| Android instrumentation/UI tests | ⏳ Not yet implemented |
| Automated test suite / test runner configuration | ⏳ Not yet implemented |

## GitHub Development

GitHub has been used for:
- Source-code version control (Android and backend code)
- Storing Part 1 and Part 2 assessment documentation
- Tracking project submission history

**GitHub Actions / CI-CD has not yet been configured** for this repository. It is listed under Future Enhancements below.

## Video Presentation

Watch the MzanziFlow Part 2 presentation: https://www.youtube.com/shorts/C9ajtQincaY

> Note: this video should reflect the same Stage 1 progress described in this README. If it demonstrates functionality beyond what is described above, please re-record or re-link once later stages are implemented, so the video and repository stay consistent with each other.

## AI Tool Usage

Claude AI and ChatGPT were used as development-support tools during this assessment (code-generation assistance, debugging support, architectural guidance, and documentation support). See `3_AI_Tool_Usage_Write_Up.docx` (Part 1) and the Part 2 AI Tool Usage document for the full account. AI-assisted output was reviewed, adapted, tested, and integrated by the student; AI did not independently design, test, or submit any part of this project.

## Academic Integrity

AI tools were used as development assistance throughout this assessment. All AI-generated suggestions were reviewed, understood, adapted to project requirements, tested, and integrated by the student. Final technical and design decisions, debugging, and submission were carried out by the student.

## Project Status Summary

| Category | Items |
|---|---|
| **Implemented** | Room data layer (Android), Mongoose data layer + schema validation (backend), Express app skeleton, `GET /api/health` |
| **Partially Implemented** | Backend service skeleton (config present, business-logic routes not yet built) |
| **Future Enhancement / Planned** | Authentication, CRUD endpoints & screens, offline sync, settings/theming/language, notifications, habit tracking UI, Study Mode, load-shedding safe mode, automated testing, CI/CD |

## Repository Structure

```
MzanziFlow/
├── android/                          # Android Studio project (Room data layer only, so far)
├── server/                           # Node.js/Express backend
│   └── src/models/                   # Mongoose models mirroring Room entities
├── docs/
│   └── traceability-matrix.md        # Part 1 requirement → Part 2 implementation status
├── 1_Research_Report.docx
├── 2_Planning_and_Design_Document.docx
├── 3_AI_Tool_Usage_Write_Up.docx      # Part 1 AI Tool Usage write-up
├── MzanziFlow-stage1.zip
├── LICENSE                           # MIT
├── .gitignore
└── README.md
```

## Installation / Setup

### Prerequisites
- Android Studio (recent stable version)
- Node.js and npm
- A MongoDB Atlas account/connection string
- A Firebase project (for the Admin SDK configuration)

### Backend

```bash
cd server
cp .env.example .env   # fill in your own MongoDB Atlas / Firebase values — never commit .env
npm install
npm run dev
```

Required environment variables (see `.env.example`):
```
MONGODB_URI
FIREBASE_PROJECT_ID
FIREBASE_CLIENT_EMAIL
FIREBASE_PRIVATE_KEY
```

### Android

Open `android/` in Android Studio and sync Gradle. Note: only the Room data layer exists at this stage — there is no UI or ViewModel layer yet, so the app cannot currently be run and interacted with on a device or emulator.

## Future Enhancements

The following are planned for subsequent stages, in line with the Part 1 design:

- Firebase Authentication (client) and JWT/Firebase token verification middleware (server)
- Repository and ViewModel layers, connecting Room and Retrofit to a UI
- Task, Project, and Habit screens with full CRUD
- WorkManager-based background synchronisation with `PENDING` / `SYNCED` / `CONFLICT` status handling
- Settings screen: theming, language switching (English, isiZulu, Afrikaans), notification preferences
- Firebase Cloud Messaging integration
- Load-shedding safe mode using a documented API abstraction (no fabricated live data)
- Unit tests (ViewModel, Repository), instrumentation tests, and Retrofit/API tests using mocks
- GitHub Actions workflow for automated lint, test, and build

## Author

**Smangaliso Ngalo**
ST10092489
MzanziFlow — Open Source Code, IIE

## License

MIT — see `LICENSE`.
