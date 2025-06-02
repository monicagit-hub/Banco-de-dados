
# 🎯 Filtrando Registros com SQL – Cláusula `WHERE`

Vamos aprender a **filtrar registros** para visualizar apenas as informações desejadas. Até o momento, utilizamos o comando `LIMIT` para limitar o número de registros exibidos. Agora, exploraremos a cláusula `WHERE` para refinar as consultas.

---

## 📋 Visualizando todos os dados

Antes de aplicar filtros, podemos verificar o conteúdo das tabelas com:

```sql
SELECT * FROM tbproduto;
SELECT * FROM tbcliente;
```

---

## 🔎 Usando `WHERE` para buscar registros específicos

A cláusula `WHERE` permite filtrar os dados com base em condições específicas. Por exemplo:

```sql
SELECT * FROM tbproduto WHERE PRODUTO = '6040504';
```

**Retorno:**

| PRODUTO | NOME                                | EMBALAGEM | TAMANHO | SABOR | PRECO_LISTA |
|---------|-------------------------------------|-----------|---------|--------|--------------|
| 6040504  | Mais Sabor - 350 ml - Laranja  | Lata      | 350 ml  | Laranja | 4.1       |



📌 Neste exemplo, estamos filtrando um único produto pelo seu código (chave primária).

---

## 🏙️ Filtrando por campos que não são chave primária

É possível utilizar qualquer campo da tabela como critério, por exemplo:

```sql
SELECT * FROM tbcliente WHERE CIDADE = 'Rio de Janeiro';
```

🔍 Esta consulta retorna todos os clientes que residem no Rio de Janeiro.

> ⚠️ A cláusula `WHERE` pode retornar **mais de um registro** e é válida para os comandos `SELECT`, `UPDATE` e `DELETE`.

---

## 🍋 Buscando por sabor

```sql
SELECT * FROM tbproduto WHERE SABOR = 'Limão';
```

🎯 Esta consulta retorna **todos os produtos** com o sabor Limão.

---

## 📝 Atualizando os sabores com `UPDATE`

Suponha que agora o sabor "Limão" será chamado de **"Cítricos"**. Podemos fazer isso com:

```sql
UPDATE tbproduto
SET SABOR = 'Cítricos'
WHERE SABOR = 'Limão';
```

🔄 Esse comando modifica todos os produtos com sabor "Limão" para "Cítricos".

---

## ✅ Verificando o resultado após o `UPDATE`

```sql
SELECT * FROM tbproduto WHERE SABOR = 'Cítricos';
```

📌 Agora os registros antes com "Limão" aparecerão como "Cítricos".

---


## 🧠 Conclusão

- A cláusula `WHERE` permite aplicar **condições simples ou compostas** para retornar registros específicos.
- Pode ser usada com qualquer campo da tabela, mesmo que não seja uma chave primária.
- Também é aplicável a comandos como `UPDATE` e `DELETE`.

