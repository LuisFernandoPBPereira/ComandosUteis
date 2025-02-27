<h1 align="center">Nomear Tabela e Campo</h1>


Caso o nome da tabela ou de um campo no banco de dados esteja diferente do nome da classe, é possível informar o nome da tabela através do atributo `Table` e o nome do campo através do atributo `Column`.

```csharp
[Table("NomeDaTabela")]
public class NomeDaClasse
{
    [Column("NomeDoCampo")]
    public int Id { get; set; }
}
```