## Curl tests (assume base http://localhost:8080)
- Health
  - curl "http://localhost:8080/api/movies/test"
- ***Homepage lists (DB-ordered by earliest show_date)***
  - Now Playing: curl "http://localhost:8080/api/movies/now-playing"
  - Upcoming: curl "http://localhost:8080/api/movies/upcoming"
- Generic search (mixed list; AND across title/genres/date; OR within genres; split client-side by status)
  - Title only: curl "http://localhost:8080/api/movies/search?title=godzilla"
  - Genres (OR inside): curl "http://localhost:8080/api/movies/search?genres=Action,Comedy"
  - Month only: curl "http://localhost:8080/api/movies/search?month=7"
  - Day only: curl "http://localhost:8080/api/movies/search?day=1"
  - Year only: curl "http://localhost:8080/api/movies/search?year=2025"
  - Title + Genres + Month: curl "http://localhost:8080/api/movies/search?title=bat&genres=Action,Thriller&month=7"
  - Full date: curl "http://localhost:8080/api/movies/search?month=10&day=1&year=2025"
- ***DB-ordered search per status (THIS IS WHAT WE'LL BE USING)***
  - Now Playing ordered: curl "http://localhost:8080/api/movies/search-now-playing?title=man&genres=Action,Drama&month=7"
  - Upcoming ordered: curl "http://localhost:8080/api/movies/search-upcoming?genres=Comedy,Romance&year=2025"
- ***Show schedule (movieId=1 examples) (THIS IS WHAT WE'LL BE USING)
  - Dates: curl "http://localhost:8080/api/movies/1/dates"
  - Times for date: curl "http://localhost:8080/api/movies/1/times?date=2025-10-01"
  - Full schedule map: curl "http://localhost:8080/api/movies/1/schedule"


---

## API reference (Endpoints, Service methods, Purpose, Example JSON)

Base URL: http://localhost:8080

### Frontend Overview (all u need to kno)
- **Homepage:**
  - *GET /api/movies/now-playing*
  - *GET /api/movies/upcoming*
- **Search page (ordered sections):**
  - *GET /api/movies/search-now-playing?... (render “Now Playing” section)*
  - *GET /api/movies/search-upcoming?... (render “Upcoming” section)*
- **ViewSelectedMovieDetailsPopup:**
  - *GET /api/movies/{movieId}/dates, then GET /api/movies/{movieId}/times?date=...*


1) Health
- Endpoint: GET /api/movies/test
- Service: N/A
- Purpose: quick server check
- Example:
  "API is working!"

1) **Homepage — Now Playing (ordered)**
- Endpoint: GET /api/movies/now-playing
- Service: MovieService.getNowPlayingOrdered()
- Purpose: NOW_PLAYING movies sorted by earliest upcoming show_date (ascending)
- Example:
  [
    { "movie_id": 2, "title": "Superman", "status": "NOW_PLAYING", "genres": "Action, Sci-Fi", "release_date": "2025-07-11", ... },
    { "movie_id": 5, "title": "Demon Slayer...", "status": "NOW_PLAYING", ... }
  ]

1) **Homepage — Upcoming (ordered)**
- Endpoint: GET /api/movies/upcoming
- Service: MovieService.getUpcomingOrdered()
- Purpose: UPCOMING movies sorted by first show_date (ascending)
- Example:
  [
    { "movie_id": 9, "title": "Oldboy", "status": "UPCOMING", "genres": "Thriller, Mystery", ... },
    { "movie_id": 12, "title": "Materialists", "status": "UPCOMING", ... }
  ]

4) Search (mixed list; split client-side)
- Endpoint: GET /api/movies/search?title=&genres=&month=&day=&year=
- Service: MovieService.searchMovies(title, genres, month, day, year)
- Purpose:
  - AND across title, genres, date parts (each part optional)
  - OR inside multiple genres (comma-separated)
  - Returns mixed NOW_PLAYING and UPCOMING; split in the frontend by status
- Example:
  [
    { "movie_id": 1, "title": "Godzilla Minus One", "status": "NOW_PLAYING", ... },
    { "movie_id": 9, "title": "Oldboy", "status": "UPCOMING", ... }
  ]

4) **Search — Now Playing only (ordered)**
- Endpoint: GET /api/movies/search-now-playing?title=&genres=&month=&day=&year=
- Service: MovieService.searchNowPlayingOrdered(title, genres, month, day, year)
- Purpose: Filtered NOW_PLAYING results ordered by earliest show_date (ascending)
- Example:
  [
    { "movie_id": 2, "title": "Superman", "status": "NOW_PLAYING", ... },
    { "movie_id": 5, "title": "Demon Slayer...", "status": "NOW_PLAYING", ... }
  ]

4) **Search — Upcoming only (ordered)**
- Endpoint: GET /api/movies/search-upcoming?title=&genres=&month=&day=&year=
- Service: MovieService.searchUpcomingOrdered(title, genres, month, day, year)
- Purpose: Filtered UPCOMING results ordered by earliest show_date (ascending)
- Example:
  [
    { "movie_id": 9, "title": "Oldboy", "status": "UPCOMING", ... },
    { "movie_id": 12, "title": "Materialists", "status": "UPCOMING", ... }
  ]

4) **Show Dates (for View Movie Details Popup)**
- Endpoint: GET /api/movies/{movieId}/dates
- Service: ShowTimeService.getAvailableDatesForMovie(movieId)
- Purpose: List of available LocalDate strings for a movie
- Example:
  ["2025-10-01","2025-10-02","2025-10-03"]

4) **Show Times by Date (for View Movie Details Popup)***
- Endpoint: GET /api/movies/{movieId}/times?date=YYYY-MM-DD
- Service: ShowTimeService.getAvailableTimesForMovieAndDate(movieId, date)
- Purpose: List of showtimes for the selected date, sorted by start_time
- Example:
  [
    { "show_time_id": 101, "show_date_id": 45, "start_time": "10:00:00", "end_time": "12:30:00", "created_at": "2025-09-26T12:00:00" },
    { "show_time_id": 102, "show_date_id": 45, "start_time": "13:30:00", "end_time": "16:00:00", "created_at": "2025-09-26T12:00:00" }
  ]

9) Full Schedule Map (optional convenience)
- Endpoint: GET /api/movies/{movieId}/schedule
- Service: ShowTimeService.getMovieShowSchedule(movieId)
- Purpose: Map of date => array of showtimes
- Example:
  {
    "2025-10-01": [
      { "show_time_id": 101, "start_time": "10:00:00", "end_time": "12:30:00", ... },
      { "show_time_id": 102, "start_time": "13:30:00", "end_time": "16:00:00", ... }
    ],
    "2025-10-02": [
      { "show_time_id": 111, "start_time": "09:30:00", "end_time": "12:00:00", ... }
    ]
  }

### Frontend Overview (all u need to kno)
- **Homepage:**
  - *GET /api/movies/now-playing*
  - *GET /api/movies/upcoming*
- **Search page (ordered sections):**
  - *GET /api/movies/search-now-playing?... (render “Now Playing” section)*
  - *GET /api/movies/search-upcoming?... (render “Upcoming” section)*
- **ViewSelectedMovieDetailsPopup:**
  - *GET /api/movies/{movieId}/dates, then GET /api/movies/{movieId}/times?date=...*