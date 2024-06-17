<h1 align="center">Ordenação de Lista (SORT)</h1>

```csharp
// Temos uma lista de clienes e queremos ordená-la pelo nome,
// com o método Sort(), podemos fazer isso de forma simples e rápida

_listaClientes.Sort((x, y) => x.Nome.CompareTo(y.Nome));
```