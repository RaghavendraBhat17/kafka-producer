# kafka-producer


Gradle based project which reads from a file under resources directory and pushes it to a topic. The records pushed to a topic are then consumed by a downstream spark application https://github.com/RaghavendraBhat17/spark-ddos-java/ to find out if there are any DDOS attacks. Under resource directory there are 2 text files as described below:

- Project-Developer-apache-access-log.txt : This file does not have IP addresses that cause DDOS attack
- access-log-with-ddos.txt: This file has IP addresses that cause DDOS attack

### Build artifact

```sh
gradle clean build
```
- The artifact will be generated under build/distributions folder

### Running application

- Make sure is kafka is running before running this application
- The downstream spark application should be started before running this application 
- Untar the artifact from build/distributions folder
- Navigate to bin folder
```sh
./kafka-producer <topic name> <access log file name with extension>
Example: ./kafka-producer test-topic access-log-with-ddos.txt
```
