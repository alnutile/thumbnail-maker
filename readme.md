# Iron ThumbnailMaker

This post https://alfrednutile.info/posts/143 covers the setup of docker and iron cli.
Also some of the basics of what is happening.

From there you can use this library to build out thumbnails for you.


## Run locally

~~~
docker run --rm -v "$(pwd)":/worker -w /worker iron/images:php-5.6 sh -c "php /worker/workers/ThumbMaker.php -payload payload.json"
~~~

## Get into the bash

~~~
docker run -it -v "$(pwd)":/worker -w /worker iron/images:php-5.6 /bin/bash
~~~

Set your .env


## Via Curl

~~~
curl -H "Content-Type: application/json" -X POST -d '{"folder": "bundles/mock-project-1/requests/mock-request-1/compares/a"}' "https://worker-aws-us-east-1.iron.io/2/projects/IRON_PROJECT_ID/tasks/webhook?code_name=ThumbMaker&oauth=IRON_TOKEN_ID"
~~~

## Payload

See `payload.json` for the most basic.

For a full set of env options

~~~
{
  "folder": "path/to/files",
  "bucket": "foo",
  "region": "east-foo",
  "secret": "bar",
  "key":    "foo",
  "destination": "thumbnails"
}
~~~

## Upload worker

sh ./upload_worker.sh