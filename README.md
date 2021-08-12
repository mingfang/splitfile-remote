# splitfile-remote
demonstrate problem running splitfile against remote splitgraph

## To see working scenario
- Edit `splitfile-remote/rdu-weather-summary.splitfile`
    - Uncomment line 5, `FROM demo/weather IMPORT rdu AS source_data`
    - Comment out line 8, `FROM demo/weather IMPORT {SELECT * FROM rdu} AS source_data`
- Running `./run_example.py --no-pause ./splitfile-remote/example.yaml` should complete with no errors

## To see error condition, reverse the above
- Edit `splitfile-remote/rdu-weather-summary.splitfile`
    - Comment out line 5, `FROM demo/weather IMPORT rdu AS source_data`
    - Uncomment line 8, `FROM demo/weather IMPORT {SELECT * FROM rdu} AS source_data`
- Running `./run_example.py --no-pause ./splitfile-remote/example.yaml` should print the errors below

```
...
Step 1/2 : FROM demo/weather IMPORT {SELECT * FROM rdu} AS source_data
Resolving repository demo/weather
Gathering remote metadata...
Fetched metadata for 2 images, 1 table, 0 objects and 1 tag.
Importing 1 table from demo/weather:40b49c9c5ba9 into demo/summary
error: psycopg2.errors.InternalError_: Error in python: KeyError
error: DETAIL:  'engine_remote'
```



