# Exercise 1

Cyber-Dojo is a great environment for learning about coding and test-driven development. This isn’t a pass/fail test it allows us to see how you approach a problem and gives us an insight into your current ability.

Please watch the following short video. It will give you a very clear idea of what we are looking for:

TDD in cyber-dojo ([https://www.youtube.com/watch?v=P0SaJlNyWMk](https://www.youtube.com/watch?v=P0SaJlNyWMk))

Please complete both the "Print Diamond" exercise.

We attach equal importance to the test code and the code. Do not write the code elsewhere and paste it into Cyber-Dojo; we will review your process and all the traffic light steps.

To attempt the "Print Diamond" exercise:

1. Navigate to [https://cyber-dojo.bluefruit.software/](https://cyber-dojo.bluefruit.software/)
2. Click “Create”
3. Select your programming language
4. Select the “Print Diamond” exercise
5. Make a note of your dojo’s ID. This is the six-digit hex code.
6. Click “Enter”
7. Complete the exercise to your best ability.

# Exercise 2

The Bluefruit finance department need to know how many people have worked on specific projects so they can check they are billing clients the correct amount.

You have been tasked with writing a script that will be run at the end of every week to process and transfer the timesheet records to the accounting system. You do not need to implement the scheduling to run the script.

## Process

1. Fetch the source data

The source data can be accessed by sending an ```HTTP GET``` request to ```https://timetracking.bluefruit.software/api/days```

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

Upload the CSV data using an ```HTTP PUT``` request to ```https://accounts.bluefruit.software/upload/<id>.csv``` where ```id``` is a UUID (or GUID) you have generated.

The ```PUT``` request will require a key sent as an HTTP header to allow the data to be uploaded.

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

Once you've completed both exercises, please send:

* From exercise 1
  * The full URL which includes your unique dojo ID. It would also be helpful for you to indicate how long you spent on each exercise.
* From exercise 2
  * The source code that you wrote to complete the exercise either as a zip file of your git repository or the source code
  * The UUID or GUID you generated in step 3
