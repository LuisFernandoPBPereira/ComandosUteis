<h1 align="center">Método com Reflection</h1>

## Como obter um método de uma classe com Reflection?

```csharp
// Capturamos o tipo da classe
var tipoDaClasse = typeof(RelatorioDeBoleto);

// Capturamos os construtores da classe
var construtores = tipoDaClasse.GetConstructors();

// Capturamos o primeiro construtor que tenha um parâmetro e um nome específico
var primeiroConstrutor = construtores
    .Single(c => c.GetParameters().Length == 1 
    && c.GetParameters().Any(p => p.Name == nomeParametroConstutor));

// Capturamos a instância da classe através do construtor obtido
// O método Invoke é responsável por executar o construtor, consequentemente instancia a classe
var instanciaDaClasse = primeiroConstrutor.Invoke(new object[] { parametroConstrutor });

// Capturamos o método da classe
var metodoParaExecucao = tipoDaClasse.GetMethod(nomeMetodo);

// Executamos o método da classe
metodoParaExecucao.Invoke(instanciaDaClasse, new object[] { parametroMetodo });
```