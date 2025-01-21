
Use o comando DROP DATABASE para excluir um banco de dados:

```sql
DROP {DATABASE | SCHEMA} [IF EXISTS] db_name

```
A cláusula [IF EXISTS] evita erros caso o banco de dados não exista.

No campo de consulta, digite e execute o comando:
```sql
DROP DATABASE SUCOS;

```
<br>

No MySQL, SCHEMA é sinônimo de DATABASE. Ou seja, usar DROP SCHEMA ou DROP DATABASE é equivalente. Ambos se referem ao conjunto de tabelas, visões, procedimentos e outros objetos dentro de um banco de dados específico. Por exemplo:

```sql
DROP SCHEMA IF EXISTS clientes_db;

```
Faz exatamente o mesmo que:

```sql
DROP DATABASE IF EXISTS clientes_db;

```