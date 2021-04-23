# Fake-S3

Simple container that runs [jubos/fake-s3](https://github.com/jubos/fake-s3).

Fake-s3 now requires a license, free for personal use, which can be acquired [here](https://supso.org/projects/fake-s3).

## Build

Place your license in `license.txt`

```
docker build --secret id=license,src=license.txt -t jrlangford/fake-s3 .
```

## Run

```
docker run -p 127.0.0.1:4567:4567 --name fake-s3 -d jrlangford/fake-s3
```

The container will be accessible in `localhost:4567`
