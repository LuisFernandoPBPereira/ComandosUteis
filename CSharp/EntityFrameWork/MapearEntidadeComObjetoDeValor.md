<h1 align="center">Mapear Entidade com Objeto de Valor</h1>

### Exemplo: Mapeando Email

```csharp
modelBuilder.Entity<Cliente>()
    .OwnsOne(c => c.Email, e =>
    {
        e.WithOwner();
        e.Property(p => p.Value).HasColumnName("Email").IsRequired();
    });
```

### Exemplo: Mapeando Endereço

```csharp
modelBuilder.Entity<Cliente>()
    .OwnsOne(c => c.Endereco, e =>
    {
        e.WithOwner();
        e.Property(p => p.Logradouro).HasColumnName("Logradouro");
        e.Property(p => p.Numero).HasColumnName("Numero");
        e.Property(p => p.Cidade).HasColumnName("Cidade");
        e.Property(p => p.UF).HasColumnName("UF");
    });
```

<br>

`e.WithOwner();` faz com que o Entity Framework não trate o objeto de valor como uma tabela no banco de dados.