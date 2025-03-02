**Informações da Tabela:**<br>
A empresa deseja armazenar dados como CPF, nome, endereço, data de nascimento, idade, sexo, limite de crédito, volume mínimo de compras e se o cliente já realizou a primeira compra.
Cada informação corresponde a uma coluna, sendo necessário definir os tipos de dados apropriados para cada campo.

Banco de dados utilizado:`SUCOS;`

Selecionar o banco com o comando `USE` antes de criar as tabelas:

```sql
use sucos;
```
<br>

**Criação da tabela cliente:**<br>

```sql
CREATE TABLE tbcliente
( CPF VARCHAR (11) ,
NOME VARCHAR (100) ,
ENDERECO1 VARCHAR (150) ,
ENDERECO2 VARCHAR (150) ,
BAIRRO VARCHAR (50) ,
CIDADE VARCHAR (50) ,
ESTADO VARCHAR (2) ,
CEP VARCHAR (8) ,
IDADE SMALLINT,
SEXO VARCHAR (1) ,
LIMITE_CREDITO FLOAT ,
VOLUME_COMPRA FLOAT ,
PRIMEIRA_COMPRA BIT (1));
```
CPF: VARCHAR(11) – Para evitar truncar zeros iniciais.<br>
NOME: VARCHAR(100) – Suporta nomes longos.<br>
ENDEREÇO: Dividido em ENDERECO1 e ENDERECO2, ambos VARCHAR(150) – Para endereços extensos.<br>
BAIRRO e CIDADE: VARCHAR(50) – Armazenam bairro e cidade, com limite suficiente.<br>
ESTADO: VARCHAR(2) – Sigla de dois caracteres, como "SP".<br>
CEP: VARCHAR(8) – Para o Código de Endereçamento Postal.<br>
IDADE: SMALLINT – Para idades de até 150 anos.<br>
SEXO: VARCHAR(1) – Armazena "M" ou "F".<br>
LIMITE_CREDITO e VOLUME_COMPRA: FLOAT – Para valores decimais (crédito em dinheiro e volume em litros).<br>
PRIMEIRA_COMPRA: BIT(1) – Indica se já realizou a primeira compra (1 para sim, 0 para não).<br>

**Desafio:** Nosso sistema de vendas tem mais uma tabela a ser criada: vendedores.<br>
Algumas informações:<br>
Nome da tabela deve ser TABELA_DE_VENDEDORES Vendedor tem o número interno da matrícula, onde será armazenado no campo MATRICULA, que deve ser um string de 5 posições. O nome do vendedor deverá ser armazenado no campo NOME, e deve ser um string de 100 posições. Criar o campo PERCENTUAL_COMISSAO que representa quantos % de comissão o vendedor ganha sobre cada venda.
<br>

**Criação da Tabela de Vendedores:**<br>

```sql
CREATE TABLE TABELA_DE_VENDEDORES(
MATRICULA VARCHAR(5),
NOME VARCHAR(100),
PERCENTUAL_COMISSAO FLOAT
);

```
MATRICULA: VARCHAR(5) – Identificador do vendedor, limitado a 5 caracteres.<br>
NOME: VARCHAR(100) – Nome completo do vendedor, permitindo nomes longos.<br>
PERCENTUAL_COMISSAO: FLOAT – Percentual de comissão, armazenado como valor decimal.<br>
<br>

**Criação da Tabela de produtos:**<br>

```sql
CREATE TABLE tbprodutos (
  produto VARCHAR(20) NULL,
  nome VARCHAR(150) NULL,
  embalagem VARCHAR(50) NULL,
  sabor VARCHAR(50) NULL,
  tamanho VARCHAR(50) NULL,
  preco_lista FLOAT NULL
);
```

PRODUTO: VARCHAR(20) – Código ou identificador do produto.<br>
NOME: VARCHAR(150) – Nome completo do produto.<br>
EMBALAGEM: VARCHAR(50) – Tipo de embalagem, como "Caixa" ou "Garrafa".<br>
SABOR: VARCHAR(50) – Tipo de sabor, como "uva" ou "Melância".<br>
TAMANHO: VARCHAR(50) – Volume ou tamanho do produto, como "1L" ou "500ml".<br>
PRECO_LISTA: FLOAT – Preço oficial do produto, usado para cálculos.<br>

Todos os campos permitem valores nulos (NULL), ou seja, podem ficar vazios, o que indica que a informação não é obrigatória.