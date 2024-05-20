<h1 align="center">Comandos SQL</h1>

<p>
    Aqui você encontra variados comandos SQL em que você
    poderá usar no dia a dia.
</p>

<h2>Sumário:</h2>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#alter">ALTER</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#create">CREATE</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#fun%C3%A7%C3%B5es">Funções</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#fun%C3%A7%C3%B5es-de-data">Funções de data</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#insert">INSERT</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#join">JOIN</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#select--filtros">SELECT + Filtros</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#subquery">SUBQUERY</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#union">UNION</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#update">UPDATE</a>

- <a href="https://github.com/LuisFernandoPBPereira/ComandosUteis/blob/main/Sql.md#view">VIEW</a>


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

- CROSS JOIN

```sql
SELECT Employees.EmployeeName, Courses.CourseName
    FROM Employees
    CROSS JOIN Courses;
```

<br>

<h2>UNION</h2>

- Une as linhas de duas tabelas

```sql
SELECT [CLIENTE], [CIDADE], [ESTADO] 
   FROM [TBL_CLIENTES] 
   UNION
   SELECT [FORNECEDOR], [CIDADE], [ESTADO]
   FROM [TBL_FORNECEDOR];
```

- Por padrão, UNION realiza o SELECT DISTINCT, então podemos usar o UNION ALL para repetir os dados

```sql
SELECT [CLIENTE], [CIDADE], [ESTADO] 
   FROM [TBL_CLIENTES] 
   UNION ALL
   SELECT [FORNECEDOR], [CIDADE], [ESTADO]
   FROM [TBL_FORNECEDOR];
```

- UNION com definição da origem do campo

```sql
SELECT [CLIENTE], [CIDADE], [ESTADO], 'CLIENTE' AS ORIGEM 
   FROM [TBL_CLIENTES] 	
   UNION ALL
   SELECT [FORNECEDOR], [CIDADE], [ESTADO], 'FORNECEDOR' AS ORIGEM
   FROM [TBL_FORNECEDOR];
```

<br>

<h2>SUBQUERY</h2>

- Exemplo básico de subquery

```sql
SELECT * FROM TABELA_DE_CLIENTES WHERE BAIRRO IN
(
    SELECT DISTINCT BAIRRO FROM TABELA_DE_VENDEDORES
);
-- Retorna todos os bairros da tabela de clientes que estão no mesmo bairro que os vendedores
```

- Subquery usando INNER JOIN

```sql
-- Sem subquery

SELECT INF.CODIGO_DO_PRODUTO, TP.NOME_DO_PRODUTO, TP.SABOR, SUM(INF.QUANTIDADE) AS QUANTIDADE 
    FROM ITENS_NOTAS_FISCAIS  INF
    INNER JOIN TABELA_DE_PRODUTOS TP 
    ON INF.CODIGO_DO_PRODUTO = TP.CODIGO_DO_PRODUTO
    GROUP BY INF.CODIGO_DO_PRODUTO, TP.NOME_DO_PRODUTO, TP.SABOR HAVING SUM(INF.QUANTIDADE) < 394000 
    ORDER BY SUM(INF.QUANTIDADE) DESC;

--=============================================================================

-- Com subquery

SELECT DISTINCT SABOR FROM TABELA_DE_PRODUTOS WHERE
CODIGO_DO_PRODUTO IN 
(
    SELECT INF.CODIGO_DO_PRODUTO FROM ITENS_NOTAS_FISCAIS  INF
    INNER JOIN TABELA_DE_PRODUTOS TP 
    ON INF.CODIGO_DO_PRODUTO = TP.CODIGO_DO_PRODUTO
    GROUP BY INF.CODIGO_DO_PRODUTO, TP.NOME_DO_PRODUTO HAVING SUM(INF.QUANTIDADE) < 394000
);

-- Retorna o sabor dos produtos que tiveram uma quantidade total vendida menor que 394000
```

- "Substituindo" o HAVING

```sql
-- Sem subquery

SELECT EMBALAGEM, AVG(PRECO_DE_LISTA) AS PRECO_MEDIO
    FROM TABELA_DE_PRODUTOS GROUP BY EMBALAGEM
    HAVING AVG(PRECO_DE_LISTA) <= 10;

--=============================================================================

-- Com subquery

SELECT MEDIA_EMBALAGENS.EMBALAGEM, MEDIA_EMBALAGENS.PRECO_MEDIO
    FROM 
    (
        SELECT EMBALAGEM, AVG(PRECO_DE_LISTA) AS PRECO_MEDIO
            FROM TABELA_DE_PRODUTOS GROUP BY EMBALAGEM
            HAVING AVG(PRECO_DE_LISTA) <= 10
    ) MEDIA_EMBALAGENS
    WHERE MEDIA_EMBALAGENS.PRECO_MEDIO <= 10;

-- Retorna o preço médio dos produtos que estão na tabela de produtos e que tem um preço médio menor ou igual a 10
```

<br>

<h2>VIEW</h2>

- Criar uma view

```sql
CREATE VIEW MEDIA_EMBALAGENS AS 
    SELECT EMBALAGEM, AVG(PRECO_DE_LISTA) AS 'PRECO MEDIO'
        FROM TABELA_DE_PRODUTOS
        GROUP BY EMBALAGEM;
```

- Buscar informações de uma view

```sql
SELECT EMBALAGEM, [PRECO MEDIO]
    FROM MEDIA_EMBALAGENS
    WHERE [PRECO MEDIO] <= 10;
```

<br>

<h2>FUNÇÕES</h2>

<h3>LOWER</h3>

- Transforma o texto em minúsculo

```sql
SELECT NOME, LOWER(NOME) AS NOME_COM_LOWER FROM TABELA_DE_CLIENTES;
```

<h3>UPPER</h3>

- Transforma o texto em maiúsculo

```sql
SELECT NOME, UPPER(NOME) AS NOME_COM_UPPER FROM TABELA_DE_CLIENTES;
```

<h3>CONCAT</h3>

- Concatena dois ou mais campos

```sql
SELECT 
    NOME, 
    CONCAT
    (
        ENDERECO_1, ' ',
        BAIRRO, ' ', 
        CIDADE, ' ', 
        ESTADO, ' - ', 
        CEP
    ) AS ENDERECO_COMPLETO
    FROM TABELA_DE_CLIENTES;
```

<h3>LEFT</h3>

- Retorna os caracteres à esquerda de uma string

```sql
SELECT 
    NOME_DO_PRODUTO, 
    LEFT(NOME_DO_PRODUTO, 3) AS TRES_PRIMEIROS_CARACTERES
    FROM TABELA_DE_PRODUTOS;
```

<h3>RIGHT</h3>

- Retorna os caracteres à direita de uma string

```sql
SELECT 
    NOME_DO_PRODUTO, 
    RIGHT(NOME_DO_PRODUTO, 3) AS TRES_ULTIMOS_CARACTERES
    FROM TABELA_DE_PRODUTOS;
```

<h3>REPLACE</h3>

- Substitui uma string por outra

```sql
-- Troca apenas a palavra Litros por L

SELECT TAMANHO, REPLACE(TAMANHO, 'Litros', 'L') AS TAMANHO_MODIFICADO
    FROM TABELA_DE_PRODUTOS;

-- Troca a palavra Litros e Litro por L

SELECT 
    TAMANHO, 
    REPLACE
    (
        (REPLACE(TAMANHO, 'Litros', 'L')), 'Litro', 'L'
    ) AS TAMANHO_MODIFICADO
    FROM TABELA_DE_PRODUTOS;
```

<h3>SUBSTRING</h3>

- Retorna uma parte de uma string

```sql
-- Retorna o primeiro nome de uma pessoa

SELECT 
    NOME, 
    SUBSTRING(NOME, 1, CHARINDEX(' ', NOME, 1)) 
    FROM TABELA_DE_CLIENTES;
```

<h3>FUNÇÕES DE DATA</h3>

- GETDATE -> retorna a data do seu computador

```sql
SELECT GETDATE();
```

- DATEADD -> adiciona uma quantidade de tempo a uma data

```sql
-- Adiciona 10 dias a data atual

SELECT DATEADD(DAY, 10, GETDATE());
```

- DATEDIFF -> retorna a diferença entre duas datas

```sql
SELECT DATEDIFF(DAY, '2024-01-01', GETDATE()) AS DIAS_DESDE_INICIO_DO_ANO;
```

- DATEPART -> retorna uma parte de uma data

```sql
SELECT DATEPART(DAY, GETDATE());
```

- ISDATE -> verifica se uma string é uma data

```sql
SELECT ISDATE('2024-02-31');
```

- DATEFROMPARTS -> retorna uma data a partir de partes

```sql
SELECT ISDATE(DATETIMEFROMPARTS(2024,05,20,11,48,00,00))
-- Ano, mês, dia, hora, minuto, segundo, milissegundo
```

- DATENAME -> retorna o nome de uma parte de uma data

```sql
SELECT NOME, CONCAT
    (
        DATENAME(WEEKDAY, DATA_DE_NASCIMENTO), ', ',
        DATENAME(DAY, DATA_DE_NASCIMENTO), ' de ',
        DATENAME(MONTH, DATA_DE_NASCIMENTO), ' ',
        DATENAME(YEAR, DATA_DE_NASCIMENTO)
    ) AS 'DATA POR EXTENSO' 
    FROM TABELA_DE_CLIENTES;
```

<h3>Funções matemáticas</h3>

- ROUND -> arredonda um número

```sql
SELECT ROUND(3.433, 2), ROUND(3.437,2)
-- 1º arredonda para 3.43 e o 2º para 3.44
```

- CEILING -> arredonda para cima

```sql
SELECT CEILING(3.433)
-- arredonda para 4
```

- FLOOR -> arredonda para baixo

```sql
SELECT FLOOR(3.433)
-- arredonda para 3
```

- POWER -> eleva um número a uma potência

```sql
SELECT POWER(2, 10)
-- 2 elevado a 10 = 1024
```

- EXP -> retorna o valor de e elevado a um número

```sql
SELECT EXP(3)
-- e elevado a 3 = 20.0855369231877
```

- SQRT -> retorna a raiz quadrada de um número

```sql
SELECT SQRT(36)
-- raiz quadrada de 36 = 6
```

- ABS -> retorna o valor absoluto de um número

```sql
SELECT ABS(-10)
-- valor absoluto de -10 = 10
```

<br>

<h3>Conversão de dados</h3>

- CONVERT -> converte um tipo de dado em outro

```sql
SELECT DATA_DE_NASCIMENTO, CONVERT(VARCHAR(25), DATA_DE_NASCIMENTO, 106) 
    FROM TABELA_DE_CLIENTES;

-- Convertendo a data de nascimento para o formato dd mon yyyy
```

- CAST -> converte um tipo de dado em outro

```sql
SELECT 
    NOME_DO_PRODUTO, 
    CONCAT('O preco de lista é ', CAST(PRECO_DE_LISTA AS VARCHAR(10))) AS PRECO FROM TABELA_DE_PRODUTOS;
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


