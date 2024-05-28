<h1 align="center">Criação de Usuários com Identity</h1>

<h2>Exemplo:</h2>

```csharp

public class UsuarioService
{
    private IMapper _mapper;
    private UserManager<Usuario> _userManager;

    public UsuarioService(IMapper mapper, 
                          UserManager<Usuario> userManager)
    {
        _mapper = mapper;
        _userManager = userManager;
    }

    public async Task Cadastra(CreateUsuarioDto usuarioDto)
    {
        Usuario usuario = _mapper.Map<Usuario>(usuarioDto);

        var result = await _userManager.CreateAsync(usuario, usuarioDto.Password);

        if (result.Succeeded == false) 
            throw new Exception("Falha ao cadastrar usuário");
    }
    // ...
}
```


<h2>Explicação:</h2>

<p>
    Fazemos a injeção de dependência de <code>IMapper</code> e <code>UserManager</code> no construtor da classe <code>UsuarioService</code>.
    <br><br>
    Para criar um usuário, utilizamos o método <code>CreateAsync</code> do <code>UserManager</code>, passando o usuário e a senha.
    O <code>UserManager</code> é uma classe que gerencia usuários, e é responsável por criar, deletar, atualizar e buscar usuários.
    <br><br>
    O método <code>CreateAsync</code> cria um usuário, e retorna um <code>IdentityResult</code> que contém informações sobre o sucesso ou falha da operação.
    <br><br>
    Se a operação falhar, lançamos uma exceção.
</p>