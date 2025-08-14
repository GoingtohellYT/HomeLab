### Why use Portainer?

Portainer is more of a "nice to have" than a strict necessity. It keeps all my Docker Compose files in one place and makes creating and managing containers much easier than using the CLI every time.  

### Installation Method

Portainer itself is a Docker container, which I deployed using:

```bash
docker volume create portainer_data
docker run -d -p 9443:9443 -p 8000:8000 \
  --name portainer \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce:latest
