Traffic Simulation:
A C++ program that simulates cars on a single road, second by second, and shows how many cars are on the road over time.

What the simulation does:
Every second, three things happen. First, new cars arrive, about 4 per second on average (a random number from a Poisson distribution). If the road is full (200 cars), no new cars can enter. Second, some cars leave (binomial distribution). The more crowded the road, the smaller the chance that a car leaves, because cars cannot move well in traffic. Third, a crash can happen. Once per day the program checks whether a crash occurs. The chance depends on the day of the week and comes from real data in the file CRASH_LANCASTER_2024.db. After a crash, no cars can leave for 10 minutes.
At the end, the program prints statistics in the terminal and creates a plot in the file plot.html.

Files:

Sim.cpp: the main program, the simulation loop, and the output to the terminal and to HTML.
Sim_Math.cpp and Sim_Math.h: random numbers, percentages, the day of the week, and reading the crash database.
TimeCode.cpp and TimeCode.h: a class that stores time (hours:minutes:seconds).
BigInteger.cpp and BigInteger.h: a class for very large integers, used to count the total number of cars.
Tests.cpp, TimeCodeTests.cpp, BigIntegerTests.cpp and the _Tests.h files: the tests.
CRASH_LANCASTER_2024.db and .csv: the crash data. The program reads the .db file.
Makefile: builds the program and the tests.

What to install (Ubuntu / WSL):
sudo apt update && sudo apt install -y build-essential libsqlite3-dev
Build

To run:
./traffic-simulation <duration_in_seconds>

Example:
./traffic-simulation 10000
The duration must be a positive whole number. Use at least 7800 seconds.

What the program prints:
In the terminal: the duration, the road capacity, new cars per second, the number of crashes, the total number of cars, and how many seconds had 0, 1, 2, or 10 or fewer cars.

How to measure the running time:
time ./traffic-simulation 10000
