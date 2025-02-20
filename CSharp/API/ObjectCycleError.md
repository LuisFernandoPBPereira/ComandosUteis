<h1 align="center">Object Cycle</h1>

O erro de Object Cycle se dá quando uma entidade faz referência a outra entidade que por sua vez faz referência a primeira entidade, criando um ciclo infinito.

<br>

Para evitar esse erro, podemos configurar na Program.cs o seguinte código:

```csharp
builder.Services.Configure<Microsoft.AspNetCore.Http.Json.JsonOptions>(options =>
{
    options.SerializerOptions.ReferenceHandler = ReferenceHandler.IgnoreCycles;
});
```