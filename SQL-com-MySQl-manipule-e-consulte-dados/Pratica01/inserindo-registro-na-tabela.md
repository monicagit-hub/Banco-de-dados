# **Inserindo Registros na Tabela**  

## **Estrutura do comando INSERT INTO**  
```sql
INSERT INTO nome_da_tabela (coluna1, coluna2, coluna3, ...)
VALUES (valor1, valor2, valor3, ...);
```  

- **nome_da_tabela:**  Nome da tabela onde os dados serão inseridos.
- **Entre parênteses:**  Lista de colunas onde os dados serão inseridos.
- **VALUES:**  Palavra-chave que indica que estamos adicionando valores.
- **Entre parênteses:**  Os valores correspondentes às colunas especificadas, sempre na mesma ordem.


# Já temos as tabelas **cliente**, **produto** e **vendedores** criadas, agora precisamos inserir informações nelas.  

**Certifique-se de estar no banco de dados correto**

```sql
USE sucos;
```  

## **Comando para Inserção de Dados**  

O comando utilizado para inserir registros em uma tabela é o `INSERT INTO`. Ao abrir parênteses, informamos os campos da tabela nos quais os valores serão inseridos. No caso da tabela **tbproduto**, os campos são:  

- **PRODUTO**  
- **NOME**  
- **EMBALAGEM**  
- **TAMANHO**  
- **SABOR**  
- **PRECO_LISTA**  

A cláusula VALUES que significa que vamos especificar os valores da instrução INSERT INTO.  

```sql
INSERT INTO tbprodutos (
PRODUTO,
NOME,
EMBALAGEM,
TAMANHO,
SABOR,
PRECO_LISTA) VALUES
('1037797',	'VitC', ' 350 ml', ' Lata','Laranja',6.01),
('1000889',	'Uvas bombom', '700 ml', 'Pet','Uva',6.31),
('1004327',	'Arvoredo','1,5 Litros',' Pet','Maça',19.51);
``` 

```sql
INSERT INTO TABELA_DE_VENDEDORES(
MATRICULA,
NOME,
PERCENTUAL_COMISSAO
)VALUES('00233', 'João Geraldo da Fonseca', 0.10);
``` 