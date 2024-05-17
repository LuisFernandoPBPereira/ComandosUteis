<h1 align="center">Comandos Git</h1>

<p>
    Aqui você encontra variados comandos git em que você
    poderá usar no dia a dia.
</p>

<br>

<h2>Configuração do Git -> config</h2>

<p>Para configurar seu usuário e e-mail no Git, segue os comandos a seguir:</p>

```bash
git config --global user.name "Seu Nome"
git config --global user.email "Seu Email"
```
<br>

<h2>Inicializar um repositório -> init</h2>

<p>Para inicializar um repositório Git em um diretório existente, você pode usar o comando:</p>

```bash
git init
```

<p>Isso criará um novo repositório Git vazio no diretório atual.</p>

<p>Se você deseja inicializar um repositório Git em um diretório específico, você pode usar o comando:</p>

```bash
git init /caminho/para/diretorio
```

<br>

<h2>Adicionar todos arquivos para o repositório -> add</h2>

```bash
git add .
```

<br>

<h2>Criar uma branch -> branch</h2>

```bash
git branch -M nome-da-branch
```

<br>

<h2>Fazer conexão com o repositório remoto -> remote</h2>

```bash
git remote add origin url-do-repositorio
```

<br>

<h2>Realizar commits -> commit</h2>

- Commit com mensagem

```bash
git commit -m "Mensagem do commit"
```

- Commit que adiciona os arquivos e já coloca a mensagem

```bash
git commit -a -m "mensagem"
``` 

- Altera a mensagem do último commit

```bash
git commit --amend -m "Nova mensagem"
```

<br>

<h2>Enviar os commits para o repositório remoto -> push</h2>

```bash
git push origin main
```

<br>

<h2>Trazer os commits do repositório remoto -> pull</h2>

```bash
git pull origin main
```

<br>

<h2>Log dos commits -> log</h2>

- Exibe o log dos commits

```bash
git log
```
- Exibe o log dos commits de forma resumida

```bash
git log --oneline
```

- Exibe o log de uma branch específica

```bash
git log nome-da-branch
```

<br>

<h2>Verificar status dos arquivos -> status</h2>

```bash
git status
```

<br>

<h2>Clonar repositório -> clone</h2>

```bash
git clone url-do-repositorio
```

<br>

<h2>Retorna a versão do commit -> reset</h2>

```bash
git checkout hash-do-commit
```

<br>

<h2>Retornar a um commit anterior</h2>

<p>
    O comando <code>git reset --hard</code> é utilizado para retornar a um commit anterior, 
    removendo todos os commits posteriores a ele.
</p>

```bash
git reset --hard hash-do-commit
```

<br>

<h2>Mostra as alterações do commit -> show</h2>

- Mostra as alterações do último commit

```bash
git show
```

- Mostra as alterações do commit especificado

```bash
git show hash-do-commit
```

<br>

<h2>Trocar de branch -> switch</h2>

- Troca de branch

```bash
git switch nome-da-branch
```

- Cria uma nova branch e troca para ela

```bash
git switch -c nome-da-branch
```

<br>

<h2>Unir branches -> merge</h2>

```bash
git merge nome-da-branch
```

<br>

<h2>Transferir commits antigos para a branch desejada -> rebase</h2>

- Transfere os commits de uma branch para outra até o momento de criação da branch

```bash
git rebase nome-da-branch
```

<br>

<h2>Guarda as alterações para aplicar posteriormente -> stash</h2>

- Guarda as alterações

```bash
git stash
```

- Remove as alterações guardadas e aplica no código

```bash
git stash pop
```

- Lista os itens em stash

```bash
git stash list
```

- Limpa os itens em stash

```bash
git stash clear
```

<br>

- Coloca as alterações em stash com mensagem personalizada

```bash
git stash push -m "mensagem"
```

- Aplica as alterações de um stash específico

```bash
git stash apply stash@{indice}
```

- Remove um stash específico

```bash
git stash drop stash@{indice}
```

<br>

<h2>Restaura as modificações -> restore</h2>

- Restaura as modificações de um arquivo que foi adicionado

```bash
git restore --staged nome-do-arquivo
```

- Restaura as modificações de um arquivo que não foi adicionado

```bash
git restore nome-do-arquivo
```

- Restaura todas as modificações

```bash
git restore .
```

- Restaura um arquivo de um commit específico

```bash
git restore --source=hash-do-commit nome-do-arquivo
```

<br>

<h2>Adicionar tags aos commits -> tag</h2>

- Adiciona uma tag ao commit

```bash
git tag nome-da-tag 
```

- Adiciona uma tag para um commit especifico

```bash
git tag nome-da-tag hash-do-commit
```

- Adiciona uma tag com mensagem

```bash
git tag -a nome-da-tag -m "mensagem"
```

- Remove a tag
    
```bash
git tag -d nome-da-tag
```

- Mostra detalhes da tag

```bash
git tag -v nome-da-tag
```

<br>

<h2>Mostra as diferenças entre commits -> diff</h2>

- Mostra as diferenças entre o último commit e o penúltimo

```bash
git diff HEAD HEAD~1
```

- Mostra as diferenças entre o último commit e o penúltimo de forma resumida

```bash
git diff --stat HEAD HEAD~1
```

<br>

<h2>Adiciona um commit específico em uma branch -> cherry-pick</h2>

```bash
git cherry-pick hash-do-commit
```

<br>

<h2>Mostra o autor das alterações -> blame</h2>

```bash
git blame nome-do-arquivo
```