# Spring Boot Actuator

[Spring Boot Actuator](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html) endpoints are enabled

## enable Spring Boot Actuator

Add to `pom.xml`:

```
    <dependencies>

        <dependency>
	        <groupId>org.springframework.boot</groupId>
		    <artifactId>spring-boot-starter-actuator</artifactId>
	    </dependency>

    </dependencies>

    <build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
				<executions>
        			<execution>
            			<goals>
                			<goal>build-info</goal>
            			</goals>
        			</execution>
    			</executions>
			</plugin>
			<plugin>
			    <groupId>pl.project13.maven</groupId>
			    <artifactId>git-commit-id-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

```

## check available endpoints

To view available endpoints, when application is running:

```
curl http://localhost:8080/actuator/ | python3 -m json.tool
```

```
{
    "_links": {
        "self": {
            "href": "http://localhost:8080/actuator",
            "templated": false
        },
        "health": {
            "href": "http://localhost:8080/actuator/health",
            "templated": false
        },
        "health-path": {
            "href": "http://localhost:8080/actuator/health/{*path}",
            "templated": true
        },
        "info": {
            "href": "http://localhost:8080/actuator/info",
            "templated": false
        }
    }
}
```

## info

```
curl http://localhost:8080/actuator/info | python3 -m json.tool
```

```
{
    "git": {
        "branch": "main",
        "commit": {
            "id": "5858565",
            "time": "2021-10-22T14:07:57Z"
        }
    },
    "build": {
        "artifact": "twitter-scheduler",
        "name": "twitter-scheduler",
        "time": "2021-10-22T14:20:35.144Z",
        "version": "0.0.1-SNAPSHOT",
        "group": "com.mastercloudapps"
    }
}
```

## health

```
curl http://localhost:8080/actuator/health | python3 -m json.tool
```

```
{
    "status": "UP"
}
```

## how to enable all actuator endpoints

Add to `application.properties` file:

```
management.endpoints.web.exposure.include=*
```

To view all endpoints, when application is running:

```
curl http://localhost:8080/actuator/ | python3 -m json.tool
```

```
{
    "_links": {
        "self": {
            "href": "http://localhost:8080/actuator",
            "templated": false
        },
        "beans": {
            "href": "http://localhost:8080/actuator/beans",
            "templated": false
        },
        "caches-cache": {
            "href": "http://localhost:8080/actuator/caches/{cache}",
            "templated": true
        },
        "caches": {
            "href": "http://localhost:8080/actuator/caches",
            "templated": false
        },
        "health": {
            "href": "http://localhost:8080/actuator/health",
            "templated": false
        },
        "health-path": {
            "href": "http://localhost:8080/actuator/health/{*path}",
            "templated": true
        },
        "info": {
            "href": "http://localhost:8080/actuator/info",
            "templated": false
        },
        "conditions": {
            "href": "http://localhost:8080/actuator/conditions",
            "templated": false
        },
        "configprops": {
            "href": "http://localhost:8080/actuator/configprops",
            "templated": false
        },
        "configprops-prefix": {
            "href": "http://localhost:8080/actuator/configprops/{prefix}",
            "templated": true
        },
        "env": {
            "href": "http://localhost:8080/actuator/env",
            "templated": false
        },
        "env-toMatch": {
            "href": "http://localhost:8080/actuator/env/{toMatch}",
            "templated": true
        },
        "loggers": {
            "href": "http://localhost:8080/actuator/loggers",
            "templated": false
        },
        "loggers-name": {
            "href": "http://localhost:8080/actuator/loggers/{name}",
            "templated": true
        },
        "heapdump": {
            "href": "http://localhost:8080/actuator/heapdump",
            "templated": false
        },
        "threaddump": {
            "href": "http://localhost:8080/actuator/threaddump",
            "templated": false
        },
        "metrics-requiredMetricName": {
            "href": "http://localhost:8080/actuator/metrics/{requiredMetricName}",
            "templated": true
        },
        "metrics": {
            "href": "http://localhost:8080/actuator/metrics",
            "templated": false
        },
        "scheduledtasks": {
            "href": "http://localhost:8080/actuator/scheduledtasks",
            "templated": false
        },
        "mappings": {
            "href": "http://localhost:8080/actuator/mappings",
            "templated": false
        }
    }
}
```

