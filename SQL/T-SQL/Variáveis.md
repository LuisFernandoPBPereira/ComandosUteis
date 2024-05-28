<h1 align="center">Variáveis em T-SQL</h1>

<h2>Declarando variáveis</h2>

```sql
-- Declaração de variáveis linha por linha
DECLARE @NomeDaVariavel VARCHAR(5);
DECLARE @NomeDaSegundaVariavel VARCHAR(5);

-- Declaração de variáveis em uma única linha
DECLARE @NomeDaVariavel VARCHAR(5), @NomeDaSegundaVariavel VARCHAR(5);
```

<br>

<h2>Atribuindo valores a variáveis</h2>

```sql
-- Atribuindo valor a variável
SET @NomeDaVariavel = 'Teste';

-- Atribuindo usando SELECT
SELECT @NomeDaVariavel = Campo FROM Tabela WHERE Condicao;
```

<br>

<h2>Exibindo valores de variáveis</h2>

```sql
-- Exibindo valor da variável
PRINT @NomeDaVariavel;
```

<br>

<h2>Usando as variáveis nos comandos</h2>

```sql
INSERT INTO Tabela (Coluna) VALUES (@NomeDaVariavel);
```