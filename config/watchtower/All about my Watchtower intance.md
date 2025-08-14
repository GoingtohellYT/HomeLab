### Why use it?

Watchtower ensures that all your Docker containers are always running the latest versions. Every night, it checks the versions currently running on the server against the latest available on Docker Hub. If a new version exists and the container does not specify a fixed version, Watchtower stops the container, downloads the latest image, and rebuilds it with the same parameters, providing a seamless update experience.

### Configuration

Watchtower is set to use the latest version available (latest tag). It sends notifications via a Discord webhook whenever it updates one or more containers. It is scheduled to run every night at either 2:30:30 or 3:30:30, as it does not account for daylight saving time (resulting in a 1-hour shift from UTC).
