# 🎯 ACM Cinema – Developer Cheatsheet

  

## 📌 Overview

- Frontend: Next.js (App Router, TS, Tailwind)

- Backend: Spring Boot (JSON APIs)

- State: Local component state + shared `FiltersContext` for search filters

- Patterns: URL-driven search, client-side fetch, shared popup for filters

  

---

  

## 🔌 API Configuration

- File: `frontend/src/config/api.ts`

- Base URL: `NEXT_PUBLIC_API_URL` (default `http://localhost:8080`)

- Endpoints (movies):

- Lists: `/api/movies/now-playing`, `/api/movies/upcoming`

- Search: `/api/movies/search-now-playing`, `/api/movies/search-upcoming`

- Genres: `/api/movies/genres`

- Details: `/api/movies/{movieId}`

- Schedule: `/api/movies/{movieId}/dates`, `/api/movies/{movieId}/times?date=YYYY-MM-DD`

- Usage:

```ts

const url = buildUrl(endpoints.movies.searchNowPlaying);

const res = await fetch(`${url}?${params.toString()}`);

const data = await res.json();

```

  

---

  

## 🧩 Providers & Shared State

- File: `frontend/src/contexts/FiltersContext.tsx`

- Wrapped in: `app/layout.tsx`

- Provides:

- `selectedGenres: Set<string>`

- `selectedDate: { month: string; day: string; year: string }`

- `setSelectedGenres`, `setSelectedDate`

- Used by:

- `NavBar` (builds search query)

- `FiltersPopUp` (selects genres/date)

- `movies/page.tsx` (reads URL params and fetches)

  

### React State Architecture: Providers, Contexts, and Hooks

- Provider: A component that makes a value (state + actions) available to all descendants.

- In this project: `FiltersProvider` wraps the app in `app/layout.tsx`.

- Context: The container for that shared value; components read it with `useContext`.

- File exposes a Context and a helper hook.

- useContext: React API to consume a Context value inside any child component.

- Custom hooks: Project-specific hooks that encapsulate context usage or logic.

- `useFilters()` (exported from `FiltersContext.tsx`) gives you `{ selectedGenres, setSelectedGenres, selectedDate, setSelectedDate }`.

- `useRegistration()` (used in registration flow) provides multi-step form state and validators.

  

Minimal example:

```tsx

// In a component (e.g., NavBar / FiltersPopUp)

import { useFilters } from '@/contexts/FiltersContext';

  

export function Example() {

const { selectedGenres, setSelectedGenres, selectedDate, setSelectedDate } = useFilters();

// read state

const hasAction = selectedGenres.has('Action');

// update state

setSelectedGenres(prev => new Set(prev).add('Drama'));

setSelectedDate({ month: '9', day: '26', year: '2025' });

return null;

}

```

Benefits:

- Single source of truth for filters across `NavBar`, `FiltersPopUp`, and `movies/page.tsx`.

- No prop drilling; components stay focused on UI.

  

---

  

## 🔍 Search & Filters Flow

1) User types in `NavBar` or movies page.

2) Build `URLSearchParams` with title + genres + date (from `FiltersContext`).

3) Navigate to `/movies?title=&genres=&month=&day=&year=`.

4) `movies/page.tsx` reads params and fetches both sections:

- `search-now-playing` and `search-upcoming` (parallel)

5) Results render in `MovieCardsGrid`.

  

`FiltersPopUp` (shared):

- Opens from `NavBar` or movies page button.

- Fetches genres once on first open; toggles selections via `FiltersContext`.

  

---

  

## 🎬 Movies & Details

- Grid: `components/common/movies/MovieCardsGrid.tsx`

- Card: `components/common/movies/MovieCard.tsx`

- Hover overlay: title, short synopsis, genres, release date

- Preview button: opens `TrailerEmbed` with `trailer_link`

- Click card: opens `SelectedMovie`

- Details Popup: `components/common/movies/SelectedMovie.tsx`

- Left: poster, compact meta (title, rating, release date), genres, synopsis

- Right: trailer, date selector, times list, cast/producer/director, tickets CTA

- Data fetching:

- On mount: `GET /api/movies/{id}/dates` → auto-select first

- On date change: `GET /api/movies/{id}/times?date=YYYY-MM-DD`

  

---

  

## 🎟️ Booking Flow

- Seats: `app/(booking)/booking/(seats)/page.tsx`

- Local seat state; header card; submit → `/booking/ticket-age?seats=&title=&date=&time=`

- Bottom promo: 20% discount → “Apply Now!” → `/booking/checkout`

- Ticket Selection: `app/(booking)/booking/ticket-age/page.tsx`

- Header: `Ticket Selection for "title"` with `date • time`

- `TicketTable`: Adult/Child/Senior rows, counters, right-aligned price

- Footer: total + compact checkout button (no wrapping)

- Bottom promo: same discount CTA → `/booking/checkout`

  

---

  

## 🎨 UI/Styling Conventions

- Theme: Dark background with blurred cards

- `bg-white/5`, `backdrop-blur-md`, `border-white/10`, rounded-xl

- Accents: `text-acm-pink`, gradients (pink → orange) for primary buttons

- Buttons: gradient, rounded, `hover:brightness-110`

- Icons: `react-icons` (`PiMagnifyingGlass`, `IoFilterOutline`, etc.)

- Images: `next/image` with `fill` + `sizes` (e.g., `"100vw"`)

  

---

  

## 📁 Quick File Index

- API: `src/config/api.ts`

- Layout/Provider: `src/app/layout.tsx` (wraps `FiltersProvider`)

- Context: `src/contexts/FiltersContext.tsx`

- Nav/Search: `components/common/navBar/NavBar.tsx`

- Filters Popup: `components/specific/movies/FiltersPopUp.tsx`

- Movies Page: `src/app/(public)/movies/page.tsx`

- Movies Grid: `components/common/movies/MovieCardsGrid.tsx`

- Movie Card/Preview: `components/common/movies/MovieCard.tsx`, `TrailerEmbed.tsx`

- Details Popup: `components/common/movies/SelectedMovie.tsx`

- Seats: `app/(booking)/booking/(seats)/page.tsx`

- Ticket Selection: `app/(booking)/booking/ticket-age/page.tsx`

- Footer: `components/specific/home/Footer.tsx` (used in home page)

  

---

  

## 🔁 Data Fetch Patterns

```ts

// Build params

const params = new URLSearchParams();

if (title) params.set('title', title);

if (genres) params.set('genres', genres);

if (month) params.set('month', month);

if (day) params.set('day', day);

if (year) params.set('year', year);

  

// Fetch

const res = await fetch(`${buildUrl(endpoints.movies.searchUpcoming)}?${params.toString()}`);

const data = await res.json();

```

  

```ts

// SelectedMovie times fetch

const url = new URL(buildUrl(endpoints.movies.times(movieId)));

url.searchParams.set('date', 'YYYY-MM-DD');

const times = await (await fetch(url)).json();

```