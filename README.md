# Free GTO — Poker Strategy Trainer

A beautifully designed, Apple-inspired GTO poker trainer. Single-page static app ready for Azure Static Web Apps hosting at `free-gto.com`.

## What's Included

```
├── index.html                  # Complete app (single file, no dependencies)
├── staticwebapp.config.json    # Azure Static Web Apps routing & headers
├── manifest.webmanifest        # PWA manifest
├── robots.txt                  # Search engine directives
├── sitemap.xml                 # SEO sitemap
└── README.md                   # This file
```

## Features

- **GTO Trainer** — Practice preflop decisions with instant feedback
- **Range Explorer** — Interactive 13×13 grid with adjustable stacks & positions
- **Push/Fold Charts** — Quick reference for short-stack play
- **Session Tracker** — Log results, track bankroll & ROI
- **Opponent Notes** — Tag player types, record tendencies
- **Equity Calculator** — Preflop matchup estimations
- **Keyboard Shortcuts** — N to deal, 1/2/3 for actions
- **Data Export/Import** — JSON backup for cross-device sync
- **100% Offline** — No server required, all logic runs client-side

## Deploy to Azure Static Web Apps

### Option 1: Azure Portal (GUI)

1. Go to [Azure Portal](https://portal.azure.com) → Create Resource → Static Web App
2. Choose your subscription and resource group
3. Name: `free-gto`
4. Hosting plan: Free
5. Source: **Other** (for manual deployment)
6. After creation, go to **Custom domains** → Add `free-gto.com`
7. Deploy using the Azure CLI (see below)

### Option 2: Azure CLI

```bash
# Install Azure Static Web Apps CLI
npm install -g @azure/static-web-apps-cli

# Login to Azure
az login

# Create the Static Web App resource (one time)
az staticwebapp create \
  --name free-gto \
  --resource-group YOUR_RESOURCE_GROUP \
  --location "centralus"

# Deploy (from this directory)
swa deploy . --deployment-token YOUR_DEPLOYMENT_TOKEN
```

### Option 3: GitHub Actions (CI/CD)

1. Push this folder to a GitHub repo
2. In Azure Portal, create a Static Web App linked to your repo
3. Azure auto-generates a GitHub Actions workflow
4. Every push to `main` auto-deploys

## Custom Domain Setup

1. In Azure Portal → Static Web App → **Custom domains**
2. Add `free-gto.com`
3. At your domain registrar, add a CNAME record:
   - **Name**: `@` or `www`
   - **Value**: `<your-app>.azurestaticapps.net`
4. Azure provides a free SSL certificate automatically

## Tech Notes

- Zero build step — just static files, deploy as-is
- All data stored in `localStorage` (key: `freegto_v1`)
- No external API calls, no tracking, no cookies
- SF Pro system font stack (renders natively on Apple devices, falls back gracefully)
- Designed for mobile-first with full desktop support
