# Design proposal

## Domain and database

![design](../../diagrams/twitter-scheduler.png)

## REST API

### Mandatory

| VERB   | PATH             | ERRORS                                             |
|--------|------------------|----------------------------------------------------|
| GET    | /                |                                                    |
| GET    | /pending         |                                                    |
| GET    | /pending/{id}    | NOT_FOUND                                          |
| POST   | /pending         | MAX_LENGTH_EXCEEDED, IMAGE_NOT_FOUND, EXPIRED_DATE |
| DELETE | /pending/{id}    | NOT_FOUND                                          |
| GET    | /tweets          |                                                    |
| GET    | /tweets/{id}     | NOT_FOUND                                          |
| GET    | /actuator/info   |                                                    |
| GET    | /actuator/health |                                                    |

### Optional

| VERB | PATH                           | ERRORS                                                       |
|------|--------------------------------|--------------------------------------------------------------|
| GET  | /pending/{startDate}/{endDate} | END_DATE_EARLIER_THAN_START_DATE                             |
| PUT  | /pending/{id}                  | NOT_FOUND, MAXLENGTH_EXCEEDED, IMAGE_NOT_FOUND, EXPIRED_DATE |
| GET  | /tweets/{startDate}/{endDate}  | END_DATE_EARLIER_THAN_START_DATE                             |
