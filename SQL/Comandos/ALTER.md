<h1 align="center">ALTER</h1>

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