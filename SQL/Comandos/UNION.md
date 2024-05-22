<h1 align="center">UNION</h1>

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