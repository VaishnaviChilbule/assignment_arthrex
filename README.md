Problem Statement->
This repository contains a simple logger module implemented in Python, which can be seamlessly integrated into any codebase. The logger module 
supports log rotation and is designed to work in a multithreaded environment.

Features
1.Logs messages to a file at a specified location.
2.Log messages include:
-Timestamp
-Log level (DEBUG, INFO, ERROR)
-File name (source code file from which the log was created)
-Function name (function name from which log creation was invoked)
-Thread ID
-Actual log message
3.Log file rotation after every 5 MB, with a limit of 10 rotations. Old logs will be automatically wrapped around.

Description->
A logger module is a software component designed to handle the logging of messages from a program. Logging is essential for tracking 
the behavior of an application, debugging, and auditing. A logger module allows you to record events, errors, and informational messages to 
a variety of destinations, such as console output, files, or remote logging servers.

Key Features of a Logger Module
Log Levels:
1.DEBUG: Detailed information, typically of interest only when diagnosing problems.
2.INFO: Confirmation that things are working as expected.
3.WARNING: An indication that something unexpected happened or indicative of some problem in the near future (e.g., ‘disk space low’). The software is still working as expected.
4.ERROR: Due to a more serious problem, the software has not been able to perform some function.
5.CRITICAL: A serious error, indicating that the program itself may be unable to continue running.

Log Message Components:
1.Timestamp: When the log entry was created.
2.Log Level: The severity of the log message.
3.Source Information: The file name, function name, and optionally the line number where the log entry was created.
4.Thread Information: The ID of the thread that created the log entry (useful in multithreaded applications).
5.Message: The actual log message.

Log Handlers:
1.Console Handler: Outputs log messages to the console (standard output).
2.File Handler: Writes log messages to a file, with optional support for log rotation (e.g., splitting logs by size or date).
3.Remote Handler: Sends log messages to a remote server or logging service.
4.Rotation file handler:writes log messages to a file of specified file size with rotation.

Log Formatters:
Define the structure of log messages. They determine how the timestamp, log level, and message are formatted and combined.

Log Rotation:
Automatically manage log files by creating new files after reaching a certain size or after a certain period, and optionally removing old log files.


Integration
To integrate this logger module into any codebase:

1.Import the Logger:
 import customizedlogger
2.Get the Logger Instance:
 logger = CustomizedLogger().get_logger()
3.Log Messages:
 logger.debug('Debug message')
 logger.info('Info message')
 logger.error('Error message')

-Make Ensure the log file path provided to CustomizeLogger (which is demoapplication log in my code)is writable and accessible.
-Adjust the max_bytes and backup_count parameters as needed.
-Customize the logging format further if required by modifying the formatter string.


Using the Logger in a Multithreaded Environment:
Logger Setup:
The CustomizedLogger sets up the logger with a rotating file handler and a formatter.
It ensures that the logger only adds handlers once.

Logging in Functions:
The application function logs messages with different log levels, including the thread name in the log message to distinguish messages 
from different threads.

Thread Function:
The thread_function simulates a multithreaded environment by logging messages indicating the start and finish of each thread, and by 
calling example_function to log additional messages.
Multithreaded Execution:

The __main__ block creates and starts multiple threads, each running thread_function.
It waits for all threads to complete using join.

Test cases:-
To ensure the logger module works correctly, especially in a multithreaded environment, we can write a few test cases. 
These test cases will verify:

1.The logger correctly writes messages to the log file.
2.The log file rotates after reaching the specified size.
3.Multiple threads can log messages without conflicts.
