<h1 align="center">Login de Usuário com Identity</h1>

<h2>Exemplo:</h2>

```csharp
public class UsuarioService
{
    private SignInManager<Usuario> _signInManager;
    private TokenService _tokenService;

    public UsuarioService(SignInManager<Usuario> signInManager, 
                          TokenService tokenService)
    {
        _signInManager = signInManager;
        _tokenService = tokenService;
    }

    public async Task<string> Login(LoginUsuarioDto usuarioDto)
    {
        string token = string.Empty;
        var result = await _signInManager.PasswordSignInAsync
        (
            usuarioDto.Username, 
            usuarioDto.Password, 
            false, 
            false
        );

        if (result.Succeeded == false)
            throw new Exception("Usuário não autenticado");

        var usuario = _signInManager
            .UserManager
            .Users
            .FirstOrDefault(user => user.NormalizedUserName == usuarioDto.Username.ToUpper());

        if (usuario != null)
            token = _tokenService.GenerateToken(usuario);

        return token;
    }
}
```

<h2>Explicação:</h2>

<p>
    Fazemos a injeção de dependência de <code>SignInManager</code> e <code>TokenService</code> no construtor da classe <code>UsuarioService</code>.
    <br><br>
    Para autenticar um usuário, utilizamos o método <code>PasswordSignInAsync</code> do <code>SignInManager</code>, passando o nome de usuário e a senha.
    O <code>SignInManager</code> é uma classe que gerencia a autenticação de usuários.
    <br><br>
    O método <code>PasswordSignInAsync</code> autentica o usuário, e retorna um <code>SignInResult</code> que contém informações sobre o sucesso ou falha da operação.
    <br><br>
    Se a operação falhar, lançamos uma exceção.
    <br><br>
    Após autenticar o usuário, buscamos o usuário no banco de dados, e geramos um token JWT com as informações do usuário.
</p>
