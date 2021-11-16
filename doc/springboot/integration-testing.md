# Integration testing

In order to be tested, application provide a set of integration tests.

## Add Rest Assured dependency

```
	<dependency>
		<groupId>io.rest-assured</groupId>
		<artifactId>rest-assured</artifactId>
		<scope>test</scope>
	</dependency>
```

## Add Integration Test

Create package `com.mastercloudapps.twitterscheduler.integration` where all integration tests will be placed

Create the class with format `<target_class_for_testing>IT.java`, for example, PendingApiControllerIT:

```
@Profile("standalone")
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
@DisplayName("PendingApiController REST tests - RESTAssured")
public class PendingApiControllerIT {

    ...
}

```

# Executing only Integration Tests

```
mvn -B -Dtest=*IT -Dspring.profiles.active=standalone test
```

If you want to execute only unitary tests:

```
mvn -B -Dtest=*Test* test
```

These can be used in GitHub actions to perform specific tests when needed.

