# Athena PDF Conversion Service on Google App Engine

This is a [Google App Engine Flexible Environment](https://cloud.google.com/appengine/docs/flexible/) Docker reference configuration for running the [Athena](https://github.com/arachnys/athenapdf) PDF conversion service.

## Running locally

1. Install [Docker for Mac](https://docs.docker.com/docker-for-mac/install/)
1. Kill any other apps running on localhost.
1. Run Docker Compose to start up the containers. `-d` to run containers in the background.

        $ docker-compose up -d
        $ docker-compose ps

1. Convert the GitHub homepage to a PDF.

        $ open http://localhost:8080/convert?auth=arachnys-weaver&url=https://github.com

1. Convert an html file on your machine to PDF.

        $ curl http://jargon-file.org/archive/jargon-1.5.0.dos.txt > jargon.txt
        $ curl -F "file=@jargon.txt" \
          http://localhost:8080/convert?auth=arachnys-weaver \
          > jargon.pdf

1. Teardown.

        $ docker-compose down

## Deploying to Google App Engine

```
$ gcloud projects list
$ gcloud set project=chocolate-covered-raisins
$ gcloud app deploy
$ gcloud app browse -s athenapdf
$ curl https://athenapdf-dot-chocolate-covered-raisins.appspot.com/convert?auth=arachnys-weaver
```

## Shout Outs

* [Arachnys](https://www.arachnys.com/), thank you for open sourcing a great alternative to [wkhtmltopdf](https://news.ycombinator.com/item?id=11446254).
* [@MrSaints](https://github.com/MrSaints)
* [Jakob Truelsen](https://github.com/antialize)
