<h1 align="center">Função que retorna 2 valores</h1>

```csharp
using System;

namespace FuncaoRetorna2Valores
{
    class Program
    {
        static (int, int) Retorna2Valores(int a, int b)
        {
            return (a + b, a - b);
        }

        static void Main(string[] args)
        {
            int a = 10;
            int b = 5;

            var resultado = Retorna2Valores(a, b);

            Console.WriteLine($"Soma: {resultado.Item1}");
            Console.WriteLine($"Subtração: {resultado.Item2}");
        }
    }
}
```