# drone-google-chat

[![Build Status](https://cloud.drone.io/api/badges/goldinteractive/drone-google-chat/status.svg)](https://cloud.drone.io/goldinteractive/drone-google-chat)
[![Go Doc](https://godoc.org/github.com/goldinteractive/drone-google-chat?status.svg)](http://godoc.org/github.com/goldinteractive/drone-google-chat)
[![Go Report](https://goreportcard.com/badge/github.com/goldinteractive/drone-google-chat)](https://goreportcard.com/report/github.com/goldinteractive/drone-google-chat)
[![](https://images.microbadger.com/badges/image/pelotech/drone-google-chat.svg)](https://microbadger.com/images/pelotech/drone-google-chat "Get your own image badge on microbadger.com")

Drone plugin for sending google chat notifications. For the usage information and a listing of the available options please reference TBD.

This plugin is currently experimental since the google chat apis haven't been released

## Build

Build the binary with the following commands:

```
drone exec
```

## Docker

Build the docker image with the following commands:

```
drone exec
docker build -t goldinteractive/drone-google-chat .
```


## Usage

Execute from the working directory:

You need to create an incomming hook from the google chat room. The webhook is everything minus the &token=... 
and the token is just the token itself.

```
docker run --rm \
  -e GOOGLE_CHAT_WEBHOOK=https://chat.googleapis.com/v1/spaces/... \
  -e GOOGLE_CHAT_KEY=somekey
  -e GOOGLE_CHAT_TOKEN=sometoken
  -e DRONE_REPO_OWNER=octocat \
  -e DRONE_REPO_NAME=hello-world \
  -e DRONE_COMMIT_SHA=7fd1a60b01f91b314f59955a4e4d4e80d8edf11d \
  -e DRONE_COMMIT_BRANCH=master \
  -e DRONE_COMMIT_AUTHOR=octocat \
  -e DRONE_COMMIT_AUTHOR_EMAIL=octocat@github.com \
  -e DRONE_COMMIT_AUTHOR_AVATAR="https://avatars0.githubusercontent.com/u/583231?s=460&v=4" \
  -e DRONE_COMMIT_AUTHOR_NAME="The Octocat" \
  -e DRONE_BUILD_NUMBER=1 \
  -e DRONE_BUILD_STATUS=success \
  -e DRONE_BUILD_LINK=http://github.com/octocat/hello-world \
  -e DRONE_TAG=1.0.0 \
  pelotech/drone-google-chat
```

### Contribution

This repo is setup in a way that if you enable a personal drone server to build your fork it will
 build and publish your image (makes it easier to test PRs and use the image till the contributions get merged)
 
* Build local ```DRONE_REPO_OWNER=goldinteractive DRONE_REPO_NAME=drone-google-chat drone exec```
* on your server just make sure you have DOCKER_USERNAME, DOCKER_PASSWORD, and PLUGIN_REPO set as secrets
