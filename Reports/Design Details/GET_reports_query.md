# List all reports that match the query

Usage
```
   GET /reports?{location}&{key_terms}&{date}
```
## Description
Returns a list of the reports that match the following query.

## Parameters
- **n** - The number of results that are returned. This number is defaulted to 10 and can only return up to 100 results.
- **location** - Geocode of the area affected
- **key_terms** - This input contains a comma separated list of all the key terms you want to get news about.
This input can be empty or omitted in the case where the user doesn’t want to restrict his search. This is not case sensitive.
- **date** - A date can be either a date-exact or a date-range.
    - **date_exact** - yyyy-mm-ddThh:mm:ss format. Year is mandatory, every other segment is optional.
Use 'x' character if missing. Strings must match the following regular expression:
`^(\d{4})-(\d\d|xx)-(\d\d|xx)T(\d\d|xx):(\d\d|xx):(\d\d|xx)$`
    - **date-range** - Let `d1` and `d2` both be of format date-exact (see section above). Then, date-range must follow format:
`d1 to d2`
and furthermore `d1` must be a date before `d2`.


## Errors

| Code | Description |
| ---- | ---------- |
| 200  | Successful |
| 400  | Invalid Location or Key Term or Date |

## Example

### Request
```
   curl http://exampleapi.com/reports?location=1566083&key_terms=Anthrax&date=2019 -X "GET" -H "Content-Type: application/json"
```
### Response
#### Snippet of the response ####
```JSON

   Status: 200 OK
   Content-Type: application/json

   {
       "url": "www.outbreaks.globalincidentmap.com/eventdetail.php?ID=31146",
       "date_of_publication": "2019-02-27T23:20:00 ",
       "headline": "TANZANIA - Anthrax kills two people in northern Tanzania",
       "main_text": "2 people died and 8 others were hospitalized following an anthrax outbreak...",
       "reports": [
           {
               "disease": [
                   "anthrax",
               ],
               "syndrome": [],
               "reported_events": [
                   {
                       "type": "death",
                       "date": "2018-12-01T23:20:00 to 2018-12-10T23:50:00",
                       "location": {
                           "geonames-id": 1566083
                       },
                       "number-affected": 2
                   },
               ],
               "Comment": null
           }
       ]
   }
```
