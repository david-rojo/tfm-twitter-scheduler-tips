# Smoke tests

```
  smoke_tests:
    name: Smoke tests
    runs-on: ubuntu-20.04
    needs: [build_and_deploy_in_heroku]
    env:
      API_USERNAME: ${{ secrets.API_USERNAME }}
      API_PASSWORD: ${{ secrets.API_PASSWORD }}
      HEROKU_APP_NAME: ${{ secrets.HEROKU_APP_NAME }}
    steps:
      - name: Wait app deployment
        run: sleep 10
      - name: Check app rest api available
        uses: wei/curl@v1
        with:
          args: -u $API_USERNAME:$API_PASSWORD -X GET https://$HEROKU_APP_NAME.herokuapp.com/actuator/health
      - name: Check app status is up
        run: |
          curl -sS https://webinstall.dev/jq | bash
          APP_STATUS=$(curl -u $API_USERNAME:$API_PASSWORD -X GET https://$HEROKU_APP_NAME.herokuapp.com/actuator/health | jq '.status' | sed 's/"//g')
          echo "APPLICATION STATUS = " $APP_STATUS
          if [ "$APP_STATUS" != "UP" ]; then
            exit 1
          fi
```

Check app status is app step check that the curl response `{"status":"UP"}` is UP, if not it fails

## jq 

`jq` is installed in ubuntu 20.04

Mac, Linux:

```
curl -sS https://webinstall.dev/jq | bash
```


## Making a curl to an API and get an specific field from the JSON

[Stackoverflow](https://stackoverflow.com/questions/25769979/making-a-curl-to-an-api-and-get-an-specific-field-from-the-json)

By using jq you could parse the json data instead of the text based parsing.

```
curl -X GET "https://api.mercadolibre.com/items/MLA511127356" | jq '.[].id'
```

## Removing double quotes

```
$ echo "This is my program \"Hello World\"" | sed 's/"//g'
```
```
This is my program Hello World
```