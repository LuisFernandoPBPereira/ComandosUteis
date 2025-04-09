<h1 align="center">Criando Imagem</h1>

Criamos um arquivo `Dockerfile` para criar uma imagem personalizada. O arquivo `Dockerfile` é um arquivo de texto que contém todos os comandos necessários para montar uma imagem Docker. O Dockerfile é o ponto de partida para criar uma imagem personalizada.

No nosso exemplo, iremos criar uma imagem de um site simples.

```dockerfile
FROM node:14
WORKDIR /app
ARG PORT_BUILD=3000
ENV PORT=$PORT_BUILD
EXPOSE $PORT_BUILD
COPY . .
RUN npm install
ENTRYPOINT npm start
```

- `FROM`:  Pega uma imagem base.
- `WORKDIR`: Define o diretório de trabalho dentro do contêiner.
- `ARG`: Define uma variável de ambiente que pode ser passada durante o build da imagem.
- `ENV`: Define uma variável de ambiente dentro do contêiner.
- `EXPOSE`: expõe a porta de execução do container.
- `COPY`: Copia arquivos do diretório atual para o contêiner.
- `RUN`: Executa um comando durante a construção da imagem.
- `ENTRYPOINT`: Define o comando que será executado quando o contêiner for iniciado.

Para criar a imagem, usamos `docker build`

```bash
docker build -t luisfernando/app:1.0 .
```

O parâmetro `-t` é usado para dar um nome e uma tag para a imagem. O ponto final `.` indica que o Dockerfile está no diretório atual.