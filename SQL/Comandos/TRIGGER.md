<h1 align="center">TRIGGER</h1>

<p>
    <strong>TRIGGER</strong> é um tipo especial de procedimento armazenado que é invocado automaticamente sempre que um evento associado à tabela ocorre.
</p>

<h2>Exemplo</h2>

```sql
CREATE TRIGGER nome-da-trigger
    ON nome-da-tabela
    AFTER INSERT, UPDATE, DELETE
    AS
    BEGIN
        -- Código da trigger a ser executado
    END