# docker-swagger-ui
Configure Swagger UI with Docker

## Steps
1 - [Install Docker](https://docs.docker.com/)

2 - Edit .yaml files in ```./swagger/doc``` as you need or create new in [Swagger Editor](https://editor.swagger.io/)

3 - Edit ```./swagger/docker-compose.yaml``` as you need

```sh
version: '3.6'
services:
  swagger-ui:
    image: swaggerapi/swagger-ui
    restart: always
    container_name: swagger_ui_container
    ports:
      - "8084:8080"
    volumes:
      - ./doc:/usr/share/nginx/html/doc
    environment:
      URLS_PRIMARY_NAME: "PetstoreApi-1.1.0"
      URLS: "[
          { url: 'doc/petstore1.yaml', name: 'PetstoreApi-1.0.11'},
          { url: 'doc/petstore2.yaml', name: 'PetstoreApi-1.1.0'},
      ]"
```

4 - Up ```docker-compose.yaml``` file

```sh
# docker-compose up -d
```

5 - Open [http://localhost:8084](http://localhost:8084) in your browser.

## License

Apache 2.0
