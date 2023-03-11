# txtai API Server
This repository contains files for building a Docker image that runs a txtai API server. Instructions for building and running the image are provided below.

## API
This section builds an image that caches models and starts an API service. The config.yml file should be configured with the desired components to expose via the API.

###The following is a sample config.yml file that creates an Embeddings API service.

**config.yml**
```yaml
writable: true

embeddings:
  path: sentence-transformers/nli-mpnet-base-v2
  content: true
```

## The next section builds the image and starts an instance.

**Get Dockerfile**
```bash
wget https://raw.githubusercontent.com/neuml/txtai/master/docker/api/Dockerfile
```

**CPU build**
```bash
docker build -t txtai-api .
```

**GPU build**
```bash
docker build -t txtai-api --build-arg BASE_IMAGE=neuml/txtai-gpu .
```

**Run**
```bash
docker run -p 8000:8000 --rm -it txtai-api
```