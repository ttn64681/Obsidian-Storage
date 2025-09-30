# Code Examples

## General code:
### Regex check to split a string with commas and get first word
```
// regex:"," looks for a comma, [0] looks for first genre, trim() removes whitespace

String first = genres.split(",")[0].trim(); // genres is a string
// E.g., "Action, Comedy, Fantasy"
// first contains "Action"
```
## JPA Repository Custom Methods
### d
```

```

### 4
```

```

### 6
```

```
## JPA Repository Derived Methods (Predefined)
### findBy*ColumnField*IgnoresCase(*Param*)
```
return movieRepository.findByGenresIgnoreCase(first); 
// looks for exact matches of "Action" and not ",Action,"
```


# Curl commands
`curl -s 'https://api.github.com/repos/jqlang/jq' | jq '.'`
- -s : silent
- --get : get method, useful if you pass in parameters in conjunction w/ -d, since that may imply a post request
-  | jq '.' : pretty printing for json output format

<hr>

## Base url
http://localhost:8080

## Test
curl -i "http://localhost:8080/api/hello"
curl -s "http://localhost:8080/api/env" | jq

## /movies test 
curl -i "http://localhost:8080/api/movies/test"
curl -i -X POST "http://localhost:8080/api/movies/create"

## /movies general
curl -s "http://localhost:8080/api/movies/now-playing" | jq
curl -s "http://localhost:8080/api/movies/upcoming" | jq

## /movies search
curl -s "http://localhost:8080/api/movies/search" | jq
curl -s --get "http://localhost:8080/api/movies/search" --data-urlencode "title=godzilla" | jq
curl -s --get "http://localhost:8080/api/movies/search" --data-urlencode "genres=Action,Sci-Fi" | jq
curl -s --get "http://localhost:8080/api/movies/search" --data-urlencode "month=7" | jq
curl -s --get "http://localhost:8080/api/movies/search" --data-urlencode "month=7" --data-urlencode "year=2025" | jq
curl -s --get "http://localhost:8080/api/movies/search" --data-urlencode "month=7" --data-urlencode "day=11" --data-urlencode "year=2025" | jq

curl -s --get "http://localhost:8080/api/movies/search" \
--data-urlencode "title=oldboy" \
--data-urlencode "genres=Drama,Thriller" | jq

curl -s --get "http://localhost:8080/api/movies/search" \
--data-urlencode "title=materialists" \
--data-urlencode "month=10" --data-urlencode "year=2025" | jq

curl -s --get "http://localhost:8080/api/movies/search" \
--data-urlencode "title=minus" \
--data-urlencode "genres=Action,Sci-Fi" \
--data-urlencode "month=7" --data-urlencode "day=11" --data-urlencode "year=2025" | jq

## /movies search-now-playing
```
# Title only
curl -s --get "http://localhost:8080/api/movies/search-now-playing" --data-urlencode "title=man" | jq
  
# Genres multi
curl -s --get "http://localhost:8080/api/movies/search-now-playing" --data-urlencode "genres=Action,Adventure" | jq

# Month only
curl -s --get "http://localhost:8080/api/movies/search-now-playing" --data-urlencode "month=9" | jq

# Full date
curl -s --get "http://localhost:8080/api/movies/search-now-playing" --data-urlencode "month=9" --data-urlencode "day=30" --data-urlencode "year=2025" | jq

# Title + genres + year
curl -s --get "http://localhost:8080/api/movies/search-now-playing" \
--data-urlencode "title=super" \
--data-urlencode "genres=Action,Fantasy" \
--data-urlencode "year=2025" | jq
```
## /movies search-upcoming
```
# Title only
curl -s --get "http://localhost:8080/api/movies/search-upcoming" --data-urlencode "title=materialists" | jq

# Genres only (multi)
curl -s --get "http://localhost:8080/api/movies/search-upcoming" --data-urlencode "genres=Drama,Romance" | jq

# Month + year
curl -s --get "http://localhost:8080/api/movies/search-upcoming" --data-urlencode "month=12" --data-urlencode "year=2025" | jq
  
# Full date
curl -s --get "http://localhost:8080/api/movies/search-upcoming" --data-urlencode "month=12" --data-urlencode "day=1" --data-urlencode "year=2025" | jq

# Title + genres + full date
curl -s --get "http://localhost:8080/api/movies/search-upcoming" \
--data-urlencode "title=old" \
--data-urlencode "genres=Thriller,Crime" \
--data-urlencode "month=11" --data-urlencode "day=15" --data-urlencode "year=2025" | jq
```


SELECT m.* FROM movies m
JOIN show_dates sd ON sd.movie_id = m.movie_id
WHERE m.status = 'NOW_PLAYING'
  AND (:title IS NULL OR LOWER(m.title) LIKE LOWER(CONCAT('%', :title, '%')))
  AND (:genresCsv IS NULL OR EXISTS (
    SELECT 1 FROM unnest(string_to_array(:genresCsv, ',')) g
    WHERE LOWER(m.genres) LIKE LOWER(CONCAT('%', trim(g), '%'))
  ))
GROUP BY m.movie_id
HAVING COUNT(CASE WHEN 
    (:year IS NULL OR EXTRACT(YEAR FROM sd.show_date) = :year) AND
    (:month IS NULL OR EXTRACT(MONTH FROM sd.show_date) = :month) AND
    (:day IS NULL OR EXTRACT(DAY FROM sd.show_date) = :day)
  THEN 1 ELSE NULL END) = COUNT(sd.show_date)
ORDER BY MIN(sd.show_date) ASC;


help give me commands (3) to put in one example show date and one exmaple show time for that show date. here is the reference command movie i intend to insert:

INSERT INTO movies
(title, status, genres, rating, release_date, synopsis, trailer_link, poster_link, cast_names, directors, producers)
VALUES
('DUMMY EXAMPLE', 'NOW_PLAYING', 'Comedy, Thriller', 'R', DATE '2025-06-10',
 'HELLO THIS IS A DUMMY DATA EXAMPLE HELLOOOOO',
 'https://youtu.be/vIu85WQTPRc?si=ni12TgPerRJzxoaG',
 'https://image.tmdb.org/t/p/original/inNN466SKHNjbGmpfhfsaPQNleS.jpg',
 'DUMMY ACOTR 1, DUMMY ACTOR 2',
 'Takashi Yamazaki',
 'Kenji Yamada, Emi Suzuki'),

here is the reference of the structure of how i add show dates to a movie:
INSERT INTO show_dates (movie_id, show_date)
SELECT 
    m.movie_id,
    CURRENT_DATE + INTERVAL '1 day' * (s.n) as show_date
FROM movies m
CROSS JOIN generate_series(0, 59) as s(n)
WHERE m.status = 'NOW_PLAYING'
ORDER BY m.movie_id, show_date;



here is the reference of the structure of how i add show times to a date:
-- Recreate show_times table with optional showtimes
CREATE TABLE show_times (
    show_time_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    show_date_id BIGINT REFERENCES show_dates(show_date_id) ON DELETE CASCADE,
    start_time TIME NOT NULL,
    end_time TIME NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Recreate indexes
CREATE INDEX idx_show_times_date_id ON show_times(show_date_id);
CREATE INDEX idx_show_times_start_time ON show_times(start_time);

with this in mind, help me insert this movie and then add a showdate to that movie and then add a showtime to that movies showdate



```
INSERT INTO movies
(title, status, genres, rating, release_date, synopsis, trailer_link, poster_link, cast_names, directors, producers)
VALUES
('DUMMY EXAMPLE', 'NOW_PLAYING', 'Comedy, Thriller', 'R', DATE '2025-06-10',
 'HELLO THIS IS A DUMMY DATA EXAMPLE HELLOOOOO',
 'https://youtu.be/vIu85WQTPRc?si=ni12TgPerRJzxoaG',
 'https://image.tmdb.org/t/p/original/inNN466SKHNjbGmpfhfsaPQNleS.jpg',
 'DUMMY ACOTR 1, DUMMY ACTOR 2',
 'Takashi Yamazaki',
 'Kenji Yamada, Emi Suzuki')
RETURNING movie_id;

INSERT INTO show_dates (movie_id, show_date)
VALUES (
  (SELECT movie_id FROM movies WHERE title = 'DUMMY EXAMPLE' ORDER BY movie_id DESC LIMIT 1),
  DATE '2025-10-01'
)
RETURNING show_date_id;

INSERT INTO show_times (show_date_id, start_time, end_time)
VALUES (
  (SELECT sd.show_date_id
   FROM show_dates sd
   JOIN movies m ON m.movie_id = sd.movie_id
   WHERE m.title = 'DUMMY EXAMPLE' AND sd.show_date = DATE '2025-10-01'
   ORDER BY sd.show_date_id DESC
   LIMIT 1),
  TIME '19:00', TIME '21:20'
);
```