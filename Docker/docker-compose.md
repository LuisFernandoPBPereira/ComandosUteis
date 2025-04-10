<h1 align="center"><code>docker-compose</code></h1>

Usamos `docker compose` para subirmos mais de um container de uma só vez, através de um arquivo `.yml`.

Aqui temos um exemplo de arquivo, onde subimos dois containers:

### Arquivo `.yml`

```yml
version: "3.9"
services:
    mongodb:
        image: mongo:latest
        container_name: mongodb
        networks:
            - minha-rede

    app:
        image: luisferenandopbp/minha-imagem:latest
        container_name: app
        networks:
            - minha-rede
        ports:
        - 3000:3000

networks:
    minha-rede:
        driver: bridge
```

Para executar o arquivo `.yml` usamos o comando:

```bash
docker compose up -d
```