# pglog
toy log framework which can work with slf4j

## design
1. [LogEvent](./src/main/java/org/slf4j/impl/LogEvent.java) 
   every LogEvent instance is a single log message.
2. [Logger](./src/main/java/org/slf4j/impl/LogHandler.java)
   Use it to create a log, it can be output to console or file or both by [ConsoleLogHandler](./src/main/java/org/slf4j/impl/ConsoleLogHandler.java) with different formats generated by different [EventParser](./src/main/java/org/slf4j/impl/EventParser.java). 
   Loggers have inheritance behavior, if the handler wasn't specified, the Logger instance will use the handler of its 
   parent Logger, so will its parent. There is a Logger instance called "root", it is the ancestor of every Logger 
   instance. 
3. [Level](./src/main/java/org/slf4j/impl/Level.java)
   Every loggerEvent has its level, if this level is not lower than the effectiveLevel of its Logger's handler, 
   the loggerEvent will be output.
    
    

## configuration
1. log output to console or file or both?
   that's what [LogHandler](./src/main/java/org/slf4j/impl/LogHandler.java) is for.
2. how log info was presented?


## todo 
1. add configuration function
2. make error level special
3. add file logHandler