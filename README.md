# Example Webapp

This application is an example web application written in [Go](https://golang.org/).

# Deployment

In order to deploy the example-webapp, you'll need the following:

  - The example-webapp binary
  - The static web assets in the public folder

Once you have these available, you can run the application binary, and it will run a HTTP server.

```bash
./example-webapp                                                                                                                  2.3.1    ✓  go1.8
2017/05/30 19:27:00 No config file found, using defaults:  Unsupported Config Type ""
[negroni] listening on :3000
```

The application listens on port `3000`

# Configuration

The example webapp connects to [Redis](https://redis.io/) to store its data.

By default, it will look for a redis installation at `localhost:6379`.

If you need to deploy your redis key/value store to another machine, or another port, you can do this in 1 of 2 ways:

## Configuration File

Place a file in the same directory as the application binary called `config.yaml` and specify the following:

```yaml
redishost: "redis.example.net"
redisport: "6380"
```

## Environment Variables

If you don't want to use a static configuration file, you can also specify the connection details using environment variables:

```bash
export REDISHOST="redis.example.net"
export REDISPORT="6380"
```

*Please note* - the *redisport* config option must be a string


# Building

If you want to build the application from scratch, we use [glide](https://glide.sh/) for dependency management, so it should be as simple as:

 - cloning this repo into `$GOPATH/src/github.com/apptio/example-webapp-go`
 - run `glide install` from the directory
 - run `go build -o example-webapp main.go`
