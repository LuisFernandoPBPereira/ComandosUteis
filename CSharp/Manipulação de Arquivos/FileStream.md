<h1 align="center">Comandos FileStream</h1>

<p>
    O comando FileStream é utilizado para manipular arquivos, como criar, ler, escrever, deletar, entre outros.
</p>

<h2>Exemplo de uso</h2>

- <h3>Abrindo um arquivo</h3>

```csharp
public static void AbrirArquivo()
{
    var bytesLidos = -1;

    using (var fluxoDoArquivo = new FileStream("endereco-do-arquivo", FileMode.Open))
    {
        var buffer = new byte[1024]; // 1 KB

        while (bytesLidos != 0)
        {
            bytesLidos = fluxoDoArquivo.Read(buffer, 0, 1024);
            
            var utf8 = new UTF8Encoding();

            var texto = utf8.GetString(buffer, 0, bytesLidos);
            Console.Write(texto);
        }

        // Fecha a leitura do arquivo
        fluxoDoArquivo.Close();
    }
}
```

<p>
    A linha do comando: 
    <code>using (var fluxoDoArquivo = new FileStream("endereco-do-arquivo", FileMode.Open))</code>, abre o arquivo para leitura.
    <br><br>
    O método Read do comando: 
    <code>fluxoDoArquivo.Read(buffer, 0, 1024);</code>, recebe o buffer, a posição inicial e a quantidade de bytes a serem lidos, respectivamente.
    <br><br>
    O parâmetro do método GetString do comando: 
    <code>utf8.GetString(buffer, 0, bytesLidos);</code>, recebe o buffer, a posição inicial e a quantidade de bytes lidos, respectivamente.
</p>

<br>

- <h3>Criando um arquivo</h3>

```csharp
public static void CriarArquivo()
{
    using (var fluxoDeArquivo = new FileStream("endereco-arquivo-csv", FileMode.Create))
    {
        string contaComoString = "000,0000,0000.00,Nome";

        var encoding = Encoding.UTF8;

        var bytes = encoding.GetBytes(contaComoString);

        fluxoDeArquivo.Write(bytes, 0, bytes.Length);
    }
}
```

<p>
    A linha do comando: 
    <code>using (var fluxoDeArquivo = new FileStream("endereco-arquivo-csv", FileMode.Create))</code>, cria o arquivo no caminho especificado.
    <br><br>
    O método GetBytes do comando:
    <code>encoding.GetBytes(contaComoString);</code>, converte a string em bytes.
    <br><br>
    O método Write do comando:
    <code>fluxoDeArquivo.Write(bytes, 0, bytes.Length);</code>, escreve os bytes no arquivo, passando por parâmetro o buffer, a posição inicial e a quantidade de bytes a serem escritos, respectivamente.
</p>