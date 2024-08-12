<h1 align="center">Delegate</h1>

<p>
    Delegate representa a referência à um método, onde a execução do método é dada através do delegate, por exemplo:
</p>

<br>

<h3>Métodos de Operações Matemáticas</h3>

```csharp
public class OperacaoMatematica
{
    public double Soma(double num1, double num2) => num1 + num2;
    public double Subtracao(double num1, double num2) => num1 - num2;
    public double Multiplicacao(double num1, double num2) => num1 * num2;
    public double Divisao(double num1, double num2) => num1 / num2;
}
```

<br>

```csharp
public static class Execucao
{
    // Declaração do delegate
    public delegate double Calculadora(double num1, double num2);
    
    public static void Executar()
    {
        var operacaoMatematica = new OperacaoMatematica();

        Calculadora calculadora = operacaoMatematica.Soma;

        var resultado = calculadora(1, 1);

        Console.WriteLine($"O resultado da {calculadora.Method.Name} é: {resultado}");
    }
}
```

<br>

<h2>Execução de mais de um método com delegate</h2>

<br>

<h3>Classe com operações matemáticas</h3>

```csharp
public class OperacaoMatematica
{
    public void Soma(double num1, double num2) 
        => Console.WriteLine($"O resultado da soma é: {num1 + num2}");

    public void Subtracao(double num1, double num2) 
        => Console.WriteLine($"O resultado da subtração é: {num1 - num2}");

    public void Multiplicacao(double num1, double num2) 
        => Console.WriteLine($"O resultado da multiplicação é: {num1 * num2}");

    public void Divisao(double num1, double num2) 
        => Console.WriteLine($"O resultado da divisão é: {num1 / num2}");
}
```

<br>

<h3>Execução do delegate</h3>

```csharp
public static class Execucao
{
    // Declaração do delegate
    public delegate void Calculadora(double num1, double num2);
    
    public static void Executar()
    {
        var operacaoMatematica = new OperacaoMatematica();

        // Atribuindo funções para o delegate
        Calculadora calculadora = operacaoMatematica.Soma;
        calculadora += operacaoMatematica.Subtracao;
        calculadora += operacaoMatematica.Multiplicacao;
        calculadora += operacaoMatematica.Divisao;

        calculadora(10, 2);
    }
}
```