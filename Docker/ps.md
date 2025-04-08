<h1 align="center"><code>docker ps</code> ou <code>docker container ls</code></h1>

Este comando serve para visualizarmos os containers em execução no momento.

```bash
docker ps
```

```bash
docker container ls
```

Podemos visualizar todos os containers, mesmo os que não estão em execução, utilizando a flag `-a` ou `--all`.

```bash
docker ps -a
```

```bash
docker container ls -a
```