<h1 align="center"> Cursor</h1>

<p>
    Cursor é um objeto que permite percorrer os registros de um conjunto de resultados. 
    Ele é utilizado para processar linha a linha de um conjunto de resultados.
</p>

<h2>Declaração</h2>

```sql
DECLARE NomeDoCursor CURSOR FOR
SELECT Campo1, Campo2
FROM Tabela
```

<h2>Abertura</h2>

```sql
OPEN NomeDoCursor
```

<h2>Recuperação de Dados</h2>

```sql
FETCH NEXT FROM NomeDoCursor INTO @Variavel1, @Variavel2
```

<h2>Fechamento</h2>

```sql
CLOSE NomeDoCursor
DEALLOCATE NomeDoCursor
```

<h2>Exemplo</h2>

```sql
DECLARE CursorClientes CURSOR FOR
SELECT Nome, Email
FROM Clientes

OPEN CursorClientes

DECLARE @Nome VARCHAR(100), @Email VARCHAR(100)

FETCH NEXT FROM CursorClientes INTO @Nome, @Email
WHILE @@FETCH_STATUS = 0
BEGIN
    PRINT 'Nome: ' + @Nome + ' - Email: ' + @Email
    FETCH NEXT FROM CursorClientes INTO @Nome, @Email
END

CLOSE CursorClientes
DEALLOCATE CursorClientes
```

<p>
    O comando <code>@@FETCH_STATUS</code> retorna o status da última operação de busca.
    O valor 0 indica que a busca foi bem-sucedida.
</p>