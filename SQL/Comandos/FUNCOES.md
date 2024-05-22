<h1 align="center">FUNÇÕES</h1>

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