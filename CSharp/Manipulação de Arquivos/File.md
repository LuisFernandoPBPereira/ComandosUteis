<h1 align="center">Comandos File</h1>

<p>
    O comando File é utilizado para manipular arquivos, como criar, ler, escrever, deletar, entre outros.
</p>

<h2>Exemplo de uso</h2>

- <h3>Lendo um arquivo</h3>

```csharp
var linhas = File.ReadAllLines("contas.txt");

Console.WriteLine(linhas.Length);

foreach (var linha in linhas)
{
    Console.WriteLine(linha);
}
```

<p>
    O método ReadAllLines do comando: 
    <code>File.ReadAllLines("contas.txt");</code>, lê todas as linhas do arquivo.
    <br><br>
    Podemos também visualizar a quantidade de linhas do arquivo.
</p>

<br>

- <h3>Ler bytes</h3>

```csharp
var bytesArquivo = File.ReadAllBytes("contas.txt");

Console.WriteLine($"Arquivo contas.txt possui {bytesArquivo.Length} bytes");
```

<p>
    O método ReadAllBytes do comando: 
    <code>File.ReadAllBytes("contas.txt");</code>, lê todos os bytes do arquivo.
    <br><br>
    Podemos também visualizar a quantidade de bytes do arquivo.
</p>

<br>

- <h3>Escrevendo um arquivo</h3>

```csharp
File.WriteAllText("escrevendoComClasseFile.txt", "Testando File.WriteAllText");
```

<p>
    O método WriteAllText do comando: 
    <code>File.WriteAllText("escrevendoComClasseFile.txt", "Testando File.WriteAllText");</code>, escreve um texto no arquivo.
</p>