<h1 align="center">Comandos Stream</h1>

<p>
    O comando Stream é utilizado para manipular arquivos, assim como o FileStream, ambos são do namespace System.IO.
</p>

<h2>Exemplo de uso</h2>

- <h3>Abrindo um arquivo</h3>

```csharp
public static void AbrirArquivo()
{
    using (var fluxoDoArquivo = new FileStream("endereco-do-arquivo", FileMode.Open))
    {
        var leitor = new StreamReader(fluxoDoArquivo);

        while (leitor.EndOfStream == false)
        {
            // Carrega por partes
            var linha = leitor.ReadLine();
        }
    }
}
```

<p>
    A linha do comando: 
    <code>using (var fluxoDoArquivo = new FileStream("endereco-do-arquivo", FileMode.Open))</code>, abre o arquivo para leitura.
    <br><br>
    O método ReadLine do comando: 
    <code>leitor.ReadLine();</code>, lê uma linha do arquivo.
</p>

<br>

- <h3>Abrindo um arquivo usando apenas o Stream Reader</h3>

```csharp
public string[] GetCliente()
{
    using (StreamReader streamReader = new StreamReader("../../../JSONs/clientes.json"))
    {
        var json = streamReader.ReadToEnd();
        
        // ...
    }
}
```

<p>
    O método ReadToEnd do comando: 
    <code>streamReader.ReadToEnd();</code>, lê todo o conteúdo do arquivo.
    <br><br>
    Podemos notar que é mais simples de usar o StreamReader, pois ele já faz a leitura do arquivo inteiro.
</p>

<br>

- <h3>Criando um arquivo</h3>

```csharp
    public static void CriarArquivoComWriter()
    {
        using (var fluxoDeArquivo = new FileStream("endereco-do-arquivo", FileMode.Create))
        using (var escritor = new StreamWriter(fluxoDeArquivo))
        {
            escritor.Write("000,0000,000.00,Nome");
        }
    }
```

<p>
    A linha do comando: 
    <code>using (var fluxoDeArquivo = new FileStream("endereco-do-arquivo", FileMode.Create))</code>, cria o arquivo.
    <br><br>
    O método Write do comando: 
    <code>escritor.Write("000,0000,000.00,Nome");</code>, escreve no arquivo.
    <br><br>
    Note que também precisamos do FileStream para criar o arquivo.
</p>

<br>

- <h3>Método Flush</h3>

```csharp
public static void TestaEscrita()
{
    using (var fluxoDeArquivo = new FileStream("endereco-do-arquivo", FileMode.Create))
    using (var escritor = new StreamWriter(fluxoDeArquivo))
    {
        for (int i =0; i<100; i++)
        {
            escritor.WriteLine($"Linha {i}");
            escritor.Flush(); // Despeja o buffer para o Stream
            Console.WriteLine($"Linha {i} foi escrita no arquivo. Tecle enter...");
            Console.ReadLine();
        }
    }
}
```

<p>
    O método Flush do comando: 
    <code>escritor.Flush();</code>, despeja o buffer para o Stream.
    <br><br>
    O Flush é utilizado para escrever no arquivo a cada linha, sem a necessidade de esperar o buffer encher.
</p>