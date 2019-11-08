# Dockerized Kafka Server + Zookeeper

This is a Docker image for running a Kafka cluster local development purposes.

The basis for this was taken from Spotify's image: https://github.com/spotify/docker-kafka/ 
-- but that image hadn't been updated in a few years, so this is a version bump of Kafka.


Connect to the `bootstrap_servers` broker at `localhost:9092`.

## Caveats

When running locally and trying to produce/consume to the broker, we need to specify the `ADVERTISED_HOST` with
the host (non-container) IP, and `127.0.0.1`, `localhost`, and `0.0.0.0` don't work.

If you're running on mac :( try this command to get the IP:

    export LOCAL_HOST=ipconfig getifaddr en0
    # you'll want to 
    docker run -p 2181:2181 -p 9092:9092 -e ADVERTISED_HOST=$LOCAL_HOST -e ADVERTISED_PORT=9092 kafka


