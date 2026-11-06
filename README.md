(this readme is ai generated, the description was entirely written by me.)

# SLING Banking — fictional demo website + API

SLING is a **fictional banking simulator**. It is not a bank or payment service. It does not connect to financial institutions, move money, or collect banking credentials. All balances and transaction records are made up.

## Run locally
Requirements: Node.js 18 or newer.

1. Keep `server.js`, `package.json`, and `sling-banking-demo.html` in the same folder.
2. Open a terminal in that folder.
3. Run `npm start`.
4. Visit `http://localhost:3000`.

## Deploy both website and API free with HTTPS (Render)

The dashboard and API are served by the **same Node.js service**, so the browser uses the same origin for API requests. No separate API domain or CORS setup is needed.

1. Create or sign in to a GitHub account at https://github.com/.
2. Create a new repository, e.g. `sling-banking-demo`. For a public demo, do not put secrets or personal data in it.
3. Upload these three files to the repository root:
   - `server.js`
   - `package.json`
   - `sling-banking-demo.html`
4. Create/sign in to Render at https://render.com/.
5. In the Render dashboard choose **New → Web Service**, connect GitHub, and select your repository.
6. Use these settings:
   - Runtime: `Node`
   - Build command: `npm install`
   - Start command: `npm start`
   - Instance type: `Free` (if offered for your account/region)
7. Create the service. Render will assign a stable service URL ending in `.onrender.com` and automatically provision HTTPS.
8. Open the service URL. The dashboard and `/api/state` endpoint should both work over HTTPS.

You can choose a service name in Render; the URL is based on that name, subject to availability. It is not a temporary tunnel URL.

### Free-tier caveats
- Free web services may spin down after a period without traffic and take a little time to wake up on the next visit.
- Free instance availability, limits, and policies can change. Check Render's current pricing/docs before relying on it.
- The service's in-memory balance and transaction list reset whenever the service restarts or redeploys. This is deliberate for this demo.
- A public URL means anyone can open the demo and submit fictional transactions. This starter has no user accounts or admin authentication. Do not treat it as a private control panel.

## API examples

Read the fictional balance and latest transactions:
```bash
curl https://YOUR-SERVICE.onrender.com/api/state
```

Add a fictional credit:
```bash
curl -X POST https://YOUR-SERVICE.onrender.com/api/transactions \
  -H "Content-Type: application/json" \
  -d '{"company":"Imaginary Acme Ltd","amount":1250.50,"type":"credit"}'
```

Add a fictional debit:
```bash
curl -X POST https://YOUR-SERVICE.onrender.com/api/transactions \
  -H "Content-Type: application/json" \
  -d '{"company":"The Snack Department","amount":18.75,"type":"debit"}'
```

`POST /api/transactions` expects:
- `company`: fictional label, up to 48 characters
- `amount`: positive number, up to 1,000,000
- `type`: `credit` or `debit`

`GET /api/state` returns the current fictional balance and transaction list.

## Safety and transparency
Keep the fictional-demo banner and disclosure visible. Do not impersonate a real bank, collect real credentials, or present demo records as genuine statements or proof of payment. If you need a public demo, keep it clearly labeled as fictional.
