# Design proposal

## Domain and database

![design](../../diagrams/twitter-scheduler.png)

## REST API

| VERB   	| PATH                           	| ERRORS                                                       	|
|--------	|--------------------------------	|--------------------------------------------------------------	|
| GET    	| /                              	|                                                              	|
| GET    	| /pending                       	|                                                              	|
| GET    	| /pending/{id}                  	| NOT_FOUND                                                    	|
| GET    	| /pending/{startDate}/{endDate} 	| END_DATE_EARLIER_THAN_START_DATE                             	|
| POST   	| /pending                       	| MAX_LENGTH_EXCEEDED, IMAGE_NOT_FOUND, EXPIRED_DATE           	|
| PUT    	| /pending/{id}                  	| NOT_FOUND, MAXLENGTH_EXCEEDED, IMAGE_NOT_FOUND, EXPIRED_DATE 	|
| DELETE 	| /pending/{id}                  	| NOT_FOUND                                                    	|
| GET    	| /tweets                        	|                                                              	|
| GET    	| /tweets/{id}                   	| NOT_FOUND                                                    	|
| GET    	| /tweets/{startDate}/{endDate}  	| END_DATE_EARLIER_THAN_START_DATE                             	|
| GET    	| /actuator/info                 	|                                                              	|
| GET    	| /actuator/health               	|                                                              	|
