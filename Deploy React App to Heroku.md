### Create the Heroku app
```sh
heroku create $APP_NAME --buildpack https://github.com/mars/create-react-app-buildpack.git
```
Replace $APP_NAME with a name for your unique app.

### Set buildpacks for existing app
```sh
heroku buildpacks:set https://github.com/some/buildpack.git -a $APP_NAME
```

### Deploy

```sh
git push heroku master
```

### Visit the app's public URL in your browser

```sh
heroku open
```

### Delete heroku app
```sh
heroku apps:destroy --app $APP_NAME
```

[reference](https://github.com/mars/create-react-app-buildpack)
