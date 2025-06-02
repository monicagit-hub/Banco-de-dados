
# 🗃️ Inserindo varios registros nas tabelas – `tbcliente` e `tbproduto`

## 📁 Selecionando o Banco de Dados

Antes de iniciar, selecione o banco de dados:

```sql
USE sucos;
```

---

## 🧹 Removendo Tabelas Existentes

Garanta que as tabelas sejam recriadas do zero:

```sql
DROP TABLE tbcliente;
DROP TABLE tbproduto;
```

---

## 🏗️ Criando as Tabelas

### 🔸 Tabela `tbcliente`

```sql
CREATE TABLE tbcliente (
  CPF VARCHAR(11),
  NOME VARCHAR(100),
  ENDERECO1 VARCHAR(150),
  ENDERECO2 VARCHAR(150),
  BAIRRO VARCHAR(50),
  CIDADE VARCHAR(50),
  ESTADO VARCHAR(2),
  CEP VARCHAR(8),
  DATA_NASCIMENTO DATE,
  IDADE SMALLINT,
  SEXO VARCHAR(1),
  LIMITE_CREDITO FLOAT,
  VOLUME_COMPRA FLOAT,
  PRIMEIRA_COMPRA BIT
);

ALTER TABLE tbcliente ADD PRIMARY KEY (CPF);
```

### 🔸 Tabela `tbproduto`

```sql
CREATE TABLE tbproduto (
  PRODUTO VARCHAR(20),
  NOME VARCHAR(150),
  EMBALAGEM VARCHAR(50),
  TAMANHO VARCHAR(50),
  SABOR VARCHAR(50),
  PRECO_LISTA FLOAT
);

ALTER TABLE tbproduto ADD PRIMARY KEY (PRODUTO);
```

---

## 📥 Inserindo Dados Fictícios

### 🧑‍💼 Tabela `tbcliente`

```sql
INSERT INTO tbcliente VALUES 
('19290992743','Fernando Cavalcante','R. Dois de Fevereiro','','Água Santa','Rio de Janeiro','RJ','22000000','2000-02-12',24,'M',100000,200000,1),
('31482935700','Mariana Soares','Av. Brasil','Bloco A','Centro','São Paulo','SP','01000000','1992-07-23',32,'F',50000,120000,1),
('59821436012','João Almeida','Rua das Palmeiras','','Jardim América','Belo Horizonte','MG','30100000','1988-11-05',36,'M',30000,75000,0),
('84729365001','Camila Dias','Rua do Comércio','Ap. 202','Centro','Curitiba','PR','80000000','1995-03-14',30,'F',45000,82000,1),
('10598247623','Roberto Nunes','Av. Atlântica','','Copacabana','Rio de Janeiro','RJ','22000001','1970-09-30',53,'M',150000,210000,0),
('90718356078','Aline Ferreira','Rua Pedro Álvares','Casa 3','Vila Nova','Salvador','BA','40000000','2001-01-10',23,'F',25000,60000,1),
('29563781922','Carlos Henrique','Av. Independência','','Centro','Fortaleza','CE','60000000','1999-06-08',25,'M',40000,91000,1),
('18372649017','Juliana Ribeiro','Rua XV de Novembro','Ap. 105','Zona Sul','Porto Alegre','RS','90000000','1985-04-19',39,'F',60000,130000,0),
('67482910345','Eduardo Pires','Rua Santa Clara','Casa 1','Tijuca','Rio de Janeiro','RJ','20500000','1993-10-01',31,'M',20000,45000,1),
('90817264533','Patrícia Lima','Rua Amapá','Bloco C','Industrial','Contagem','MG','32000000','1990-12-15',34,'F',35000,72000,0);
```

### 📦 Tabela `tbproduto`

```sql
INSERT INTO tbproduto VALUES
('1040107','Light - 350 ml - Melância','Lata','350 ml','Melância',4.55),
('2040150','Sabor da Serra - 500 ml - Uva','Pet','500 ml','Uva',3.99),
('3040201','Tropical - 2L - Abacaxi','Pet','2 L','Abacaxi',6.75),
('4040302','Refrescante - 600 ml - Limão','Garrafa','600 ml','Limão',4.25),
('5040403','Delícia - 1L - Manga','Caixa','1 L','Manga',5.80),
('6040504','Mais Sabor - 350 ml - Laranja','Lata','350 ml','Laranja',4.10),
('7040605','Verão - 1.5L - Pêssego','Pet','1.5 L','Pêssego',5.60),
('8040706','Energy - 250 ml - Frutas Vermelhas','Lata','250 ml','Frutas Vermelhas',6.20),
('9040807','Suco Verde - 300 ml - Couve e Limão','Garrafa','300 ml','Couve e Limão',4.90),
('10050908','Zero Açúcar - 600 ml - Guaraná','Pet','600 ml','Guaraná',4.35);
```

---

## 🔍 Consultas SQL Básicas 

### 1️⃣ Selecionar todos os registros da tabela `tbcliente`

```sql
SELECT * FROM tbcliente;
```

### 2️⃣ Exibir apenas CPF e NOME dos clientes

```sql
SELECT CPF, NOME FROM tbcliente;
```


### 3️⃣ Limitar a 5 registros

```sql
SELECT CPF, NOME FROM tbcliente LIMIT 5;
```

### 4️⃣ Renomear colunas na exibição (`AS`)

```sql
SELECT CPF AS CPF_CLIENTE, NOME AS NOME_CLIENTE FROM tbcliente;
```

### 5️⃣ Selecionar dados específicos para análise

```sql
SELECT NOME, CPF, SEXO, IDADE, DATA_NASCIMENTO FROM tbcliente;
```

---------------------------------------------------------------------------------------------
<br>
<br>


### 1️⃣ Selecionar todos os registros da tabela `tbproduto`

```sql
SELECT * FROM tbproduto;
```

---

### 2️⃣ Exibir apenas o código do produto e o nome

```sql
SELECT PRODUTO, NOME FROM tbproduto;
```

---

### 3️⃣ Limitar a 5 registros

```sql
SELECT PRODUTO, NOME FROM tbproduto LIMIT 5;
```

---

### 4️⃣ Renomear colunas na exibição com `AS`

```sql
SELECT PRODUTO AS CODIGO_PRODUTO, NOME AS NOME_PRODUTO FROM tbproduto;
```

---

### 5️⃣ Selecionar dados específicos para análise

```sql
SELECT NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA FROM tbproduto;
```
