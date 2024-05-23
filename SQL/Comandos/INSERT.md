<h1 align="center">INSERT</h1>

- Inserindo campos em uma tabela

```sql
INSERT INTO nome-da-tabela (campos) VALUES (valores);
```

- Inserindo campos de uma tabela de um banco de dados em outro banco de dados

```sql
INSERT INTO PRODUTOS 
    SELECT
        CODIGO_DO_PRODUTO AS CODIGO, 
        NOME_DO_PRODUTO AS DESCRITOR,
        SABOR,
        TAMANHO,
        EMBALAGEM,
        PRECO_DE_LISTA AS PRECO_LISTA
    FROM 
        SUCOS_FRUTAS.DBO.TABELA_DE_PRODUTOS;
```

<p>
    Como podemos notar, no SELECT há um mapeamento dos campos da tabela de origem para os campos da tabela de destino, deixandos-os
    de maneira que o nome dos campos correspondam com os campos do destino.
</p>