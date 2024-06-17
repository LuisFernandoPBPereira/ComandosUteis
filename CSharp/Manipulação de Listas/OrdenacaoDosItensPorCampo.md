<h1 align="center">Ordenação de Lista</h1>


<p>
    Temos uma lista de clienes e queremos ordená-la pelo nome, podemos fazer isso de forma simples e rápida com alguns comandos.
</p>

<h3>Sort</h3>

```csharp
_listaClientes.Sort((x, y) => x.Nome.CompareTo(y.Nome));
```

<br>

<h3>OrderBy</h3>

```csharp
_listaClientes = _listaClientes.OrderBy(cliente => cliente.Nome).ToList();
```
