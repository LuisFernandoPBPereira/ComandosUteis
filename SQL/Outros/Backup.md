<h1 align="center">Backup</h1>

### Criar arquivo de Backup

```sql
BACKUP DATABASE [NomeDoBanco] TO DISK = 'caminho-do-arquivo/nome-do-arquivo.bak'
```

<br>

### Restaurar arquivo de Backup

```sql
-- Devemos dropar o banco antes de restaurar e executar o comando estando conectado ao banco master

RESTORE DATABASE [NomeDoBanco] FROM DISK = 'caminho-do-arquivo/nome-do-arquivo.bak' WITH RECOVERY
```

### Backup Incremental

```sql
-- Para criarmos um backup que possa recerber backups incrementais, devemos adicionar a cláusula WITH INIT ao comando de backup

BACKUP DATABASE [NomeDoBanco] TO DISK = 'caminho-do-arquivo/nome-do-arquivo.bak' WITH INIT

-- Criando backup incremental, o nome do arquivo deve ser o mesmo criado com o WITH INIT

BACKUP LOG [NomeDoBanco] TO DISK = 'caminho-do-arquivo/nome-do-arquivo.bak' WITH NOINIT
```

<br>

### Backup Diferencial (Backup Full em um mesmo arquivo)

```sql
-- Para criarmos um backup diferencial, devemos adicionar a cláusula WITH DIFFERENTIAL ao comando de backup

BACKUP DATABASE [NomeDoBanco] TO DISK = 'caminho-do-arquivo/nome-do-arquivo.bak' WITH DIFFERENTIAL
```

<br>

### Visualizando Backups disponíveis

```sql
RESTORE HEADERONLY FROM DISK = 'caminho-do-arquivo/nome-do-arquivo.bak'
```

<br>

### Restaurando base de dados com mais de um backup

```sql
-- Devemos dropar o banco antes de restaurar e executar o comando estando conectado ao banco master


-- Restaurando o backup full, estamos especificando qual arquivo queremos no WITH FILE = (número do arquivo)
RESTORE DATABASE [NomeDoBanco] FROM DISK = 'caminho-do-arquivo/nome-do-arquivo.bak' WITH FILE = 1, NORECOVERY;

-- Devemos seguir uma sucessão de backups, restaurando os backups diferenciais e incrementais na ordem que foram criados, até o backup desejado.

RESTORE DATABASE [NomeDoBanco] FROM DISK = 'caminho-do-arquivo/nome-do-arquivo.bak' WITH FILE = 10, RECOVERY;

-- O útlimo backup deve ser restaurado com a cláusula RECOVERY
```