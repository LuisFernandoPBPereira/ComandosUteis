<h1 align="center">Instanciar uma classe genérica</h1>

### Exemplo de uso

Aqui temos um método que mapeia um texto para um objeto genérico. O método recebe um array de nomes de propriedades e um array de valores de propriedades. A partir desses arrays, o método instancia um objeto genérico e mapeia os valores para as propriedades do objeto.

```csharp
private T MapearTextoParaObjeto<T>(string[] nomesPropriedades, string[] valoresPropriedades)
{
    // INSTÂNCIA DA CLASSE GENÉRICA
    T objetoParaMapeamento = Activator.CreateInstance<T>();

    if(objetoParaMapeamento != null)
    {
        for (int i = 0; i < nomesPropriedades.Length; i++)
        {
            string nomePropriedade = nomesPropriedades[i];
            
            // Capturamos a propriedade da classe genérica
            PropertyInfo? propertyInfo = objetoParaMapeamento.GetType().GetProperty(nomePropriedade);
    
            if(propertyInfo != null)
            {
                // Capturamos o tipo da propriedade
                Type propertyType = propertyInfo.PropertyType;
                
                string valor = valoresPropriedades[i];

                // Convertendo o valor para o tipo da propriedade
                object valorConvertido = Convert.ChangeType(valor, propertyType);

                // Setamos o valor convertido na propriedade
                propertyInfo.SetValue(objetoParaMapeamento, valorConvertido);
            }
        }
    }

    return objetoParaMapeamento;
}
```