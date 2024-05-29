<h1 align="center">Número de Linhas - ROW_NUMBER()</h1>

- A função `ROW_NUMBER()` é usada para atribuir um número sequencial a cada linha de um conjunto de resultados

<h2>Exemplo:</h2>

```sql
SELECT ROW_NUMBER() OVER (ORDER BY Nome) AS Numero, * FROM Clientes;
```