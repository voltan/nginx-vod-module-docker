# nginx-vod-module-docker
Local dockerfile for run nginx vod module by kaltura

## Building locally
This repository uses Docker's multi-stage builds, therefore building this image
requires Docker 17.05 or higher. Given that you have all the required
dependencies, building the image is as simple as running a docker build:

```
docker build -t nginxvod -f Dockerfile .
```

here `nginxvod` is your local image name, and you can change this name if you like

## Running this example locally
You can run this example locally with Docker
```
docker run -p 3030:80 -v $PWD/videos:/opt/static/videos -v $PWD/nginx.conf:/usr/local/nginx/conf/nginx.conf nginxvod
```

* docker run on port `3030`, you can change this port if you want
* open port on server firewall
* `/videos` its local directory for video sources 
* `nginx.conf` its nginx config file.
* you can change video path by change `$PWD/videos` to new path
* Add `-d` after `run`, if you want run it background


## Example

* HLS: `http://localhost:3030/hls/demo.mp4/master.m3u8`
* Dash: `http://localhost:3030/dash/demo.mp4/manifest.mpd`
* Thumbnail: `http://localhost:3030/thumb/demo.mp4/thumb-1000.jpg`


## Run examples

* Run in background :

```
docker run -d -p 3030:80 -v $PWD/videos:/opt/static/videos -v $PWD/nginx.conf:/usr/local/nginx/conf/nginx.conf nginxvod
```

## Source

* [dojocasts/nginx-vod-module-docker](https://gitlab.com/dojocasts/nginx-vod-module-docker)
* [nytimes/nginx-vod-module-docker](https://github.com/nytimes/nginx-vod-module-docker)