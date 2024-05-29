<h1 align="center">Funções UDF (User Defined Function)</h1>

- As funções UDF são funções definidas pelo usuário

<h2>Exemplo:</h2>

```sql
CREATE FUNCTION FaturamentoNota(@NumeroNota AS INT)
RETURN FLOAT
AS
BEGIN
    DECLARE @FATURAMENTO FLOAT

    SELECT @FATURAMENTO = SUM(QUANTIDADE * PRECO)
        FROM ITENS_NOTAS_FISCAIS
        WHERE NUMERO_NOTA = @NumeroNota
    
    RETURN @FATURAMENTO
END;

-- Uso da função
SELECT NUMERO_NOTA, dbo.FaturamentoNota(NUMERO_NOTA) AS FATURAMENTO
    FROM NOTAS_FISCAIS
```

<br>

<h2>Retornando uma tabela</h2>

```sql
CREATE FUNCTION ListaNotasCliente(@CPF AS VARCHAR(11))
RETURNS TABLE
AS
RETURN
(
    SELECT NUMERO_NOTA, DATA_EMISSAO, VALOR_TOTAL
        FROM NOTAS_FISCAIS
        WHERE CPF_CLIENTE = @CPF
);

-- Uso da função
SELECT * FROM dbo.ListaNotasCliente('00000000000')
```

<br>

<h2>Alterando uma função existente</h2>

```sql
ALTER FUNCTION NomeDaFuncao(parametros)
RETURNS tipo
AS
BEGIN

    -- Alterações na função

END;
```

<br>

<h2>Excluindo uma função</h2>

```sql
DROP FUNCTION NomeDaFuncao
```


