<h1 align="center">Protected Internal</h1>

<p>
    O modificador <strong>protected internal</strong> é uma combinação dos modificadores <strong>protected</strong> e <strong>internal</strong>. 
    Ele permite que a classe derivada e as classes do mesmo assembly acessem o membro protegido.
</p>

<h2>Exemplo</h2>

- <h3>Protected internal em um método</h3> 

```csharp
protected internal abstract double getBonificacao();
```

<p>
    Neste exemplo, o método <strong>getBonificacao</strong> é protegido e interno. Isso significa que ele pode ser acessado por classes derivadas e classes do mesmo assembly.
    Em outras palavras, apenas classes que herdam da classe que contém o método e classes que estão no mesmo projeto podem acessá-lo.
</p>
