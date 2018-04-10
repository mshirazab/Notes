# NodeJS Heroku Deployment

## Deployment Checklist

1.  **Dynamic Port Binding**: In app.js where you express.listen()

    ```javascript
    const PORT = process.env.PORT || 5000;
    // process.env is given by heroku
    app.listen(PORT);
    ```

2.  **Specify Node Environment**:In package.json, specify the engines

    ```json
    {
      "engines": {
        "node": "8.1.1", // the version you want to run
        "npm": "5.0.3"
      }
    }
    ```

3.  **Specify start script**: In package.json, edit start in scripts

    ```json
    {
      "start": {
        "start": "node index.js"
      }
    }
    ```

4.  **create .gitignore file**: Create a .gitignore in root directory

    ```
    node_modules
    dev.js
    ```

## First deployment

1.  Create an account in heroku account at https://www.heroku.com
2.  Install git at https://git-scm.com/downloads
3.  initialize your project with git `git init`
4.  add the files to commit `git add .`
5.  Commit those files `$git commit -m "My message"`
6.  Download Heroku CLI https://devcenter.heroku.com/articles/heroku-cli
7.  Login to heroku `heroku login`
8.  Create app at heroku and it will help you after that by giving a git link
9.  `heroku git:remote -a <The app name>`
10. `git push heroku push`
11. run `heroku open` to open the website
12. run `heroku logs` to check problems

## Subsiquent Deploys

* `git push heroku push`

## Adding sensitive data

* Goto app console in heroku website
* Then in settings and add them as config vars
* then you can access them with `process.env`
