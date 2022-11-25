# docker-swagger-ui
Configure Swagger UI with Docker

## Steps
1 - [Install Docker](https://docs.docker.com/)

2 - Edit and save one or more .yaml file in [Swagger Editor](https://editor.swagger.io/)

3 - Copy file(s) to ``` ./swagger/doc``` folder

4 - Edit docker-compose.yaml file

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
      - ./swagger/doc:/usr/share/nginx/html/doc
    environment:
      URLS_PRIMARY_NAME: "OpenApiOne"
      URLS: "[
          { url: 'doc/openapi1.yaml', name: 'OpenApiOne'},
          { url: 'doc/openapi2.yaml', name: 'OpenApiTwo'},
      ]"
```

5 - Up ```docker-compose.yaml``` file

```sh
# docker-compose up -d
```

6 - Open [http://localhost:8084](http://localhost:8084) in your browser.

## License

Apache 2.0
