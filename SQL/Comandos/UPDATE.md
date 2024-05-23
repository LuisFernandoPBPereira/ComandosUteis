<h1 align="center">UPDATE</h2>

```sql
UPDATE nome-da-tabela 
    SET nome-da-coluna = novo-valor 
    WHERE condicao;
```

- Atualizando campos de uma tabela, usando uma tabela de outro banco de dados

```sql
UPDATE A SET A.PRECO_LISTA = B.PRECO_DE_LISTA
    FROM
        PRODUTOS AS A
    INNER JOIN
        SUCOS_FRUTAS.DBO.TABELA_DE_PRODUTOS AS B
    ON
        A.CODIGO = B.CODIGO_DO_PRODUTO;
```
