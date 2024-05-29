<h1 align="center">Tabelas Temporárias em T-SQL</h1>

- <h3>Os nomes de tabelas que começam com #:</h3>

    - São visíveis apenas para a sessão de conexão atual
    - São excluídas automaticamente quando a conexão é encerrada
    - São conhecidas como tabelas temporárias locais

<h3>Exemplo:</h3>

```sql
CREATE TABLE #Temporaria (ID INT, Nome VARCHAR(50));
```

- <h3>Os nomes de tabelas que começam com ##:</h3>

    - São visíveis para todas as conexões
    - São excluídas quando a última conexão que as criou é encerrada
    - São conhecidas como tabelas temporárias globais

<h3>Exemplo:</h3>

```sql
CREATE TABLE ##Temporaria (ID INT, Nome VARCHAR(50));
```

- <h3>Os nomes de tabelas que começam com @:</h3>

    - São conhecidas como variáveis de tabela
    - São visíveis apenas para o bloco de código em que foram declaradas
    - São excluídas automaticamente quando o bloco de código é encerrado

<h3>Exemplo:</h3>

```sql
DECLARE @Temporaria TABLE (ID INT, Nome VARCHAR(50));
```

