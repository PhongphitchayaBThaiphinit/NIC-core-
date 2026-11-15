# NIC Core

## Run locally
```bash
npm install
npm start
```
Open http://localhost:3000

## Deploy publicly on Render
This is an Express app, so create a **Web Service** (not Static Site).

1. Push this project folder to a GitHub repository. Do not upload `node_modules`.
2. In Render choose **New > Web Service** and connect the repository.
3. Set Runtime `Node`, Build Command `npm install`, Start Command `npm start`.
4. Deploy. Render provides an HTTPS `onrender.com` URL.

### SQLite persistence
Render free web services have an ephemeral filesystem; SQLite history can be lost on restart, redeploy, or spin-down. To keep SQLite data, use a paid web service with a persistent disk:
- Mount path: `/var/data`
- Environment variable: `DATABASE_PATH=/var/data/nic_core.db`

Alternatively migrate to managed PostgreSQL.

## Bluetooth
- Web Bluetooth requires `localhost` or HTTPS and works in supported browsers such as Chrome/Edge.
- The ESP32 must be physically near the device running the browser.
- The browser connects directly to ESP32 over BLE; publishing the website does not make the ESP32 remotely reachable from the server.
- The included ESP32 sketch currently sends demo values; replace them with actual sensor readings.

## BLE payload
```json
{"N":45,"P":22,"K":35,"M":68,"T":28,"PH":6.5}
```
