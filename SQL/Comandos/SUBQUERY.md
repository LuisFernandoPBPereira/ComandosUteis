<h1 align="center">SUBQUERY</h1>

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