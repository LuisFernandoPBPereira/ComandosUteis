<h1 align="center">Criando Imagem</h1>

Criamos um arquivo `Dockerfile` para criar uma imagem personalizada. O arquivo `Dockerfile` é um arquivo de texto que contém todos os comandos necessários para montar uma imagem Docker. O Dockerfile é o ponto de partida para criar uma imagem personalizada.

No nosso exemplo, iremos criar uma imagem de um site simples.

```dockerfile
FROM node:14
WORKDIR /app
COPY . .
RUN npm install
ENTRYPOINT npm start
```

Para criar a imagem, usamos `docker build`

```bash
docker build -t luisfernando/app:1.0 .
```

O parâmetro `-t` é usado para dar um nome e uma tag para a imagem. O ponto final `.` indica que o Dockerfile está no diretório atual.