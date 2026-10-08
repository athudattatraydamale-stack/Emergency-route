Emergency Route – Live (SIMULATION)

Real maps (OpenStreetMap/Leaflet), real routing (OSRM), real signal locations (OSM Overpass), real-time updates (Socket.IO), JWT + role-based access. Signal states are simulated; nothing controls real traffic infrastructure.


Run


Install Node 18+. 2. npm install 3. cp .env.example .env (set JWT_SECRET) 4. npm run dev 5. Open http://localhost:3000


Demo logins (password demo1234)

operator (EMERGENCY_OPERATOR) · officer (TRAFFIC_OFFICER) · admin (ADMIN)


Demo

Open two browser windows: operator and officer. Operator: search destination + set start (GPS or map click) → START EMERGENCY TRIP → ▶ Simulate drive → REQUEST SIGNAL PRIORITY. Officer: Approve → signal turns green (PRIORITY) → vehicle passes → returns to NORMAL after PRIORITY_HOLD_MS. Audit log updates live.


API (Bearer token)

POST /auth/login · POST /emergency-trips · GET /emergency-trips/:id · POST /emergency-trips/:id/location · POST /emergency-trips/:id/end · POST /priority-requests · GET /priority-requests · POST /priority-requests/:id/approve|reject (officer only) · GET /traffic-signals · GET /audit-logs (officer/admin)


Notes


Data is in memory (resets on restart). Replace db in server.js with PostgreSQL.

OSRM, Overpass and Nominatim public servers are fair-use only; use your own or a paid provider for more than demos. Works best for city-scale trips.

Deploy: Render/Railway/Fly (Node web service, npm start), set JWT_SECRET and DEMO_PASSWORD, serve over HTTPS (GPS needs HTTPS).

