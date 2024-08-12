<h1 align="center"1>Explicit Operator</h1>

<p>
    Explicit Operator é um operador capaz de realizar conversões necessitando explicitar seu tipo, por exemplo:
</p>

<br>

<h3>Classe que possui o operador explícito</h3>

```csharp
public class PessoaEntity
{
    public string Nome { get; set; } = string.Empty;
    public int Idade { get; set; }

    public static explicit operator PessoaEntity(PessoaModel pessoaModel)
    {
        return new PessoaEntity() 
        { 
            Nome = pessoaModel.Nome, 
            Idade = pessoaModel.Idade 
        };
    }
}
```

<br>

<h3>Classe que será convertida em "PessoaEntity"</h3>

```csharp
public class PessoaModel
{
    public int Id { get; set; }
    public string Nome { get; set; } = string.Empty;
    public int Idade { get; set; }
}
```

<br>

<h3>Execução da conversão explícita</h3>

```csharp
public static class Execucao
{
    public static void Executar()
    {
        var pessoaModel = new PessoaModel()
            { 
                Id = 1, 
                Nome = "Luis", 
                Idade = 20 
            };

        //Conversão explícita
        PessoaEntity pessoa = (PessoaEntity) pessoaModel;
    }
}
```