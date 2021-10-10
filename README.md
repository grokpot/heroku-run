# Heroku Run Command

![GitHub issues](https://img.shields.io/github/issues/michcio1234/heroku-run.svg)
![GitHub](https://img.shields.io/github/license/michcio1234/heroku-run.svg)

This is a very simple GitHub action that allows you to invoke the `$ heroku` CLI to call a custom command.

```yaml
on:
  push:
    branches:
      - master

name: Build and Deploy
env:
  HEROKU_APP_NAME: "your-heroku-app-name"

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:

      - name: Ensure Worker Dyno is Running
        uses: michcio1234/heroku-run@master
        with:
          heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
          heroku_app_name: ${{ env.HEROKU_APP_NAME }}
          heroku_email: "${{ secrets.HEROKU_EMAIL }}"
          command: ps:scale worker=1  # Do NOT preface with 'heroku'
```

Entirely based on https://github.com/tiltshift/heroku-promote-app.
