# Compiling and Packaging the Java Servlet

Use Maven to compile and package the java servlet

Requirements:

- Maven
- java sdk 17
- docker
- docker compose

In a terminal shell, navigate to the folder containing the **docker-compose.yml** file and the **pom.xml** file.

```shell
mvn clean compile package -f pom.xml
```