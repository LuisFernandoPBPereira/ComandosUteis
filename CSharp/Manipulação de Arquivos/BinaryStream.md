<h1 align="center">Comandos BinaryStream</h1>

<p>
    O comando BinaryStream é utilizado para manipular arquivos binários, como criar, ler, escrever, deletar, entre outros.
</p>

<h2>Exemplo de uso</h2>

- <h3>Lendo um arquivo binário</h3>

```csharp
public static void LeituraBinaria()
{
    using (var fluxoDeArquivo = new FileStream("TestaEscrita.txt", FileMode.Open))
    using (var leitor = new BinaryReader(fluxoDeArquivo))
    {
        var agencia = leitor.ReadInt32();
        var numeroDaConta = leitor.ReadInt32();
        var saldo = leitor.ReadDouble();
        var nome = leitor.ReadString();

        Console.WriteLine($"Agência: {agencia}\n" +
                          $"Numero conta: {numeroDaConta}\n" +
                          $"Saldo: {saldo}\n" +
                          $"Titular: {nome}");
    }
}
```

<p>
    A linha do comando: 
    <code>using (var fluxoDeArquivo = new FileStream("TestaEscrita.txt", FileMode.Open))</code>, abre o arquivo para leitura.
    <br><br>
    O método ReadInt32 do comando: 
    <code>leitor.ReadInt32();</code>, lê um inteiro de 4 bytes do arquivo.
    <br><br>
    O método ReadDouble do comando: 
    <code>leitor.ReadDouble();</code>, lê um double de 8 bytes do arquivo.
    <br><br>
    O método ReadString do comando: 
    <code>leitor.ReadString();</code>, lê uma string do arquivo.
</p>

<br>

- <h3>Escrevendo um arquivo binário</h3>

```csharp
public static void CriarArquivoComBinaryWriter()
{
    using (var fluxoDeArquivo = new FileStream("TestaEscrita.txt", FileMode.Create))
    using (var escritor = new BinaryWriter(fluxoDeArquivo))
    {
        escritor.Write(000);
        escritor.Write(000000);
        escritor.Write(000.00);
        escritor.Write("Nome");
    }
}
```

<p>
    A linha do comando: 
    <code>using (var fluxoDeArquivo = new FileStream("TestaEscrita.txt", FileMode.Create))</code>, cria o arquivo.
    <br><br>
    O método Write do comando: 
    <code>escritor.Write(000);</code>, escreve um inteiro de 4 bytes no arquivo.
    <br><br>
    O método Write do comando: 
    <code>escritor.Write(000000);</code>, escreve um inteiro de 4 bytes no arquivo.
    <br><br>
    O método Write do comando: 
    <code>escritor.Write(000.00);</code>, escreve um double de 8 bytes no arquivo.
    <br><br>
    O método Write do comando: 
    <code>escritor.Write("Nome");</code>, escreve uma string no arquivo.
</p>
