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

<h2>IF...ELSE</h2>

```sql
DECLARE @DiaDaSemana VARCHAR(20);
DECLARE @NumeroDias INT;

SET @NumeroDias = 5;
SET @DiaDaSemana = DATENAME(WEEKDAY, DATEADD(DAY, @NumeroDias, GETDATE()));

IF @DiaDaSemana = 'Sábado' OR @DiaDaSemana = 'Domingo'
    PRINT 'Este dia é fim de semana';
ELSE
    PRINT 'Este dia não é fim de semana';
```

