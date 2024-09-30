# Read Me First

The following original idea is from  
https://medium.com/@facuramallo8/understanding-logback-66044df087ed

Also see  
https://medium.com/@facuramallo8/understanding-logback-66044df087ed

# Logback

Logback is divided into three modules:

1. logback-core
2. logback-classic
3. logback-access

# Logback Core Module

The core module lays the groundwork for the other two modules.

# Logback Classic Module - Application Logs

The classic module extends core and corresponds to a significantly improved version of log4j. Logback-classic
natively implements the SLF4J API.

For this we need spring-boot-starter-logging
**Files**
The following files are provided under org/springframework/boot/logging/logback/

1. **defaults.xml**
   Provides conversion rules, pattern properties, and common logger configurations.
2. **console-appender.xml**
   Adds a ConsoleAppender named CONSOLE that uses the CONSOLE_LOG_PATTERN to format the message.
3. **file-appender.xml**
   Adds a RollingFileAppender named FILE using the FILE_LOG_PATTERN and ROLLING_FILE_NAME_PATTERN with appropriate
   settings.
4. **base.xml** - legacy
   Provided for compatibility with earlier versions of Spring Boot.

# Logback Access Module - Servlet Logs

The third module, access, integrates with Servlet containers to provide HTTP-access logging functionality.

By default, the access logs aren’t enabled. We can enable them by adding a property to “application.yaml” file:

```
server.tomcat.accesslog.enabled: true
```

but this configuration only allows to use default logging format and storing log events to a file in a temporary
directory.

To enable logback-classic functionality but in the scope of HTTP access logging, we need to use the logback-access
module
that integrates with Servlet containers such as Jetty or Tomcat.

The easiest way to configure logback-acces in our Spring-Boot application is to use the
logback-access-spring-boot-starter. This starter uses the configuration file specified in application.yaml which is
logback-access-spring.xml for this project
