<h1 align="center">Identity</h1>

<p>
    Identity é um pacote que permite a autenticação e autorização de usuários.
</p>

<h2>Instalação</h2>

<p>Em pacotes NuGet, pesquisar por:</p>

- Microsoft.AspNetCore.Identity.EntityFrameworkCore

<h2>Configuração</h2>

<h3>Adicionar o Identity no domínio da aplicação na Program.cs</h3>

```csharp
builder.Services.AddIdentity<Usuario, IdentityRole>()
    .AddEntityFrameworkStores<Contexto>()
    .AddDefaultTokenProviders();
```

<p>
    Onde <code>Usuario</code> é a classe que representa o usuário e <code>Contexto</code> é a classe que representa o contexto do banco de dados.
</p>

<br>

<h3>Adicionar o <code>UseAuthentication();</code> na Program.cs</h3>

```csharp
app.UseAuthentication();
app.UseAuthorization();
```

<p>
    O <code>UseAuthentication();</code> é responsável por autenticar o usuário, o inserimos acima do <code>UseAuthorization();</code> para que o usuário seja autenticado antes de ser autorizado.
</p>

<br>

<h3>Criar uma classe para representar o usuário:</h3>

```csharp
using Microsoft.AspNetCore.Identity;

public class Usuario : IdentityUser
{
    public DateTime DataNascimento { get; set; }
    public Usuario() : base(){}
}
```

<p>
    A classe <code>Usuario</code> herda de <code>IdentityUser</code> e possui um atributo <code>DataNascimento</code>
</p>

<br>

<h3>Criar uma classe para representar o contexto do banco de dados:</h3>

```csharp
using Microsoft.AspNetCore.Identity.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore;

public class UsuarioDbContext : IdentityDbContext<Usuario>
{
    public UsuarioDbContext(DbContextOptions<UsuarioDbContext> options) : base(options){}
}
```

<p>
    A classe <code>UsuarioDbContext</code> herda de <code>IdentityDbContext</code> e necessita que uma entidade seja passada em seu tipo, no caso: <code>Usuario</code>
</p>
