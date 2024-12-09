<h1 align="center">Switch Expression</h1>

<p>
    Switch expression é uma sintáxe mais limpa para o switch case, podemos usar da seguinte fomra:
</p>

<h3>Usando Switch Expression</h3>

```csharp

VideoGame console = VideoGame.XboxSeries;

string empresa = console switch
{
    VideoGame.XboxSeries => "Microsoft",
    VideoGame.PS5 => "Sony",
    VideoGame.NintendoSwitch => "Nintendo",
    _ => "Desconhecido"
};
```

Essa expressão é a substituição do switch tradicional:

```csharp
VideoGame console = VideoGame.XboxSeries;

switch (console)
{
    case VideoGame.XboxSeries:
        empresa = "Microsoft";
        break;
    
    case VideoGame.PS5:
        empresa = "Sony";
        break;
    
    case VideoGame.NintendoSwitch:
        empresa = "Nintendo";
        break;
    
    default:
        empresa = "Desconhecido";
        break;
}
```

### Usando com funções

Esse é um exemplo totalmente didático, podemos executar funções que retornam o tipo especificado pela variável, no nosso caso `empresa` é uma `string`

```csharp
string empresa = console switch
{
    VideoGame.XboxSeries => atribuiValor("Microsoft"),
    VideoGame.PS5 => atribuiValor("Sony"),
    VideoGame.NintendoSwitch => atribuiValor("Nintendo"),
    _ => atribuiValor("Desconhecido")
};

```