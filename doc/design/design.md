# Design proposal

## Domain and database

![design](../../diagrams/twitter-scheduler.png)

## REST API

| VERB   | PATH           |
|--------|----------------|
| GET    | /pending       |
| GET    | /pending/{id}  |
| POST   | /pending       |
| PUT    | /pending/{id}  |
| DELETE | /pending/{id}  |
| GET    | /tweet         |
| GET    | /tweet/{id}    |
| GET    | /actuator/info |
| GET    | /actuator/info |
