# Design proposal

## Domain and database

![design](../../diagrams/twitter-scheduler.png)

## REST API

### Mandatory

| VERB   | PATH                  | ERRORS                                             |
|--------|-----------------------|----------------------------------------------------|
| GET    | /                     |                                                    |
| GET    | /api/pending          |                                                    |
| GET    | /api/pending/{id}     | NOT_FOUND                                          |
| POST   | /api/pending          | MAX_LENGTH_EXCEEDED, IMAGE_NOT_FOUND, EXPIRED_DATE |
| DELETE | /api/pending/{id}     | NOT_FOUND                                          |
| GET    | /api/tweets           |                                                    |
| GET    | /api/tweets/{id}      | NOT_FOUND                                          |
| GET    | /api/scheduler/status |                                                    |
| GET    | /actuator/info        |                                                    |
| GET    | /actuator/health      |                                                    |

### Optional

| VERB | PATH                               | ERRORS                                                       |
|------|------------------------------------|--------------------------------------------------------------|
| GET  | /api/pending/{startDate}/{endDate} | END_DATE_EARLIER_THAN_START_DATE                             |
| PUT  | /api/pending/{id}                  | NOT_FOUND, MAXLENGTH_EXCEEDED, IMAGE_NOT_FOUND, EXPIRED_DATE |
| GET  | /api/tweets/{startDate}/{endDate}  | END_DATE_EARLIER_THAN_START_DATE                             |
