# Instalação do MySQL Server e Workbench — Ubuntu 26

> Guia de instalação do MySQL Server 8.4 e MySQL Workbench no Ubuntu 26 (Resolute).

---

## Pré-requisitos

Antes de instalar o MySQL, certifique-se de que o sistema está atualizado:

```bash
sudo apt update
```

---

## 1. MySQL Server

### 1.1 Instalar o MySQL Server

```bash
sudo apt install mysql-server -y
```

> Instala o MySQL Server 8.4 diretamente dos repositórios do Ubuntu. O `-y` confirma automaticamente a instalação sem pedir confirmação.

### 1.2 Iniciar o serviço do MySQL

```bash
sudo systemctl start mysql
```

> Inicia o serviço do MySQL imediatamente.

### 1.3 Habilitar o MySQL na inicialização do sistema

```bash
sudo systemctl enable mysql
```

> Configura o MySQL para iniciar automaticamente sempre que o computador ligar. Não exibe mensagem de retorno quando bem-sucedido.

### 1.4 Configuração de segurança

```bash
sudo mysql_secure_installation
```

> Executa um script de segurança interativo. Responda às perguntas da seguinte forma:

| Pergunta | Resposta | Motivo |
|---|---|---|
| Setup VALIDATE PASSWORD component? | **N** | Em desenvolvimento, complica mais do que ajuda |
| Remove anonymous users? | **Y** | Remove acessos desnecessários |
| Disallow root login remotely? | **Y** | Segurança: root só via localhost |
| Remove test database? | **Y** | Remove banco de teste desnecessário |
| Reload privilege tables now? | **Y** | Aplica todas as mudanças |

### 1.5 Acessar o MySQL

```bash
sudo mysql -u root -p
```

> Abre o terminal do MySQL como usuário root. Na primeira vez, basta pressionar Enter quando pedir senha (ela ainda está em branco).

### 1.6 Definir senha do root (necessário para o Workbench)

Dentro do terminal do MySQL, execute:

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'sua_senha';
FLUSH PRIVILEGES;
EXIT;
```

> `ALTER USER` define a senha e o método de autenticação do root. No MySQL 8.4, o método correto é `caching_sha2_password` — o `mysql_native_password` foi removido nessa versão.
> `FLUSH PRIVILEGES` recarrega as permissões para que a mudança entre em vigor.
> `EXIT` sai do terminal do MySQL.

⚠️ **Importante:** Guarde essa senha — ela será usada para conectar no MySQL Workbench.

---

## 2. MySQL Workbench

### 2.1 Instalar via Snap

```bash
sudo snap install mysql-workbench-community
```

> Instala o MySQL Workbench (interface gráfica do MySQL) via Snap. É a forma mais simples no Ubuntu 26.

### 2.2 Conectar ao banco de dados

1. Abra o MySQL Workbench
2. Clique em **Local instance 3306**
3. Digite a senha definida no passo 1.6
4. Se aparecer um aviso de versão incompatível, clique em **Continue Anyway** e marque **"Don't show this message again"**

> O aviso aparece porque o Workbench 8.0 foi testado até o MySQL 8.0, mas o Ubuntu 26 traz o MySQL 8.4. Ele funciona normalmente para uso do dia a dia.

---

## Manutenção

### Verificar status do MySQL

```bash
sudo systemctl status mysql   # Ver se está rodando
sudo systemctl stop mysql     # Parar o serviço
sudo systemctl start mysql    # Iniciar o serviço
sudo systemctl restart mysql  # Reiniciar o serviço
```

### Acessar o MySQL pelo terminal

```bash
sudo mysql -u root -p
```

> Digite a senha quando solicitado.
