# Design proposal

## Domain and database

![design](../../diagrams/twitter-scheduler.png)

## REST API

| VERB   	| PATH           	| ERRORS                                                       	|
|--------	|----------------	|--------------------------------------------------------------	|
| GET    	| /pending       	|                                                              	|
| GET    	| /pending/{id}  	| NOT_FOUND                                                    	|
| POST   	| /pending       	| EXPIRED_DATE, MAXLENGTH_EXCEEDED, IMAGE_NOT_FOUND            	|
| PUT    	| /pending/{id}  	| NOT_FOUND, EXPIRED_DATE, MAXLENGTH_EXCEEDED, IMAGE_NOT_FOUND 	|
| DELETE 	| /pending/{id}  	| NOT_FOUND                                                    	|
| GET    	| /tweet         	|                                                              	|
| GET    	| /tweet/{id}    	| NOT_FOUND                                                    	|
| GET    	| /actuator/info 	|                                                              	|
| GET    	| /actuator/info 	|                                                              	|
