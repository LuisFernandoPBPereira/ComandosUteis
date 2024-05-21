<h1 align="center">Arquivo XML</h1>

<p>
    A serialização é o processo de converter um objeto ou um conjunto de objetos em um formato que possa ser armazenado ou transmitido e reconstruído posteriormente. A serialização XML é um tipo de serialização que converte um objeto em um arquivo XML.
</p>

> [!IMPORTANT]
> Para serializar um objeto em XML, é necessário que a classe tenha um construtor sem parâmetros, caso contrário será lançada uma exceção do tipo: System.InvalidOperationException

<h2>Exemplo de uso</h2>

- <h3>Serializando uma lista de objetos</h3>

```csharp
var xmlSerializer = new XmlSerializer(_listaDeContas.GetType());

using (FileStream fs = new FileStream("listaContas.xml", FileMode.Create))
{
    xmlSerializer.Serialize(fs, _listaDeContas);
}
```

<p>
    O método Serialize do comando: 
    <code>xmlSerializer.Serialize(fs, _listaDeContas);</code>, serializa o objeto em um arquivo XML.
</p>

<br>

- <h3>Deserializando uma lista de objetos</h3>

```csharp
XmlSerializer serializer = new XmlSerializer(_listaDeContas.GetType());

using (FileStream stream = new FileStream("listaContas.xml", FileMode.Open))
{
    List<ContaCorrente> contas = (List<ContaCorrente>)serializer.Deserialize(stream);

    foreach (var item in contas)
    {
        // Listar os itens da lista aqui
    }
}
```

<p>
    O método Deserialize do comando: 
    <code>serializer.Deserialize(stream);</code>, deserializa o arquivo XML em um objeto.
</p>




