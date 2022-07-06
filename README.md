# Exercise 2

The Bluefruit finance department need to know how many people have worked on specific projects so they can check they are billing clients the correct amount.

You have been tasked with writing a script that will be run at the end of every week to process and transfer the timesheet records to the accounting system. You do not need to implement the scheduling to run the script.

## Process

1. Fetch the source data

The souce data can be access by sending a ```HTTP GET``` request to ```https://timetracking.bluefruit.co.uk/api/days```

The returned JSON data will be formatted as below:

```json
[
  {
    "name": "bob",
    "project": "synth",
    "start": "2022-06-28",
    "end": "2022-06-29"
  },
  {
    "name": "frank",
    "project": "fridge",
    "start": "2022-07-01",
    "end": "2022-07-05"
  },
  {
    "name": "alice",
    "project": "synth",
    "start": "2022-06-27",
    "end": "2022-07-05"
  }
]
```

2. Generate CSV data

Generate CSV data containing the number of people working on each project for the date range of the data.

For example the example response data above would generate the following CSV file:

```csv
date,synth,fridge
2022-06-27,1,0
2022-06-28,2,0
2022-06-29,2,0
2022-06-30,1,0
2022-07-01,1,1
2022-07-02,1,1
2022-07-03,1,1
2022-07-04,1,1
2022-07-05,1,1
```

3. Upload the CSV

Upload the CSV data using a ```HTTP PUT``` request to ```https://accounts.bluefruit.co.uk/upload/<id>.csv``` where ```id``` is a UUID (or GUID) you have generated.

The ```PUT``` request will require a key sent as a HTTP header to allow the data to be uploaded.

```upload-key:95341ee6-4efc-4148-9619-b4b800b9eeb6```

The response to the ```PUT``` request will indicate if the upload was successful or not.

On success:
```json
{"result": "ok"}
```

On failure:
```json
{"result": "fail"}
```

# Submission

Send us:
* The source code that you wrote to complete the exercise either as a zip file of your git repository or the source code
* The UUID or GUID you generated in step 3