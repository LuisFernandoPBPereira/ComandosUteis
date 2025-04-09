<h1 align="center"><code>docker run</code></h1>

Este comando serve para executar um container com base em uma imagem, que pode estar local ou remotamente.

```bash
docker run [opções] <imagem>[:<tag>]
```

Podemos executar uma container de forma iterativa sem a necessidade de rodar um `docker exec`.

```bash
docker run -it <container> <comando>
```