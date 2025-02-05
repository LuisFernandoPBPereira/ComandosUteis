<h1 align="center">Exception Handler</h1>

## O que é Exception Handler?

Exception Handler é uma forma de assegurar que o código irá tratar as exceções que podem ocorrer durante a execução do programa de forma global.

## Implementação


### Program.cs
```csharp
// ...

// Inserimos o middleware de tratamento de exceções com um lambda descartável
// (Podemos usar o corpo do lambda para tratar a exceção)

app.UseExceptionHandler(_ => { });

// ...
```

<br>

### Criando exceção personalizada
```csharp
public class NullReferenceExceptionHandler : IExceptionHandler
{
    public ValueTask<bool> TryHandleAsync(
        HttpContext httpContext,
        Exception exception,
        CancellationToken cancellationToken
    )
    {
        if(exception is not NullReferenceException)
        {
            return new ValueTask<bool>(false);
        }

        ProblemDetails problemDetails = new ProblemDetails
        {
            Title = "Null Reference Exception",
            Detail = exception.Message,
            Status = StatusCodes.Status500InternalServerError
        };

        httpContext.Response.StatusCode = problemDetauls.Status.Value;
        httpContext.Response.WriteAsJsonAsync(problemDetails);

        return ValueTask.FromResult(true);
    }
}
```

<br>

### Adicionando handler de exceção na Program.cs
```csharp
// ...

builder.Serivces.AddExceptionHandler<NullReferenceExceptionHandler>();

// ...
```