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
curl -s --get "http://localhost:8080/api/movies/search-upcoming" --data-urlencode "month=10" --data-urlencode "year=2025" | jq
  
# Full date
curl -s --get "http://localhost:8080/api/movies/search-upcoming" --data-urlencode "month=12" --data-urlencode "day=1" --data-urlencode "year=2025" | jq

# Title + genres + full date
curl -s --get "http://localhost:8080/api/movies/search-upcoming" \
--data-urlencode "title=old" \
--data-urlencode "genres=Thriller,Crime" \
--data-urlencode "month=11" --data-urlencode "day=15" --data-urlencode "year=2025" | jq
```