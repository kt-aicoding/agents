# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

ADV Moto Hub is a motorcycle route sharing and exploration platform focused on ADV (Adventure) motorcycle riders. The project includes a React web application for the frontend and WeChat cloud functions for the backend.

**Directory Structure:**
```
adv-moto-hub/
├── adv-moto-web/          # Frontend React application
│   ├── src/
│   │   ├── pages/         # Route pages (Home, Explore, Upload, Profile, RouteDetail)
│   │   ├── components/    # Reusable UI components
│   │   ├── services/      # Business logic (storage, GPX parsing)
│   │   ├── hooks/         # Custom React hooks
│   │   ├── types/         # TypeScript type definitions
│   │   └── styles/        # CSS stylesheets
│   └── cloudfunctions/    # WeChat cloud functions (backend)
```

## Common Commands

### Frontend Development

```bash
cd adv-moto-hub/adv-moto-web
npm run dev                # Start development server (Vite)
npm run build              # Production build (TypeScript compile + Vite build)
npm run lint               # Run ESLint
npm run preview            # Preview production build
```

### Cloud Functions (WeChat Mini Program Backend)

Each cloud function in `cloudfunctions/` has its own `package.json`:

```bash
cd cloudfunctions/<function-name>
npm install                # Install dependencies for a specific cloud function
```

Available cloud functions:
- `route-list` - Get route listings with filtering and pagination
- `route-detail` - Get single route details
- `route-create` - Create new route
- `review-create` - Create route review
- `user-login` - User authentication
- `user-update` - Update user profile

## Architecture Overview

### Frontend Architecture

**Technology Stack:**
- **Build:** Vite 7.x with React 19 and TypeScript 5.9
- **UI Library:** Ant Design Mobile 5.x (mobile-first design)
- **Map:** MapLibre GL JS 5.x (free OpenStreetMap alternative)
- **Routing:** React Router DOM 7.x
- **State Management:** Local state + localStorage (currently using LocalStorage service)

**Key Services:**

1. **LocalStorage Service** (`src/services/storage.ts`):
   - Manages all client-side data persistence
   - Handles routes, reviews, favorites, and user data
   - Includes seeded sample data for development
   - Key methods: `getRoutes()`, `saveRoute()`, `getRoute()`, `toggleFavorite()`

2. **GPX Parser Service** (`src/services/gpxParser.ts`):
   - Parses GPX files for motorcycle route data
   - Extracts waypoints, elevation data, and calculates statistics
   - Supports `trkpt`, `rtept`, and `wpt` XML elements
   - Key methods: `parse()`, `toGeoJSONCoordinates()`, `generateGPX()`

**Responsive Design:**
- Uses `useBreakpoint` hook for responsive layouts
- Mobile-first approach with Ant Design Mobile components
- Desktop layouts use grid systems and different navigation

### Type System

Core types defined in `src/types/index.ts`:
- `User` - User profile with garage (bikes)
- `Bike` - Motorcycle details (brand, model, year)
- `Route` - Route data with geometry, stats, difficulty
- `Review` - Route reviews and comments
- `GPXData` - Parsed GPX file structure
- `GPXTrackPoint` - Individual GPS waypoint

### Backend Architecture

**WeChat Cloud Functions:**
- Uses `wx-server-sdk` for database operations
- MongoDB-like database queries
- Each function is independently deployable

**Route Data Model:**
- `difficultyLevel`: 1-5 (1=paved, 5=extreme off-road)
- `terrainTags`: ['碎石', '涉水', '泥泞', '沙地', '高海拔']
- `geometry`: GeoJSON coordinates for map display
- `startPoint`/`endPoint`: Geographic bounds for filtering

## Design System

The application uses a "Wild Industrial" design theme (野性工业风):

**Color Palette (CSS Variables in `src/index.css`):**
- Primary backgrounds: Dark (#0a0a0b to #232326)
- Accent: Orange (#ff6b35) with gold (#f4a261) and cyan (#2ec4b6)
- Difficulty colors: Green → Blue → Yellow → Red → Purple (levels 1-5)

**Typography:**
- Display: Oswald (headings)
- Body: Space Grotesk
- Mono: JetBrains Mono (data/numbers)

**Key CSS Classes:**
- `.card` / `.card-interactive` - Card containers
- `.btn` / `.btn-primary` / `.btn-secondary` - Buttons
- `.difficulty-1` through `.difficulty-5` - Difficulty badges
- `.glass` - Glassmorphism effects

## Important Development Notes

### Data Flow
1. **Current MVP:** Uses LocalStorage service for all data persistence
2. **Planned:** Migrate to WeChat cloud functions for backend API
3. **GPX Files:** Parsed client-side, stored as string data in routes

### Map Integration
- Uses MapLibre GL JS (open-source fork of Mapbox GL)
- OpenStreetMap tiles (free, no API key required)
- Routes displayed as GeoJSON LineString features

### Mobile Navigation
- Bottom tab bar for mobile (Home, Explore, Upload, Profile)
- Desktop nav bar for larger screens
- Navigation hidden on detail pages (RouteDetail)

### Route Upload Flow
1. User uploads GPX file
2. GPXParser extracts coordinates, elevation, calculates distance/time
3. User adds metadata (title, description, difficulty, terrain tags)
4. Route saved with GeoJSON geometry for map rendering

### State Management Patterns
- Pages use `useState` for local state
- `LocalStorage` class provides centralized data access
- `useEffect` for data loading on mount
- No global state management library (yet)

## Known Constraints & Future Plans

1. **Map Compliance:** Operating in China requires mapping licenses. Currently positioned as "outdoor community" rather than "navigation app" for compliance.

2. **AI Integration:** Planned features include:
   - AI-powered route generation from travelogues
   - Visual terrain analysis from user photos
   - Dynamic risk warnings based on weather

3. **Cloud Functions:** Currently implemented but not integrated with frontend. Frontend still uses LocalStorage.
