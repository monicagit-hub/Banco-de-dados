Agora que temos o **MySQL Workbench** instalado e funcionando, podemos começar a manipular bancos de dados. O primeiro passo é criar um banco de dados, além dos exemplos que já vêm na instalação do MySQL.

Para criar um banco de dados, usamos o comando **`CREATE DATABASE`** ou **`CREATE SCHEMA`**, pois no MySQL ambos são sinônimos. A sintaxe básica é:

```sql
CREATE {DATABASE | SCHEMA} [IF NOT EXISTS] db_name
      [create_specification]

```

O uso do **IF NOT EXISTS** faz com que o banco de dados seja criado apenas se não houver um banco de dados com o mesmo nome já existente.

Dentro de **create_specification**, é possível especificar opções como:

- **CHARACTER SET**: Define o conjunto de caracteres padrão (por exemplo, UTF-8 ou UTF-16).
- **COLLATE**: Define o padrão de comparação de caracteres.
- **ENCRYPTION**: Define se a criptografia será ativada (Y) ou desativada (N).

Se nenhuma dessas opções for especificada, o MySQL usará os valores padrão.

Ao criar um banco de dados no **Workbench**, como no comando `CREATE DATABASE SUCOS;`, o banco de dados será criado e uma mensagem "1 row(s) affected" confirmará a execução bem-sucedida. Para visualizar o banco de dados no **Workbench**, é necessário clicar com o botão direito em **Schemas** e selecionar "Refresh All".

Fisicamente, o banco de dados é armazenado no diretório de dados do MySQL. No Windows, o caminho padrão é **`C:\ProgramData\MySQL\MySQLServer 8.0`**, onde o arquivo **my.ini** contém as variáveis de configuração, incluindo o diretório onde os bancos de dados são armazenados.

No Linux, é possível encontrar o diretório de dados executando o comando `ps -aux | grep mysql` no terminal. Também é possível verificar o caminho do diretório de dados diretamente no **Workbench** com o comando `select @@datadir;`.

Se você acessar o diretório de dados, verá uma pasta com o nome do banco de dados criado, mas inicialmente ela estará vazia. As tabelas serão criadas à medida que você adicionar dados ao banco de dados.
