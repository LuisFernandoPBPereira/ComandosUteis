<h1 align="center">Mapear Enum para String</h1>

```csharp
modelBuilder.Entity<Endereco>()
    .Property(c => c.Estado)
    .HasConversion<string>();
```