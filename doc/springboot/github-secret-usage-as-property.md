## Use GitHub secret as property

[Github actions not recognizing secret value during build](https://stackoverflow.com/questions/66841566/github-actions-not-recognizing-secret-value-during-build)

You have to inform your environment variables for each job.

## Example:

```
 - name: Maven Package 
     env: EMAIL_API_KEY: ${{ secrets.EMAIL_API_KEY }} 
     run: mvn -B clean package
```

## Explanation:

As jobs run in different runners, those runners are in different machines. Each job runs in a fresh instance of the virtual environment specified by runs-on.

It is not possible to share environment variables between machines. Github actions don’t support to share variables between jobs (yet).

However, there are some actions that allows to share datas between jobs using artifacts. You could eventually use it if it makes sense: github.com/marketplace/actions/share-jobs-data