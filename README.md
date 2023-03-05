# Video Streamer with RTSP Server using Docker Compose

This project uses Docker Compose to manage two containers: a video streamer and an RTSP server. The video streamer streams an input video file to the RTSP server, which can then be accessed from a video player. This project can be used for testing RTSP video streaming in a development environment.

## Prerequisites

- Docker
- Docker Compose

## Installation

1. Clone the repository:
```
git clone github.com/goadiros/rtsp-media-server
```
2. Navigate to the project directory:
```
cd rtsp-media-server
```

## Usage

1. Start the containers using Docker Compose:
```
docker compose up
```

2. The containers will start running and the video stream will be available at `rtsp://localhost:8554/mystream`.

3. To stop the containers, use `Ctrl-C` in the terminal or run the following command in a new terminal window:
```
docker compose down
```

## Configuration

The `volumes` field in the `video-streamer` service specifies the location of the input video file. 
You can replace the `./data` path with the location of your own video file.
Keep in mind the you will need to change the docker-compose.yml video-streamer command to relvant mp4 filename.
## Services

### rtsp-server

This service uses the `aler9/rtsp-simple-server` Docker image and sets the container name and hostname to "rtsp-server". The host network mode is used.

### video-streamer

This service uses the `jrottenberg/ffmpeg` Docker image and sets the container name to "video-streamer". The host network mode is used and a volume is mounted to the "/data" directory. The `command` field specifies the command to be executed inside the container, which includes streaming an input video file located at `/data/input.mp4` to the RTSP endpoint at `rtsp://localhost:8554/mystream`.


