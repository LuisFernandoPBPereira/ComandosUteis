<h1 align="center">Private Protected</h1>

<p>
    O modificador <strong>private protected</strong> é uma combinação dos modificadores <strong>private</strong> e <strong>protected</strong>. 
    Ele permite que a classe derivada acesse o membro protegido, mas apenas se a classe derivada estiver no mesmo assembly.
    Em outras palavras, apenas classes que herdam da classe que contém o membro e classes que estão no mesmo projeto podem acessá-lo.
</p>

<h2>Exemplo</h2>

- <h3>Private protected em um método</h3> 

```csharp
private protected abstract double getBonificacao();
```

<p>
    Neste exemplo, o método <strong>getBonificacao</strong> é privado e protegido. Isso significa que ele pode ser acessado por classes derivadas, mas apenas se a classe derivada estiver no mesmo assembly.
    Em outras palavras, apenas classes que herdam da classe que contém o método e classes que estão no mesmo projeto podem acessá-lo.
</p>