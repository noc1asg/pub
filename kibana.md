# some tips 

filter 
```{
  "query": {
    "bool": {
      "should": [
        {
          "match_phrase": {
            "Code": "100060004"
          }
        },
        {
          "match_phrase": {
            "Code": "100060005"
          }
        },
        {
          "match_phrase": {
            "Code": "100060007"
          }
        }
      ],
      "minimum_should_match": 1
    }
  }
}
```
