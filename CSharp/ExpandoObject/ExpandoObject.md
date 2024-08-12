<h1 align="center">Expando Object</h1>

<p>
    Expando Object é a representação de um objeto onde seus membros são adicionados dinamicamente em tempo execução, por exemplo:
</p>

```csharp
public static class Execucao
{
    public static void Executar()
    {
        dynamic json = """{"De": "Luis" , "Para": "Carlos"}""";

        // Usando ExpandoObject para desserializar um json
        var mensagem = JsonSerializer.Deserialize<ExpandoObject>(json);

        mensagem.Texto = $"Olá, {mensagem.Para}";

        EnviarMensagem(mensagem);
    }

    private static void EnviarMensagem(dynamic mensagem)
    {
        Console.WriteLine($"De: {mensagem.De}");
        Console.WriteLine($"Para: {mensagem.Para}");
        Console.WriteLine($"Texto: {mensagem.Texto}");
    }
}
```

