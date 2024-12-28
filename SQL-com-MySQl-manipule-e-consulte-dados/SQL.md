## Conceitos Fundamentais de Bancos de Dados

### Banco de Dados
* **Definição:** Um repositório organizado de dados, armazenado eletronicamente e acessível por meio de um sistema de gerenciamento de banco de dados (SGBD).
* **Objetivo:** Armazenar, gerenciar e recuperar dados de forma eficiente.

### Entidades
* **Tabelas:**
    * Estruturas bidimensionais compostas por linhas (registros) e colunas (campos).
    * **Campos:** Representam atributos de um registro (ex: nome, idade, CPF).
    * **Chave primária:** Identifica de forma única cada registro.
    * **Chave estrangeira:** Estabelece relacionamentos entre tabelas.
    * **Índices:** Aceleram a busca por dados.
* **Esquemas:** Coleções de tabelas relacionadas logicamente.
* **Views:** Tabelas virtuais derivadas de outras tabelas.
* **Procedures:** Blocos de código pré-compilados que executam várias instruções SQL.
* **Funções:** Blocos de código que retornam um único valor.
* **Triggers:** Eventos que disparam ações automaticamente.

### Conceitos Adicionais
* **Integridade de dados:** Garantia da consistência e precisão dos dados.
* **Relacional:** Modelo de banco de dados que estabelece relacionamentos entre tabelas.
* **Performance:** Velocidade das operações no banco de dados.
* **ANSI:** Padrão para a linguagem SQL.

### Resumo em Tabela
| Termo | Definição |
|---|---|
| Banco de dados | Repositório organizado de dados |
| Tabela | Estrutura bidimensional para armazenar dados |
| Campo | Coluna de uma tabela |
| Chave primária | Identificador único de um registro |
| Chave estrangeira | Relacionamento entre tabelas |
| Índice | Estrutura para acelerar a busca por dados |
| Esquema | Coleção de tabelas relacionadas |
| View | Tabela virtual derivada de outras tabelas |
| Procedure | Bloco de código pré-compilado |
| Função | Bloco de código que retorna um valor |
| Trigger | Evento que dispara uma ação automaticamente |


## Exemplos Práticos de Entidades em um Banco de Dados de Livraria

### Introdução
Vamos construir um banco de dados simples para uma livraria, utilizando os conceitos de tabelas, esquemas, views, procedures, funções e triggers.

### Tabelas
* **Livros:** Armazena informações sobre os livros, como título, autor, editora e ano de publicação.
    | ID_Livro | Título | Autor | Editora | Ano_Publicação | ISBN |
    |---|---|---|---|---|---|
    | 1 | Dom Quixote | Miguel de Cervantes | Planeta | 1605 | 978-85-7665-023-1 |
    | 2 | 1984 | George Orwell | Editora Globo | 1949 | 978-85-250-4531-8 |

* **Autores:** Contém informações sobre os autores dos livros.
    | ID_Autor | Nome | Nacionalidade |
    |---|---|---|
    | 1 | Miguel de Cervantes | Espanhol |
    | 2 | George Orwell | Inglês |

* **Editoras:** Armazena informações sobre as editoras dos livros.
    | ID_Editora | Nome | País |
    |---|---|---|
    | 1 | Planeta | Brasil |
    | 2 | Editora Globo | Brasil |

* **Empréstimos:** Registra os empréstimos de livros por usuários.
    | ID_Empréstimo | ID_Livro | ID_Usuario | Data_Empréstimo | Data_Devolução |
    |---|---|---|---|---|
    | 1 | 1 | 123 | 2023-11-20 | 2023-11-27 |

### Relacionamentos
* **Um para muitos:** Um autor pode escrever vários livros, mas um livro tem apenas um autor (chave estrangeira ID_Autor na tabela Livros).
* **Um para muitos:** Uma editora pode publicar vários livros, mas um livro é publicado por apenas uma editora (chave estrangeira ID_Editora na tabela Livros).
* **Um para muitos:** Um usuário pode emprestar vários livros, mas um livro pode ser emprestado por apenas um usuário a cada momento (chave estrangeira ID_Livro na tabela Empréstimos).

### Esquema
O esquema "Livraria" agrupa as tabelas "Livros", "Autores", "Editoras" e "Empréstimos".<br>
O esquema "Livraria" engloba todas as tabelas e relações definidas para representar uma livraria. É como um mapa que mostra como os dados estão organizados no banco de dados.

### Views
* **LivrosDisponiveis:** Mostra os livros que estão disponíveis para empréstimo.
    ```sql
    CREATE VIEW LivrosDisponiveis AS
    SELECT * FROM Livros
    WHERE ID_Livro NOT IN (SELECT ID_Livro FROM Empréstimos WHERE Data_Devolução IS NULL);
    ```

### Procedures
* **InserirLivro:** Insere um novo livro no banco de dados.
    ```sql
    CREATE PROCEDURE InserirLivro
    -- ...
    ```

### Funções
* **CalcularIdadeLivro:** Calcula a idade de um livro em anos.
    ```sql
    CREATE FUNCTION CalcularIdadeLivro (@Ano_Publicação INT)
    -- ...
    ```

### Triggers
* **AtualizarDisponibilidade:** Atualiza o status de um livro para "Indisponível" ao ser emprestado.
    ```sql
    CREATE TRIGGER tr_AtualizarDisponibilidade
    ON Empréstimos
    AFTER INSERT
    -- ...
    ```

