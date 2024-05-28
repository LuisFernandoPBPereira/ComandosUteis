<h1 align="center">Criação do Token JWT</h1>

<p>
    JWT (JSON Web Token) é um token que carrega informações em formato JSON e é útil para autenticação e autorização.
</p>

<h2>Instalação</h2>

<p>Em pacotes NuGet, pesquisar por:</p>

- System.IdentityModel.Tokens.Jwt

<h2>Configuração</h2>

<h3>Adicionar o JWT no domínio da aplicação na Program.cs</h3>

```csharp
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddJwtBearer(options =>
    {
        options.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuer = true,
            ValidateAudience = true,
            ValidateLifetime = true,
            ValidateIssuerSigningKey = true,
            ValidIssuer = Configuration["Jwt:Issuer"],
            ValidAudience = Configuration["Jwt:Audience"],
            IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(Configuration["Jwt:Key"]))
            ClockSkew = TimeSpan.Zero
        };
    });
```

<p>
    Caso precise usar o ValidateIssuer, ValidateAudience e ValidateLifetime, mantenha desta forma, caso contrário, podemos colocar seus valores para false.
    <br><br>
    Não podemos nos esquecer do <code>ClockSkew = TimeSpan.Zero</code>, ele é responsável por validar o tempo de autenticação do usuário.
</p>

<br>

<h3>Criar uma classe para gerar o token:</h3>

<p>Vamos por partes, primeiro vamos criar uma classe para gerar o token, depois de criada, seguiremos com o construtor:</p>

```csharp
private IConfiguration _configuration;
public TokenService(IConfiguration configuration)
{
    _configuration = configuration;
}
```

<p>
    Fazemos a injeção de dependência de IConfiguration para pegar os valores do appsettings.json, ou mesmo a sua secrets.json.
</p>

<br>

<h3>Crie um método:</h3>

```csharp
public string GenerateToken(Usuario usuario)
{
    // Geração do token
}
```

<p>
    Precisamos receber por parâmetro, a entidade que será autenticada
</p>

<br>

<h3>Claims:</h3>

```csharp
Claim[] claims = new Claim[]
    {
        new Claim("username", usuario.UserName),
        new Claim("id", usuario.Id),
        new Claim(ClaimTypes.DateOfBirth, usuario.DataNascimento.ToString())
    };
```

<p>
    As claims são informações que ficarão no token, como o nome do usuário, id, data de nascimento, etc.
</p>

<br>

<h3>Chave e Credencial de Signing:</h3>

```csharp
    var key = new SymmetricSecurityKey
    (
        Encoding.UTF8.GetBytes(_configuration["SymmetricSecurityKey"])
    );

    var signingCredentials = new SigningCredentials
    (
        key,
        SecurityAlgorithms.HmacSha256
    );
```

<p>
    A chave é a responsável por pegar um valor qualquer (definido por você), e transformar em um valor criptografado.
    <br><br>
    A credencial de signing é a responsável por assinar o token, ou seja, ela é a responsável por garantir que o token é válido.
</p>

<br>

<h3>Criando o token:</h3>

```csharp
var token = new JwtSecurityToken
(
    expires: DateTime.Now.AddMinutes(20),
    claims: claims,
    signingCredentials: signingCredentials
);
```

<p>
    O token é criado com a data de expiração, as claims e a credencial de signing.
    <br><br>
    Caso você queira retornar o JWT em formato de string, basta fazer o seguinte:
</p>

```csharp
return new JwtSecurityTokenHandler().WriteToken(token);
```

<p>O código todo ficará desta maneira:</p>

```csharp
public class TokenService
{
    private IConfiguration _configuration;
    public TokenService(IConfiguration configuration)
    {
        _configuration = configuration;
    }
    public string GenerateToken(Usuario usuario)
    {
        Claim[] claims = new Claim[]
        {
            new Claim("username", usuario.UserName),
            new Claim("id", usuario.Id),
            new Claim(ClaimTypes.DateOfBirth, usuario.DataNascimento.ToString())
        };

        var key = new SymmetricSecurityKey
        (
            Encoding.UTF8.GetBytes(_configuration["SymmetricSecurityKey"])
        );

        var signingCredentials = new SigningCredentials
        (
            key, 
            SecurityAlgorithms.HmacSha256
        );

        var token = new JwtSecurityToken
        (
            expires: DateTime.Now.AddMinutes(20),
            claims: claims,
            signingCredentials: signingCredentials
        );

        return new JwtSecurityTokenHandler().WriteToken(token);
    }
}
```