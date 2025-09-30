# 🎬 Cinema Booking System API - Developer Cheatsheet

## Base URL
```
http://localhost:8080/api/movies
```

---

## 📋 **CORE MOVIE ENDPOINTS**

### 1. Get Now Playing Movies
**Purpose**: Display movies currently showing on <span style="background:#fff88f">homepage  "Now Playing" section</span>
**Method**: `GET`  
**Endpoint**: `/now-playing`  
**Parameters**: None  

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/now-playing"
```

**Returns**: `List<Movie>` - Full movie objects ordered by earliest show date  
**Example Response**:
```json
[
  {
    "movie_id": 1,
    "title": "Godzilla Minus One",
    "status": "NOW_PLAYING",
    "genres": "Action, Sci-Fi, Drama",
    "rating": "PG-13",
    "release_date": "2024-11-03",
    "synopsis": "A post-war Japan story about Godzilla...",
    "trailer_link": "https://youtube.com/watch?v=...",
    "poster_link": "https://example.com/poster1.jpg",
    "cast_names": "Ryunosuke Kamiki, Minami Hamabe",
    "directors": "Takashi Yamazaki",
    "producers": "Minami Ichikawa"
  }
]
```

---

### 2. Get Upcoming Movies
**Purpose**: Display upcoming movies when <span style="background:#fff88f">clicking from homepage the "Upcoming" button</span>  
**Method**: `GET`  
**Endpoint**: `/upcoming`  
**Parameters**: None  

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/upcoming"
```

**Returns**: `List<Movie>` - Full movie objects ordered by earliest show date  
**Example Response**:
```json
[
  {
    "movie_id": 1,
    "title": "Old Boy",
    "status": "UPCOMING",
    "genres": "Action, Drama, Psychological",
    "rating": "PG-13",
    "release_date": "2024-11-03",
    "synopsis": "A korean film about an old boy or summ...",
    "trailer_link": "https://youtube.com/watch?v=...",
    "poster_link": "https://example.com/poster1.jpg",
    "cast_names": "Ryunosuke Kamiki, Minami Hamabe",
    "directors": "Takashi Yamazaki",
    "producers": "Minami Ichikawa"
  }
]
```

---

### 3. Get Available Genres
**Purpose**: Populate genres state variable when you hover over the filter icon, so it displays immediately on click of filters button then showing the filters popup <span style="background:#fff88f">(either from navbar searchbar or search page searchbar)</span>
**Method**: `GET`  
**Endpoint**: `/genres`  
**Parameters**: None  

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/genres"
```

**Returns**: `List<String>` - Alphabetically sorted unique genres  
**Example Response**:
```json
["Action", "Comedy", "Drama", "Horror", "Sci-Fi", "Thriller"]
```

---

## 🔍 **SEARCH ENDPOINTS**

### 4. Search Now Playing Movies
**Purpose**: Search within Now Playing movies  
**Method**: `GET`  
**Endpoint**: `/search-now-playing`  
**Parameters**: *All optional*
- `title` (String): Movie title search
- `genres` (String): Comma-separated genres (e.g., "Action,Comedy")
- `month` (Integer): 1-12
- `day` (Integer): 1-31
- `year` (Integer): e.g., 2024

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/search-now-playing?title=godzilla&genres=Action,Sci-Fi&month=11"
```

**Returns**: `List<Movie>` - Filtered NOW_PLAYING movies ordered by earliest show date <span style="background:#fff88f">on search</span>
**Example Response**:
```json
[
  {
    "movie_id": 1,
    "title": "Godzilla Minus One",
    "status": "NOW_PLAYING",
    "genres": "Action, Sci-Fi, Drama",
    "rating": "PG-13",
    "release_date": "2024-11-03",
    "synopsis": "A post-war Japan story about Godzilla...",
    "trailer_link": "https://youtube.com/watch?v=...",
    "poster_link": "https://example.com/poster1.jpg",
    "cast_names": "Ryunosuke Kamiki, Minami Hamabe",
    "directors": "Takashi Yamazaki",
    "producers": "Minami Ichikawa"
  }
]
```

---

### 5. Search Upcoming Movies
**Purpose**: Search within upcoming movies  
**Method**: `GET`  
**Endpoint**: `/search-upcoming`  
**Parameters**: Same as above  

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/search-upcoming?genres=Drama&year=2024"
```

**Returns**: `List<Movie>` - Filtered UPCOMING movies ordered by show date  <span style="background:#fff88f">when user searches</span>
**Example Response**: 
```json
[
  {
    "movie_id": 1,
    "title": "Old Boy",
    "status": "UPCOMING",
    "genres": "Action, Drama, Psychological",
    "rating": "PG-13",
    "release_date": "2024-11-03",
    "synopsis": "A korean film about an old boy or summ...",
    "trailer_link": "https://youtube.com/watch?v=...",
    "poster_link": "https://example.com/poster1.jpg",
    "cast_names": "Ryunosuke Kamiki, Minami Hamabe",
    "directors": "Takashi Yamazaki",
    "producers": "Minami Ichikawa"
  },
  {
  	...
  }
]
```

---

### 6. Get Movie Details By ID
**Purpose**: Full movie details <span style="background:#fff88f">when user clicks on a movie </span> 
**Method**: `GET`  
**Endpoint**: `/{movieId}`  
**Parameters**: 
- `movieId` (Path Variable): Movie ID

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/1"
```

**Returns**: `Movie` - Full movie object with all fields  
**Example Response**: Same format as endpoint #1


<hr>

## 🎫 **SHOW SCHEDULE ENDPOINTS**

### 7. Get Available Dates for Movie
**Purpose**: Populate date dropdown<span style="background:#fff88f"> for movie popup when user clicks on a movie</span>
**Method**: `GET`  
**Endpoint**: `/{movieId}/dates`  
**Parameters**: 
- `movieId` (Path Variable): Movie ID

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/1/dates"
```

**Returns**: `List<LocalDate>` - Available show dates ordered by date  
**Example Response**:
```json
["2024-11-01", "2024-11-02", "2024-11-03", "2024-11-04"]
```

---

### 8. Get Available Times for Movie on Date
**Purpose**: Populate time slots for selected date <span style="background:#fff88f">for movie popup when user clicks on a movie</span>
**Method**: `GET`  
**Endpoint**: `/{movieId}/times`  
**Parameters**: 
- `movieId` (Path Variable): Movie ID
- `date` (Query Parameter): Date in YYYY-MM-DD format

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/1/times?date=2024-11-01"
```

**Returns**: `List<ShowTime>` - Available show times for the date  
**Example Response**:
```json
[
  {
    "show_time_id": 123,
    "show_date_id": 45,
    "start_time": "10:00:00",
    "end_time": "12:30:00",
    "created_at": "2024-09-26T12:00:00"
  },
  {
    "show_time_id": 124,
    "show_date_id": 45,
    "start_time": "14:30:00",
    "end_time": "17:00:00",
    "created_at": "2024-09-26T12:00:00"
  }
]
```

---

## 🎯 **OPTIMIZED BROWSING ENDPOINTS**

### 9. Get Now Playing (Lightweight)
**Purpose**: Fast loading for homepage grids  
**Method**: `GET`  
**Endpoint**: `/browse/now-playing`  
**Parameters**: None  

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/browse/now-playing"
```

**Returns**: `List<MovieSummary>` - Lightweight movie data (excludes cast, directors, producers)  
**Example Response**:
```json
[
  {
    "movie_id": 1,
    "title": "Godzilla Minus One",
    "status": "NOW_PLAYING",
    "genres": "Action, Sci-Fi, Drama",
    "rating": "PG-13",
    "release_date": "2024-11-03",
    "synopsis": "A post-war Japan story about Godzilla...",
    "trailer_link": "https://youtube.com/watch?v=...",
    "poster_link": "https://example.com/poster1.jpg"
  }
]
```

---

### 10. Get Upcoming (Lightweight)
**Purpose**: Fast loading for upcoming movies grid  
**Method**: `GET`  
**Endpoint**: `/browse/upcoming`  
**Parameters**: None  

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/browse/upcoming"
```

**Returns**: `List<MovieSummary>` - Lightweight movie data  
**Example Response**: Same format as above

---

## 🛠️ **UTILITY ENDPOINTS**

### 11. API Health Check
**Purpose**: Test if API is working  
**Method**: `GET`  
**Endpoint**: `/test`  
**Parameters**: None  

**Example Call**:
```bash
curl "http://localhost:8080/api/movies/test"
```

**Returns**: `String` - Simple status message  
**Example Response**:
```json
"API is working!"
```

---

### 12. Create Movie (Placeholder)
**Purpose**: Create new movie (placeholder implementation)  
**Method**: `POST`  
**Endpoint**: `/create`  
**Parameters**: None  

**Example Call**:
```bash
curl -X POST "http://localhost:8080/api/movies/create"
```

**Returns**: `String` - Confirmation message  
**Example Response**:
```json
"Posted movie."
```

---

## 📝 **QUICK REFERENCE**

| Endpoint              | Method | Purpose                     | Returns              |
| --------------------- | ------ | --------------------------- | -------------------- |
| `/now-playing`        | GET    | Homepage/NowPlaying movies  | `List<Movie>`        |
| `/upcoming`           | GET    | Upcoming movies             | `List<Movie>`        |
| `/genres`             | GET    | All Available Genres        | `List<String>`       |
| `/search-now-playing` | GET    | Search NowPlaying movies    | `List<Movie>`        |
| `/search-upcoming`    | GET    | Search Upcoming movies      | `List<Movie>`        |
| `/browse/now-playing` | GET    | Lightweight current movies  | `List<MovieSummary>` |
| `/browse/upcoming`    | GET    | Lightweight upcoming movies | `List<MovieSummary>` |
| `/{movieId}`          | GET    | Full movie details          | `Movie`              |
| `/{movieId}/dates`    | GET    | Available dates             | `List<LocalDate>`    |
| `/{movieId}/times`    | GET    | Available times             | `List<ShowTime>`     |
| `/test`               | GET    | Health check                | `String`             |
| `/create`             | POST   | Create movie                | `String`             |

---

## 🚀 **FRONTEND INTEGRATION TIPS**

1. **Homepage**: Use `/browse/now-playing` for fast loading
2. **Search**: Use `/search-now-playing` or `/search-upcoming` with filters
3. **Movie Details**: Use `/{movieId}` when user clicks on movie
4. **Booking Flow**: Use `/{movieId}/dates` then `/{movieId}/times`
5. **Genre Filters**: Use `/genres` to populate filter dropdowns

---

## ⚡ **PERFORMANCE NOTES**

- **Lightweight endpoints** (`/browse/*`) exclude heavy fields (cast, directors, producers)
- **Full endpoints** include all movie data for detailed views
- **Search endpoints** support complex filtering with AND/OR logic
- **Date filtering** ensures movies match ALL provided date criteria on the SAME show date