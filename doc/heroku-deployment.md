# Heroku deployment

## Add server port

Include in `application.properties`

```
server.port=8080
```

## Use exposed port when execute app

`Dockefile` content:

```
FROM openjdk:11-jre
COPY target/*.jar /opt/webapp.jar
CMD java -Dserver.port=$PORT $JAVA_OPTS -jar /opt/webapp.jar
```

## Add job

Include in `push-main.yml`

```
  build_and_deploy_in_heroku:
    name: Publish and deploy in Heroku
    runs-on: ubuntu-20.04
    needs: [run_tests_build_app]
    env:
      IMAGE_NAME: twitter-scheduler-tfm
      HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
      HEROKU_APP_NAME: ${{ secrets.HEROKU_APP_NAME }}
    steps:
      - name: Clone repository
        uses: actions/checkout@v2
      - name: Download jar from previous job
        uses: actions/download-artifact@v2
        with:
          name: target
          path: target
      - name: Heroku Container Registry login
        run: heroku container:login 
      - name: Build and push
        run: heroku container:push -a $HEROKU_APP_NAME web 
      - name: Release
        run: heroku container:release -a $HEROKU_APP_NAME web
```

Heroku CLI and Docker are available within the virtual environment provided to the runners, when using Ubuntu, so is not needed to install them