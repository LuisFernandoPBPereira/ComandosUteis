<h1 align="center"><code>is</code> e <code>or</code> Keywords</h1>

- Usamos o `is` para verificar se um objeto é de um tipo específico. 
- O `or` é usado para verificar se um objeto é de um dos tipos especificados.
- O `not` é usado para negar se um objeto é daquele tipo.

### `is` Keyword
```csharp
object frase = "Bom dia!";

if (frase is string)
{
    Console.WriteLine("A variável é uma string!");
}

// Podemos usar o "is" para fazer o cast do objeto verificado

object numero = 10;

if (numero is int num)
{
    Console.WriteLine($"A variável é inteira: {num}");
}
```

### `not` Keyword

```csharp
object frase = "Bom dia!";

if (frase is not int)
{
    Console.WriteLine("A variável não é um inteiro!");
}
```

### `or` Keyword

```csharp
object euler = 2.718281828459045;

if (euler is double or float)
{
    Console.WriteLine("A variável é um número de ponto flutuante!");
}
```

