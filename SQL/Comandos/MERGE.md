<h1 align="center">MERGE</h1>

<p>
    Comando que combina as operações de INSERT e UPDATE em uma única instrução. O comando MERGE é útil quando é necessário sincronizar duas tabelas, ou seja, quando é necessário atualizar uma tabela com os dados de outra tabela.
</p>

- Sintaxe básica

```sql	
MERGE INTO nome-da-tabela AS destino
    USING nome-da-tabela AS origem
    ON condicao
    WHEN MATCHED THEN
        UPDATE SET nome-da-coluna = novo-valor
    WHEN NOT MATCHED THEN
        INSERT 
            (nome-da-coluna) 
        VALUES 
            (novo-valor);
```
