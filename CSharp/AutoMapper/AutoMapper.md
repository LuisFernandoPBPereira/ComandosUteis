<h1 align="center">AutoMapper</h1>

<p>
    AutoMapper é uma library que permite mapear objetos de um tipo para outro.
</p>

<h2>Instalação</h2>

<p>Em pacotes NuGet, pesquisar por:</p>

- AutoMapper

<h2>Configuração</h2>

<h3>Adicionar o AutoMapper no domínio da aplicação na Program.cs</h3>

```csharp
builder.Services.AddAutoMapper(AppDomain.CurrentDomain.GetAssemblies());
```

<br>

<h3>Criar uma classe para mapear determinado objeto:</h3>

```csharp
using AutoMapper;

public class ClassProfile : Profile
{
	public FilmeProfile()
	{
		CreateMap<DTO, ClasseDesejada>();	
	}
}
```

<br>

<h3>Fazer a injeção de dependência no local desejado:</h3>

```csharp
private IMapper _mapper;

public Classe(IMapper mapper)
{
	_mapper = mapper;	
}
```

<br>

<h3>Utilizar o mapeamento:</h3>

```csharp
Classe classe = _mapper.Map<Classe>(dtoParaMapear);
```

<br>

<h3>Explicitando relacionamento:</h3>

```csharp
public class CinemaProfile : Profile
{
    public CinemaProfile()
    {
        CreateMap<CreateCinemaDto, Cinema>();

        CreateMap<Cinema, ReadCinemaDto>()
			.ForMember(cinemaDto => cinemaDto.Endereco,
					   opt => opt.MapFrom(cinema => cinema.Endereco))
			.ForMember(cinemaDto => cinemaDto.Sessoes,
					   opt => opt.MapFrom(cinema => cinema.Sessoes));

        CreateMap<UpdateCinemaDto, Cinema>();
    }
}
```
<p>
	No exemplo acima, o AutoMapper irá mapear o objeto Cinema para o objeto ReadCinemaDto, porém, o objeto ReadCinemaDto possui um atributo do tipo Endereco e um atributo do tipo Sessoes. Para mapear esses atributos, é necessário explicitar o relacionamento entre eles.
</p>
