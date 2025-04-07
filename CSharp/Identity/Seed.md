<h1 align="center">Seed</h1>

Usamos Seed para popular o banco de dados com dados iniciais, como usuários e roles.

### Exemplo

```csharp
public class IdentitySeeder
{
    public static async Task SeedUsersAsync(IServiceProvider serviceProvider)
    {
        var userManager = serviceProvider.GetRequiredService<UserManager<IdentityUser>>();
        var roleManager = serviceProvider.GetRequiredService<RoleManager<IdentityRole>>();
        
        const string userRole = "User";
        if (!await roleManager.RoleExistsAsync(userRole))
        {
            await roleManager.CreateAsync(new IdentityRole(userRole));
        }
        
        await CreateUserAsync(userManager, "alice@smith.com", "Password@123", userRole);
        await CreateUserAsync(userManager, "bob@smith.com", "Password@123", userRole);
    }
    private static async Task CreateUserAsync(UserManager<IdentityUser> userManager, string email, string password, string role)
    {
        
        if (await userManager.FindByEmailAsync(email) != null)
        {
            return;
        }
        var user = new IdentityUser
        {
            UserName = email,
            Email = email,
            EmailConfirmed = true 
        };
        
        var result = await userManager.CreateAsync(user, password);
        if (result.Succeeded)
        {
        
            await userManager.AddToRoleAsync(user, role);
        }
        else
        {
            throw new Exception($"Erro ao criar usuário {email}: {string.Join(", ", result.Errors)}");
        }
    }
}
```

Precisamos adicionar da `Program.cs` os seguintes códigos:

```csharp
builder.Services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
    .AddRoles<IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>();
```

E chamar a função que criamos:

```csharp
using (var scope = app.Services.CreateScope())
{
    var services = scope.ServiceProvider;
    try
    {
        await IdentitySeeder.SeedUsersAsync(services);
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Erro ao executar o Seeder: {ex.Message}");
    }
}
```