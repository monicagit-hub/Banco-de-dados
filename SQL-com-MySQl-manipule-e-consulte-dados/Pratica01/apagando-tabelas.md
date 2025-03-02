# Exclusão de Tabelas no SQL  

Antes de excluir uma tabela, é importante verificar se ela possui relações com outras tabelas no banco de dados. Caso existam dependências, a remoção pode não ser permitida. No exemplo a seguir, trabalhamos com duas tabelas que não possuem relacionamentos, permitindo a exclusão sem problemas.  

No entanto, como utilizaremos as tabelas **clientes** e **produtos** nas próximas aulas, não as excluiremos diretamente. Em vez disso, modificaremos o nome da tabela de clientes no script, adicionando o sufixo `"2"`, e executaremos os comandos para testar a exclusão.  

## Certifique-se de que o banco de dados sucos está selecionado. Se necessário, execute:
```sql
USE sucos;
```

## Criando tabela para teste:

Crie a tabela **tbcliente2** executando o seguinte comando SQL:  

```sql
CREATE TABLE tbcliente2 (
    CPF VARCHAR(11),
    NOME VARCHAR(100),
    ENDERECO1 VARCHAR(150),
    ENDERECO2 VARCHAR(150),
    BAIRRO VARCHAR(50),
    CIDADE VARCHAR(50),
    ESTADO VARCHAR(2),
    CEP VARCHAR(8),
    IDADE SMALLINT,
    SEXO VARCHAR(1),
    LIMITE_CREDITO FLOAT,
    VOLUME_COMPRA FLOAT,
    PRIMEIRA_COMPRA BIT(1)
);
```
## Para excluir a tabela tbcliente2, execute o seguinte comando:

```sql
DROP TABLE tbcliente2;
```