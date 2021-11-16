# Twitter Scheduler TFM tips

Heroku info endpoint: [https://twitter-scheduler-tfm.herokuapp.com/actuator/info](https://twitter-scheduler-tfm.herokuapp.com/actuator/info)

## Meetings

- [22/07/2021: Kickoff](doc/meetings/20210722-kickoff.md)
- [29/10/2021: Follow Up](doc/meetings/20211029-followup.md)
- [11/2021: Follow up](doc/meetings/202111-followup.md)

## Project documentation

 - [Design proposal](doc/design/design.md)

## OpenApi

- [SpringDoc-OpenApi v1.5.12 official doc](https://springdoc.org/)
- [OpenApi securization](doc/openapi/openapi-securization.md)
- [Baeldung: How to Turn Off Swagger-ui in Production](https://www.baeldung.com/swagger-ui-turn-off-in-production)
- [Sort endpoints alphabetically](https://springdoc.org/index.html#how-can-i-sort-endpoints-alphabetically)

## Hexagonal

- [Baeldung: Organizing Layers Using Hexagonal Architecture, DDD, and Spring](https://www.baeldung.com/hexagonal-architecture-ddd-spring)
- [Hands-on Hexagonal Architecture With Spring Boot](https://medium.com/javarevisited/hands-on-hexagonal-architecture-with-spring-boot-ca61f88bed8b)
- *[Hexagonal Architecture with Java and Spring](https://reflectoring.io/spring-hexagonal/)
- [Domain-Driven Design and the Hexagonal Architecture](https://vaadin.com/learn/tutorials/ddd/ddd_and_hexagonal) --> domain exceptions

## Spring Boot

- [Spring Boot Actuator is enabled in the project](doc/springboot/spring-boot-actuator.md)
- [GitHub secret usage as property in Java code](doc/springboot/github-secret-usage-as-property.md)
- [Spring Profiles](doc/springboot/profiles.md)

## H2 database

- [Baeldung: Spring Boot With H2 Database](https://www.baeldung.com/spring-boot-h2-database)
- [Add H2 Database to Spring Boot Project with Spring Security](https://www.appsdeveloperblog.com/add-h2-database-to-spring-boot-project-with-spring-security/)

## Flyway

- [Database Migrations with Flyway](https://www.baeldung.com/database-migrations-with-flyway)
- [Build a Spring Boot App With Flyway and Postgres](https://dzone.com/articles/build-a-spring-boot-app-with-flyway-and-postgres)
- Práctica 02-servicios-internet/03-persistencia-datos/practica-02

## Resilience

- [Baeldung: Guide to Try in Vavr](https://www.baeldung.com/vavr-try)
- [Resilience4j](https://github.com/resilience4j/resilience4j)

## Scheduled

- [Spring scheduled tasks](doc/springboot/scheduled-tasks.md)
- [Expressing fixedRateString and initialDelayString with Duration](https://docs.oracle.com/javase/8/docs/api/java/time/Duration.html?is-external=true#parse-java.lang.CharSequence-)
- [Baeldung: How to test @Scheduled annotation](https://www.baeldung.com/spring-testing-scheduled-annotation)

## Feature Flags

### Togglz

- [togglz](doc/springboot/togglz.md)
- [togglz spring boot starter](https://www.togglz.org/documentation/spring-boot-starter.html)
- [authentication](https://www.togglz.org/documentation/authentication.html)
- [configuration](https://www.togglz.org/documentation/configuration.html)
- [StackOverflow: Spring Boot Togglz - no qualifying bean of type UserProvider error](https://stackoverflow.com/questions/41263339/spring-boot-togglz-no-qualifying-bean-of-type-userprovider-error)
- [StackOverflow: How to enable togglz-console in spring-boot application](https://stackoverflow.com/questions/36352832/how-to-enable-togglz-console-in-spring-boot-application)

### FFJ4

- [FF4J main page](https://ff4j.github.io/)
- [GitHub FF4J examples](https://github.com/ff4j/ff4j-samples)

## Twitter

- [Twitter developer platform: tools and libraries](https://developer.twitter.com/en/docs/twitter-api/tools-and-libraries)
- [Baeldung: Introduction to TwitterJ](https://www.baeldung.com/twitter4j)
- [How to post image tweets to Twitter using Twitter4j Java API](https://roytuts.com/how-to-post-image-tweets-to-twitter-using-twitter4j-java-api/)
- [Twitter4J](https://github.com/Twitter4J/Twitter4J)
- Tweet url: `https://twitter.com/BlueOcean_TFM/status/1458162214926434316`
    - `BlueOcean_TFM` is `user.getScreenName()`
    - `1458162214926434316` is `status.getId()`

## Heroku

- [Deploy to Heroku](https://github.com/marketplace/actions/deploy-to-heroku)
- [Deploying to Heroku from GitHub Actions](https://dev.to/heroku/deploying-to-heroku-from-github-actions-29ej)
- [SpringBoot with GitHub Actions and Heroku](https://github.com/gcatanese/SpringBootService)
- [Getting Started on Heroku with Java](https://devcenter.heroku.com/articles/getting-started-with-java)
- [StackOverflow: Deploying Spring boot App, to Heroku With Docker using github](https://stackoverflow.com/questions/66259266/deploying-spring-boot-app-to-heroku-with-docker-using-github)
- [Go on Heroku: Continuous Deployment with GitHub](https://www.youtube.com/watch?v=sffWuu7XBN4)

## Heroku env vars

- [heroku container:push](https://devcenter.heroku.com/articles/heroku-cli-commands#heroku-container-push)
- [Docker env vars + Heroku; Heroku requires ENV while local build requires ARG](https://stackoverflow.com/questions/49476481/docker-env-vars-heroku-heroku-requires-env-while-local-build-requires-arg)
- [Custom GitHub action heroku-deploy](https://github.com/AkhileshNS/heroku-deploy)

## Heroku DB

- [Credentials issue in springboot](doc/springboot/heroku-credentials.md)
- [How to set up a free PostgreSQL database on Heroku](https://dev.to/prisma/how-to-setup-a-free-postgresql-database-on-heroku-1dc1)
- *[Spring how to limit db connections](https://stackoverflow.com/questions/47141176/spring-boot-psqlexception-fatal-sorry-too-many-clients-already-when-running)

## Unitary Tests

- [Spring boot MockMVC example](https://howtodoinjava.com/spring-boot2/testing/spring-boot-mockmvc-example/)
- [Testing with Spring Boot and @SpringBootTest](https://reflectoring.io/spring-boot-test/)
- [Baeldung: How to test @Scheduled annotation](https://www.baeldung.com/spring-testing-scheduled-annotation)

## Integration Tests

- [Integration testing](doc/springboot/integration-testing.md)

## Smoke tests

- [Smoke tests](doc/test/smoke-test.md)
- [Github Action for curl](https://github.com/marketplace/actions/github-action-for-curl)
- [Getting started with GitHub Actions](https://itnext.io/getting-started-with-github-actions-fe94167dbc6d)
- [Using cURL with a username and password?](https://stackoverflow.com/questions/2594880/using-curl-with-a-username-and-password)
- [How to capture a curl http status code in a GitHub Action to determine success/failure?](https://stackoverflow.com/questions/65728933/how-to-capture-a-curl-http-status-code-in-a-github-action-to-determine-success-f)
- [Using GitHub actions for integration testing on a REST API](https://medium.com/weekly-webtips/using-github-actions-for-integration-testing-on-a-rest-api-358991d54a20)

## Coverage

- [Jacoco configuration in the project](doc/springboot/jacoco.md)
- [GitHub Actions CI pipeline: GitHub Packages, Codecov, release to Maven Central & GitHub](https://blog.codecentric.de/en/2021/02/github-actions-pipeline/)
- **[HOWTO SONARQUBE: Continuous Integration of Java project with GitHub Actions](https://faun.pub/continuous-integration-of-java-project-with-github-actions-7a8a0e8246ef)
  - [github repo](https://github.com/wkrzywiec/NoticeBoard)


## Misc

- [How to Add an Image to Github for a Project's Social Media Preview](doc/misc/github-add-image-social-media-preview.md)
