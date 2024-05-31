<h1 align="center">Procedures</h1>

<h2>Criação</h2>
    
```sql
CREATE PROCEDURE CalculaIdade
AS
BEGIN
    UPDATE TABELA_DE_CLIENTES SET IDADE = DATEDIFF(YEAR, DATA_NASCIMENTO, GETDATE())
END;
```

<br>

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

<br>

<h2>Procedure com entrada por referência</h2>
    
```sql
CREATE PROCEDURE CalculaIdade
    @DataNascimento DATE,
    @Idade INT OUTPUT
AS
BEGIN
    SET @Idade = DATEDIFF(YEAR, @DataNascimento, GETDATE())
END;
```

<h2>Execução com Parâmetros por Referência</h2>
    
```sql
DECLARE @Idade INT

EXEC dbo.CalculaIdade '1990-01-01', @Idade OUTPUT

SELECT @Idade
```

<br>

<h2>Excluindo uma Procedure</h2>
    
```sql
DROP PROCEDURE NomeDaProcedure
```