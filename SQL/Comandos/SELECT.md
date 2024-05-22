<h1 align="center">SELECT + filtros</h1>

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