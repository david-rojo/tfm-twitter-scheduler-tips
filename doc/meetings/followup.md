# Follow up

## Progress

- Created Spring Boot maven project structure in [repository](https://github.com/MasterCloudApps-Projects/TwitterScheduler) with Spring Boot Actuator enabled
- [DockerHub repository](https://hub.docker.com/repository/docker/drojo/twitter-scheduler-tfm)
- CI/CD ready [GitHub actions workflow](https://github.com/MasterCloudApps-Projects/TwitterScheduler/actions) on every push on main branch:
  - unit tests executed
  - docker image built and published in DockerHub
  - heroku image built and deployed
- [Heroku app info endpoint](https://twitter-scheduler-tfm.herokuapp.com/actuator/info)
- Twitter account: [@BlueOcean_TFM](https://twitter.com/BlueOcean_TFM)
- Twitter API:
  - registration
  - PoC: [twitter-publisher](https://github.com/david-rojo/twitter-publisher)
- [Project logo](http://davidrojo.eu/images/tfm/1.jpg)

## Questions

- Heroku documentation application with DB?
- Use repository secrets in properties? Needed for Twitter API credentials:
```
  oauth.consumerKey=<consumer_key>
  oauth.consumerSecret=<consumer_secret>
  oauth.accessToken=<access_token>
  oauth.accessTokenSecret=<access_token_secret>
```
- [Design proposal](../design/design.md):
  - Domain
  - Database
  - REST API endpoints
