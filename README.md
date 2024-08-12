# The One Billion Row Challenge

The One Billion Row Challenge (1BRC) was originally a fun exploration of how far modern Java can be pushed for
aggregating one billion rows from a text file. Here is the
original [blog post](https://www.morling.dev/blog/one-billion-row-challenge/),
and [repository](https://github.com/gunnarmorling/1brc).
The results were remarkable, and surprising to many, with the best attempt (for the duration of the challenge) to make
~1.5 seconds. All submissions were tested on the same hardware.

## The Challenge

The challenge is simple. There is a single txt file containing some number of rows, say one billion. Each row is a
measurement of the temperature recorded by a weather station located in a city, and it's formatted as `City-name`
followed by a semicolon `;` and finally the `temperature` with single decimal precision. For instance

```
Hamburgh;12.0
Balawayo;8.9
Palembang;28.8
St. John's;15.2
Cracow;12.6
...
```

The program should retrieve the temperature measurement values form the text file and calculate the minimum, mean, and
maximum temperature per weather station. Then, the program should print out the min, max, and mean temperature for each
station, in alphabetical order, like so:

```
{Athens=5.0/18.0/27.4, Abidjan=15.7/26.0/34.1, ... }
```

The names of the weather stations are UTF-8 encoded, and the temperature values are in the range of -99.9 to 99.9.

## Start the challenge

To start the challenge we will need the measurements file, as well as the expected output for our algorithm. To produce
them, clone the GitHub repository of the original challenge, and follow the instructions. Since the repo is cluttered with
the leaderboard and other irrelevant for us information, I am summarizing the steps below.
1. Clone the repository:
    ```no_run
    git clone --depth=1 https://github.com/gunnarmorling/1brc.git
    ```
2. Build the project using Apache Maven:
    ```no_run
    /.mvnw clean verify 
    ```
3. Create the measurements file with 1 billion rows (just once):
    ```no_run
    ./create_measurements.sh 1000000000
    ```
4. Calculate the average measurement values:
    ```no_run
    ./calculate_average_baseline.sh
    ```
5. Optimize!!!