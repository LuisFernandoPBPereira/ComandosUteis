<h1 align="center"><code>docker run</code></h1>

Este comando serve para executar um container com base em uma imagem, que pode estar local ou remotamente.

```bash
docker run [opções] <imagem>[:<tag>]
```

Podemos executar uma container de forma iterativa sem a necessidade de rodar um `docker exec`.

```bash
docker run -it <container> <comando>
```

Para mapear as portas de um container, podemos usar a opção `-P`.

```bash
docker run -P <container>
```

Para mapear as portas de um container manualmente, podemos usar a opção `-p` ou `--publish`.

```bash
docker run -p <porta_local>:<porta_container> <container>
```

Para não travar o terminal ao executar um container, podemos usar a opção `-d` ou `--detach`.

```bash
docker run -d <container>
```