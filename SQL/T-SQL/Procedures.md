<h1 align="center">Procedures</h1>

<h2>Criação</h2>
    
```sql
CREATE PROCEDURE CalculaIdade
AS
BEGIN
    UPDATE TABELA_DE_CLIENTES SET IDADE = DATEDIFF(YEAR, DATA_NASCIMENTO, GETDATE())
END;
```

<h2>Execução</h2>
    
```sql
EXEC dbo.CalculaIdade
```

<h2>Parâmetros</h2>
    
```sql
CREATE PROCEDURE CalculaIdade
    @DataNascimento DATE
AS
BEGIN
    UPDATE TABELA_DE_CLIENTES SET IDADE = DATEDIFF(YEAR, @DataNascimento, GETDATE())
END;
```

<h2>Execução com Parâmetros</h2>
    
```sql
EXEC dbo.CalculaIdade '1990-01-01'

-- Ou
EXEC dbo.CalculaIdade @DataNascimento = '1990-01-01'
```
