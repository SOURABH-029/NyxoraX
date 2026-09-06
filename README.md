# NYXORA — Visual Universe

> **"Enter the Visual Universe."**  
> Official production-ready website for YouTube creator channel [NYXORA](https://www.youtube.com/channel/UCkb_QdDgDiuRfCWAAl9N9sw) (`UCkb_QdDgDiuRfCWAAl9N9sw`).

---

## ⚡ Overview & Features

NYXORA is an ultra-premium, futuristic, and cinematic web application built specifically for digital creators. It acts as an official live synchronized visual hub connected to the creator's YouTube channel.

- **Dual-Engine Live YouTube Synchronization**:
  - **Zero-Config Live RSS Engine**: Automatically fetches real uploads, Shorts, titles, descriptions, views, and thumbnails directly from the YouTube Atom feed without needing any API setup or keys.
  - **YouTube Data API v3 Engine**: When a `YOUTUBE_API_KEY` is provided in `.env.local`, the serverless backend automatically switches to the YouTube Data API for granular metrics (durations, like counts, and channel statistics).
  - **Smart In-Memory Caching & Manual Refresh**: Prevents quota exhaustion with a 10-minute cache while enabling instant on-demand synchronization via the "Live Sync" button in the navigation bar.
- **Futuristic 3D WebGL Experience**:
  - **Interactive 3D Hero Monolith**: Three.js WebGL canvas with an interactive rotating crystal prism, glowing energy core, dual orbital gyro rings, and a 800+ particle celestial dust field responding dynamically to mouse parallax.
  - **Performance Optimized**: Uses `IntersectionObserver` to automatically pause rendering when off-screen to preserve battery and GPU power. Graceful CSS visual fallback for devices without WebGL.
- **3D Tilt Video Cards**:
  - Hardware-accelerated CSS 3D transforms (`rotateX`, `rotateY`, `scale3d`) that dynamically tilt toward the user's cursor with specular glare and subtle atmospheric glow.
- **Cinematic Video Theater Modal**:
  - Embedded YouTube video player with responsive 16:9 widescreen or 9:16 vertical Shorts layout.
  - Complete video metadata, creator notes, view count, published date, one-click link sharing, and related recommendations.
- **Dedicated NYXORA Shorts Section**:
  - Mobile-optimized vertical 9:16 cards with swipe-friendly horizontal feed and instant theater preview.
- **Channel Metaspace & Stats**:
  - Live channel stats (Total Views, Video Count, Community Subscribers, Channel Founding Year 2023) directly from YouTube data.
- **Custom Futuristic Cursor**:
  - Dual-layer trailing cursor with glowing precision core and interactive follower ring that reacts to buttons, links, and 3D elements. Automatically disabled on mobile/touch screens and respects `prefers-reduced-motion`.
- **Preloader**:
  - Fast, non-blocking cinematic entrance sequence revealing the NYXORA glyph and brand typography.
- **Centralized Configuration**:
  - Edit brand name, social handles, channel ID, SEO metadata, and creative pillars in a single file: `src/config/site.ts`.

---

## 🛠️ Tech Stack

- **Framework**: Next.js 16 (App Router, Server Components & Serverless Routes)
- **Language**: TypeScript 5
- **Styling**: Tailwind CSS 4 with custom glassmorphism and atmospheric glow design system
- **3D & WebGL**: Three.js
- **Icons**: Custom SVG authentic brand glyphs + Lucide React
- **Animations**: CSS 3D perspective transforms & Canvas Confetti
- **XML Parsing**: `fast-xml-parser`

---

## 🚀 Getting Started

### 1. Installation
```bash
cd nyxora
npm install
```

### 2. Environment Configuration (Optional)
The website is **100% functional right out of the box** using the zero-config RSS sync engine.

To enable extended YouTube Data API v3 metrics (durations, like counts, subscriber metrics):
1. Copy `.env.example` to `.env.local`:
   ```bash
   cp .env.example .env.local
   ```
2. Add your YouTube Data API v3 Key:
   ```env
   YOUTUBE_CHANNEL_ID=UCkb_QdDgDiuRfCWAAl9N9sw
   YOUTUBE_API_KEY=your_api_key_here
   ```

### 3. Run Development Server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

### 4. Build for Production
```bash
npm run build
npm run start
```

---

## 📁 Project Structure

```
nyxora/
├── src/
│   ├── app/
│   │   ├── api/youtube/sync/route.ts  # Serverless YouTube sync & caching API
│   │   ├── globals.css                # Cinematic dark theme & glassmorphism
│   │   ├── layout.tsx                 # Root layout with SEO & metadata
│   │   └── page.tsx                   # SSR Home page
│   ├── components/
│   │   ├── 3d/
│   │   │   ├── HeroScene.tsx          # Three.js 3D Interactive Monolith & Particles
│   │   │   └── TiltCard.tsx           # Interactive 3D tilt card with specular glare
│   │   ├── layout/
│   │   │   ├── Navbar.tsx             # Glassmorphism navbar with live sync pill
│   │   │   └── Footer.tsx             # Cinematic footer & channel links
│   │   ├── modal/
│   │   │   └── VideoModal.tsx         # High-fidelity video & Shorts theater modal
│   │   ├── sections/
│   │   │   ├── HeroSection.tsx        # Hero section with split 3D layout
│   │   │   ├── ChannelStats.tsx       # Live channel metrics & verification
│   │   │   ├── FeaturedVideo.tsx      # Cinematic video spotlight
│   │   │   ├── LatestVideos.tsx       # 3D tilt video gallery with filter
│   │   │   ├── ShortsSection.tsx      # Vertical 9:16 Shorts showcase
│   │   │   ├── AboutSection.tsx       # Creator editorial narrative
│   │   │   └── SocialCTA.tsx          # Grand Subscribe banner & social hub
│   │   ├── ui/
│   │   │   ├── CustomCursor.tsx       # Desktop custom trailing cursor
│   │   │   ├── Icons.tsx              # Authentic brand SVGs (YouTube, IG, X, Discord)
│   │   │   └── Preloader.tsx          # Cinematic loading reveal
│   │   └── NyxoraApp.tsx              # Client application state manager
│   ├── config/
│   │   └── site.ts                    # Central brand & channel configuration
│   └── lib/
│       └── youtube.ts                 # Dual-engine YouTube sync & parser
├── .env.example                       # Environment variables template
├── .env.local                         # Local environment settings
└── next.config.ts                     # Next.js configuration & image domains
```

---

## 🌐 Deployment

This application is ready to deploy to any modern hosting platform:
- **Vercel**: Import the repository, add `YOUTUBE_API_KEY` to Project Settings > Environment Variables (optional), and click Deploy.
- **Netlify / Cloudflare Pages / Node.js Host**: Standard `npm run build` and `npm run start`.
