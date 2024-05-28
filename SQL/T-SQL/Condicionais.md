<h1 align="center">Condições em T-SQL</h1>

<h2>IF</h2>

```sql
-- Se a tabela existir, será excluída
IF OBJECT_ID('NomeDaTabela', 'U') IS NOT NULL
    DROP TABLE NomeDaTabela;

-- Se a tabela não existir, será criada
IF OBJECT_ID('NomeDaTabela', 'U') IS NULL
    CREATE TABLE NomeDaTabela (Colunas)
```
