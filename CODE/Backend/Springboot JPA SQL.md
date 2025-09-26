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



## JPA Repository Derived Methods (Predefined)
### findBy*ColumnField*IgnoresCase(*Param*)
```
return movieRepository.findByGenresIgnoreCase(first); 
// looks for exact matches of "Action" and not ",Action,"
```
