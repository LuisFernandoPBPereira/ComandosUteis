<h1 align="center">Conexão com Banco de Dados</h1>

### SqlConnection

```csharp
public class SQLServer
{
    public string ConnectionString { get; set; }
    public SqlConnection Connection { get; set; }

    public SQLServer()
    {
        ConnectionString = "connectionString";
        Connection = new SqlConnection(ConnectionString);
    }
}
```

<br>

### Entity Framework
    
```csharp
public class Context : DbContext
{
    public Context() : base("name=ConnectionString")
    {
    }

    public DbSet<Cliente> Clientes { get; set; }
}
```


