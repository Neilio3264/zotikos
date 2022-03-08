# ZOTIKOS
Zotikos is a C++ custom logging application. The goal of the logger is to provide reliable performance while operating in a thread safe manner. Therefore, the logger runs as a singleton, making use of threads to handle file output
It is intended to be modular requiring only a few changes to run in unison with any application.

The current setup originates from an operating systems course which can be found [here](https://github.com/Neilio3264/CS4348-OperatingSystems-Project01)

+ If changes need to be made for your use, only `zotikos.cpp` should require changes. 
+ If you would like to customize the states, the files requiring changes are `log_stream.cpp`, and `log_states.h`.
+ If you would like to customize output methods ***(beyond changing the log file name)*** the only change needed is modifying print() in `logger.cpp`

## File List

   1. `zotikos.cpp`: the main file for the log program. The pattern followed for the single instance logger is similar to ostream with cout.
   2. `logger.cpp`: the goal of this file is to define the logger class such that it is thread safe. The main logic of the log program resides in *print*. In this method, you write to the file if the queue has data to be read. Otherwise, you set the thread to periodically check the queue and allow the thread to sleep for a set duration.
   3. `log_stream.cpp`: this file simply houses the creation of the output string that will be sent to the file. It combines the time, state, and input to the stream.
   4. `logger.h`: this file defines the logger class as a singleton and also includes the *log_stream* link to the actual logger object.
   5. `log_stream.h`: this file defines the stream class. It also inherits ostream so that the logger can be utilized like cout with overloaded operators.
   6. `timeutil.h`: a simple util file that grabs and formats the time as per the logger requirements.
   7. `log_states.h`: a file that defines enums with the possible states that the logger must handle.

## Compile and Run

To compile this code, I have created a makefile withing the /src directory.

In order to run, `cd` to the indicated directory (or include the path in the command) and first run `make clean`. This will ensure any existing object files are removed for a fresh run. Next run `make`.

If the make is successful, an output file should be created in /bin. To run the exe, cd to the /bin folder and run `./[exe]` (**assuming UNIX system**).

>NOTE: By default, the output log file will be created under /log as *driver.log*. To pass a different file name and location, include the file directory as a command line argument.
