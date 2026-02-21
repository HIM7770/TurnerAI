 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
index f44d202e911f8059e8025d34a9d4512f1c7409ab..b6e73399dcddd2c2a2f6ed4e6a6c309d30843155 100644
--- a/README.md
+++ b/README.md
@@ -1,2 +1,75 @@
 # TurnerAI
-TurnerAI is a 3D game bulider
+
+TurnerAI is a browser-based AI-powered 3D game creation platform scaffold inspired by your Genesis Engine AI prompt.
+
+## Tech Stack
+
+- **Frontend:** React + Three.js + WebGL (Vite)
+- **Backend:** Node.js + Express
+- **Security:** JWT auth, Stripe webhook signature validation, project encryption utility
+- **AI Workflow:** queued generation jobs for 3D scenes, game logic, NPC systems, and multiplayer templates
+
+## Implemented Features (Scaffold)
+
+### Core Engine UI
+- Web-based 3D viewport (Three.js)
+- Scene hierarchy panel
+- Inspector panel
+- Asset browser section
+- Lighting/physics controls (UI scaffold)
+- Primitive object rendering, transform visualization
+
+### AI Systems API
+- `POST /api/generate` with generation types:
+  - `scene3d`
+  - `gameLogic`
+  - `npc`
+  - `multiplayerTemplate` (Studio+ only)
+- Job polling endpoint: `GET /api/generate/:jobId`
+- Starter fake generation outputs to unblock UI + workflow integration
+
+### Subscription + Usage Controls
+- Builder / Pro / Studio / Creator Elite tier definitions
+- Generation count tracking per user
+- Monthly generation limits enforced for Builder and Pro
+- Tier-gated exports and multiplayer generation
+
+### Dashboard + Exports
+- `GET /api/dashboard` returns:
+  - current tier
+  - remaining generations
+  - project list
+  - export history
+- `POST /api/export` supports:
+  - `zip`, `rbxm`, `unitypackage`, `unreal`, `obj`, `glb`
+
+### Security + Scalability Foundation
+- JWT-protected API routes
+- Stripe webhook signature verification endpoint
+- Project payload encryption helper
+- Queue-style async generation flow (in-memory starter)
+
+## Project Structure
+
+- `frontend/` React + Three.js editor shell
+- `backend/` Express API + auth/subscriptions/generation queue scaffolding
+- `docs/` implementation notes and next phases
+
+## Run Locally
+
+### Backend
+```bash
+cd backend
+cp .env.example .env
+npm install
+npm run dev
+```
+
+### Frontend
+```bash
+cd frontend
+npm install
+npm run dev
+```
+
+Then open `http://localhost:5173`.
 
EOF
)
