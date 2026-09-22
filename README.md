# MzanziFlow

*A South African Student Productivity & Collaboration Platform*

**Repository:** https://github.com/021Luvelle/MzanziFlow

**Module:** Open Source Code (IIE) — Portfolio of Evidence, Part 2: App Prototype Development
**Student:** Smangaliso (ST10092489)

## Current Build Status

This repository currently contains **Stage 1 of the Part 2 build only**: the
offline-first data layer.

**Implemented and verified:**
- Room entities, DAOs, and database class (Android/Kotlin) — `android/app/src/main/java/com/mzanziflow/data/local/`
- Express app + MongoDB config + Firebase Admin config (Node.js) — `server/`
- Mongoose models mirroring the Room entities — `server/src/models/`
- `GET /api/health` verified returning `200 OK`
- Mongoose schema validation verified against valid/invalid data

**Not yet implemented** (required by the Part 2 assessment brief):
- Authentication (Firebase Auth, JWT middleware, Login/Register UI)
- Task/Project/Habit CRUD endpoints and screens
- Offline sync (WorkManager, conflict resolution)
- Settings, theming, multi-language support
- Notifications (FCM)
- Unit/instrumentation tests
- GitHub Actions CI/CD
- Video demonstration

See [`docs/traceability-matrix.md`](docs/traceability-matrix.md) for the
full requirement-by-requirement status.

## Video Presentation

*Not yet recorded — add the link here once available. A README without this
link does not meet the submission brief's requirement.*

## AI Tool Usage

*Part 2 AI Tool Usage write-up to be added — see Part 1's write-up
(`3_AI_Tool_Usage_Write_Up.docx`) for the required format.*

## Running the server locally

```bash
cd server
cp .env.example .env   # then fill in your own MongoDB Atlas / Firebase values
npm install
npm run dev
```

## Running the Android app

Open `android/` in Android Studio. Note: only the data layer (Room) exists
so far — there is no UI or ViewModel layer yet to run on a device/emulator.
