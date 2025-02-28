<h1 align="center">Begin Transaction</h1>

```csharp
using (var transaction = contexto.Database.BeginTransaction())
{
    /* 
        Operações de banco de dados aqui
    */
    
    try
    {
        transaction.Commit();
    }
    catch (Exception)
    {
        transaction.Rollback();
    }
}
```