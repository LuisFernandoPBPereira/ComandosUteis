<h1 align="center">Comandos SQL</h1>

<p>
    Aqui você encontra variados comandos SQL em que você
    poderá usar no dia a dia.
</p>

<h2>CREATE</h2>

- Criar um banco de dados:

```sql
CREATE DATABASE nome-do-banco;
```

- Criar uma tabela:

```sql
CREATE TABLE nome-da-tabela (
    id INT PRIMARY KEY,
    nome VARCHAR(255),
    idade INT
);
```

<br>

<h2>ALTER</h2>

- Alterar uma tabela:

```sql
ALTER TABLE nome-da-tabela 
    ADD COLUMN sobrenome VARCHAR(255);
```

- Adicionar uma primary key

```sql
ALTER TABLE nome-da-tabela 
    ADD CONSTRAINT PK-nome-da-pk 
    PRIMARY KEY CLUSTERED nome-da-pk
```

<br>

<h2>INSERT</h2>

- Inserindo campos em uma tabela

```sql
INSERT INTO nome-da-tabela (campos) VALUES (valores);
```

<h2>SELECT + filtros</h2>

- Seleção sem repetição de dados

```sql
SELECT DISTINCT nome-do-campo FROM nome-da-tabela;
```

- Seleção para contar o registro da tabela;

```sql
SELECT COUNT(*) FROM nome-da-tabela;
```

- Seleção que substitui o uso do OR ao conter mais de dois campos para se comparar
```sql
SELECT * FROM  nome-da-tabela 
    WHERE nome-da-coluna = IN (valor1, valor2, valor3);
```

- Seleção que o valor contenha determinado texto em qualquer parte dele

```sql
SELECT * FROM nome-da-tabela 
    WHERE nome-da-coluna 
    LIKE '%palavra%';
```

- Seleção que o valor contenha determinado texto no final

```sql
SELECT * FROM nome-da-tabela 
    WHERE nome-da-coluna 
    LIKE '%palavra';
```

- Seleção que o valor contenha determinado texto no começo

```sql
SELECT * FROM nome-da-tabela 
    WHERE nome-da-coluna 
    LIKE 'palavra%';
```

- Seleção que retorna um número desejado de linhas

```sql
SELECT DISTINCT TOP 10 nome-do-campo 
    FROM nome-da-tabela;
```

- Seleção que ordena o resultado com base em um campo específico

```sql
SELECT * FROM nome-da-tabela 
    WHERE condicao 
    ORDER BY nome-do-campo;
```

- Seleção que agrupa o resultado com base em um campo específico

```sql
SELECT nome-do-campo 
    FROM nome-da-tabela 
    GROUP BY nome-do-campo;
```

- Seleção que aplica uma função de agregação no agrupamento

```sql
SELECT nome-do-campo 
    FROM nome-da-tabela 
    GROUP BY nome-do-campo 
    HAVING SUM(nome-do-campo);
```

- Seleção que contém uma condição

```sql
SELECT [CLIENTE], 
    (
        CASE WHEN [NUM_FUNC] >= 20 
                THEN 'GRANDE' 
             ELSE 'PEQUENO' END
    ) 
    FROM [CLIENTE];
```

<h2>UPDATE</h2>

```sql
UPDATE nome-da-tabela 
    SET nome-da-coluna = novo-valor 
    WHERE condicao;
```

<br>

<h2>JOIN</h2>

- INNER JOIN

```sql
SELECT [C.CIDADE], [C.ESTADO], [M.DATA], [M.VALOR_VENDA] 
   FROM [MOVIMENTO] M 
   INNER JOIN [CLIENTE] C ON C.CLIENTE = M.CLIENTE;
```

- INNER JOIN sem repetição de dados

```sql
SELECT DISTINCT [TC.CPF], [TC.NOME], [NF.CPF] 
   FROM [TABELA_CLIENTES] TC 
   INNER JOIN [NOTAS_FISCAIS] NF ON [TC.CPF] = [NF.CPF];
```

- RIGHT JOIN sem repetição de dados

```sql
SELECT DISTINCT [TV.NOME], [TV.BAIRRO], [TC.BAIRRO], [TC.NOME]
   FROM [TABELA_CLIENTES] TC 
   RIGHT JOIN [TABELA_VENDEDORES] TV
   ON [TC.BAIRRO] = [TV.BAIRRO]
   WHERE TC.NOME IS NULL;
```

- LEFT JOIN sem repetição de dados

```sql
SELECT DISTINCT [TV.NOME], [TV.BAIRRO], [TC.BAIRRO], [TC.NOME]
   FROM [TABELA_CLIENTES] TC 
   LEFT JOIN [TABELA_VENDEDORES] TV
   ON [TC.BAIRRO] = [TV.BAIRRO]
   WHERE TV.NOME IS NULL;
```

- FULL JOIN sem repetição de dados

```sql
SELECT DISTINCT [TV.NOME], [TV.BAIRRO], [TC.BAIRRO], [TC.NOME]
   FROM [TABELA_CLIENTES] TC 
   FULL JOIN [TABELA_VENDEDORES] TV
   ON [TC.BAIRRO] = [TV.BAIRRO]
   WHERE TV.NOME IS NULL;
```

<br>

<h2>Tipos de Dados</h2>

<h3>Numéricos exatos</h3>

- BIT
- SMALLINT
- BIGINT
- DECIMAL
- INT
- MONEY
- SMALLMONEY
- NUMERIC
- TINYINT

<br>

<h3>Numéricos aproximados</h3>

- FLOAT
- REAL

<br>

<h3>Data e hora</h3>

- DATE
- DATETIME2
- DATETIME
- DATETIMEOFFSET
- SMALLDATETIME
- TIME

<br>

<h3>Cadeias de caracteres</h3>

- VARCHAR
- CHAR
- TEXT

<br>

<h3>Cadeias de caracteres Unicode</h3>

- NVARCHAR
- NCHAR
- NTEXT

<br>

<h3>Cadeia de caracteres binária</h3>

- BINARY
- IMAGE
- VARBINARY

<br>

<h3>Outros tipos de dados</h3>

- CURSOR
- HIERARCHYID
- SQL_VARIANT
- TABLE
- ROWVEWRSION
- UNIQUEIDENTIFIER
- XML


