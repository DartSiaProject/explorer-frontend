# dartsia-frontend

> Blockchain explorer and network intelligence interface for the [Sia](https://sia.tech) decentralized storage network.

Live at **[dartsia.app](https://dartsia.app)**

---

## Overview

`dartsia-frontend` is the React/TypeScript client for the Dartsia platform. It queries the [dartsia-backend](https://github.com/poclus2/dartsia-backend) REST API to render real-time data about the Sia network: blocks, transactions, storage hosts, and network statistics — on both desktop and mobile.

---

## Features

- **Block Explorer** — paginated list of recent blocks with height, timestamp, transaction count, and fees; per-block detail page with parent hash, included transactions, and miner payouts
- **Transaction Explorer** — live transaction stream with type classification (transfer, contract formation, contract revision, storage proof, host announcement); filterable and searchable
- **Host Network** — filterable and sortable host list with status, storage price, capacity, uptime, and software version; per-host detail page with speed gauges, uptime history chart, and contract parameters
- **Geographic Map** — interactive Leaflet map showing the worldwide distribution of the active host fleet
- **Global Search** — unified search for blocks (by height or hash), transactions (by ID), and hosts (by public key or network address)
- **Full Mobile Support** — dedicated bottom navigation, touch-optimized bottom sheets, real-time network status strip

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | React 18 + Vite |
| Language | TypeScript |
| Styling | Tailwind CSS |
| UI Components | shadcn/ui |
| Data Fetching | TanStack Query |
| Routing | React Router v6 |
| Map | React Leaflet |
| Icons | Lucide React |

---

## Getting Started

**Requirements:** Node.js 18+

```bash
# Clone the repository
git clone https://github.com/poclus2/dartsia-frontend.git
cd dartsia-frontend

# Install dependencies
npm install

# Configure environment
cp .env.example .env
# Set VITE_API_URL and VITE_API_KEY in .env

# Start the development server
npm run dev
```

The dev server will be available at `http://localhost:5173`.

---

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `VITE_API_URL` | URL of the dartsia-backend API | `http://localhost:3000` |
| `VITE_API_KEY` | API key for backend authentication | — |

---

## Docker

A production Docker image is built and published automatically via GitHub Actions on every push to `main`.

```bash
# Build locally
docker build -f Dockerfile.prod \
  --build-arg VITE_API_URL=https://your-backend.com \
  --build-arg VITE_API_KEY=your-key \
  -t dartsia-frontend .

# Run
docker run -p 80:80 dartsia-frontend
```

---

## Project Structure

```
src/
├── api/          # Axios client and API calls
├── components/   # Shared UI components (layout, mobile, hosts, network...)
├── hooks/        # TanStack Query hooks (useDartsia, useMobile...)
├── pages/        # Route-level page components
└── types/        # TypeScript types for the Dartsia API
```

---

## Related

- **[dartsia-backend](https://github.com/poclus2/dartsia-backend)** — NestJS API, block ingestion worker, and host scanner
- **[Sia Foundation](https://sia.tech)** — the Sia protocol and ecosystem

---

## License

MIT
