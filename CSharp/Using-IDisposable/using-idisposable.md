<h1 align="center">Relação entre Using e IDisposable</h1>

<p>
    A instrução <code>using</code> serve para implementarmos
    determinado recurso que implemente a interface IDisposable.
    Ao final de sua execução, a implementação da interface entra
    em ação e executa o método <code>Dispose()</code>. Exemplo:
</p>

<br>

<h3>Classe que implementa IDisposable</h3>

```csharp
public class RecursoComDispose : IDisposable
{
    public void Dispose() => Console.WriteLine("Chamando método Dispose");
}
```

<br>

<h3>Using</h3>

```csharp
using (RecursoComDispose recurso = new RecursoComDispose())
{
    Console.WriteLine("Acessando recurso com dispose");
}
```

<br>

<h3>Saída da execução</h3>

```
Acessando recurso com dispose
Chamando método Dispose
```

<br>

<p>
    Ao tentar usar um recurso que não implementa IDisposable,
    resultará em um erro de compilação:    
</p>

```
CS1674: 'RecursoSemDisposable': O tipo usado em uma instrução using deve ser implicitamente conversível em 'System.IDisposable'.
```

<br>

<h3>Conversão do using pelo compilador (Descompilação)</h3>

```csharp
using System;
using System.Diagnostics;
using System.Reflection;
using System.Runtime.CompilerServices;
using System.Security;
using System.Security.Permissions;

[assembly: CompilationRelaxations(8)]
[assembly: RuntimeCompatibility(WrapNonExceptionThrows = true)]
[assembly: Debuggable(DebuggableAttribute.DebuggingModes.IgnoreSymbolStoreSequencePoints)]
[assembly: SecurityPermission(SecurityAction.RequestMinimum, SkipVerification = true)]
[assembly: AssemblyVersion("0.0.0.0")]
[module: UnverifiableCode]
[module: RefSafetyRules(11)]

public class RecursoComDispose : IDisposable
{
    public void Dispose()
    {
        Console.WriteLine("Chamando método Dispose");
    }
}

public static class Execucao
{
    public static void Executar()
    {
        RecursoComDispose recursoComDispose = new RecursoComDispose();
        try
        {
            Console.WriteLine("Acessando recurso com dispose");
        }
        finally
        {
            if (recursoComDispose != null)
            {
                ((IDisposable)recursoComDispose).Dispose();
            }
        }
    }
}

```