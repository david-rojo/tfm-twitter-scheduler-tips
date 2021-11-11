# Heroku credentials issue

DB credentials can be checked in Heroku for app postgre database:

- Host
- Database
- User
- Port
- Password
- URI
- Heroku CLI

In order to be used by SpringBoot app are needed:

- Host
- Port
- Database
- User
- Password

Create in heroku app dashboard, following config vars:

- DB_URL
- DB_USERNAME
- DB_PASSWORD

> **_NOTE:_**  `DATABASE_URL` is created by default when DB is created, but its content is not valid

the format must be: `postgresql://<host>:<port>/<database>?user=<username>&password=<password>` that one must be used in DB_URL config var

Create same env vars as secrets in GitHub repository

Once they are created, add following configuration to properties file:

```
spring.datasource.driverClassName=org.postgresql.Driver
spring.datasource.url=jdbc:${DB_URL:**********}
spring.datasource.username=${DB_USERNAME:**********}
spring.datasource.password=${DB_PASSWORD:**********}
spring.jpa.hibernate.ddl-auto=validate
spring.flyway.baselineOnMigrate=true

#limit database connections
spring.datasource.hikari.maximum-pool-size=2
```

Add their usage to github actions workflow when tests has been executed:

```
env:
  DB_URL: ${{ secrets.DB_URL }}
  DB_USERNAME: ${{ secrets.DB_USERNAME }}
  DB_PASSWORD: ${{ secrets.DB_PASSWORD }}
```




