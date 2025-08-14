### Why use it?

SearXNG fights on multiple fronts. Firstly, it is a huge gain for privacy compared to using Google or Bing, as it removes all the JavaScript scripts that are normally returned with the results page.  

This prevents Google from linking my searches to a Google account and removes personalized results, making search outcomes more objective. Additionally, the ability to get results from multiple search engines makes searches more diversified and trustworthy.

### Installation method

SearXNG runs in a Docker container created with the following command:

```bash
docker run -d --name=searxng -p 8080:8080 -v /home/alex/searxng:/etc/searxng searxng/searxng:latest

SearXNG uses plain HTTP and takes up port 8080, but can be accessed using HTTPS through the Cloudflare tunnel

### Configuration
#### Preferences

The instance configuration is stored in a YAML file. Users can modify settings through the web interface, and personal settings are stored in a browser cookie. Deleting all cookies will remove any personal SearXNG configuration.
