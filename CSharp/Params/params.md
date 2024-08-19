<h1 align="center">Params</h1>

<p>
    Params permite que um método possa receber um número variável de
    elementos. Exemplo:
</p>

<br>

<h3>Usando Params</h3>

```csharp
public static void Soma(params int[] numeros)
{
    int resultado = 0;

    foreach (var num in numeros)
    {
        resultado += num;    
    }

    Console.WriteLine(resultado);
}
```

<h3>Executando método</h3>

```csharp
public static void Executar()
{
    Soma(1,2,3,4,5,6,7,8,9);
}
```