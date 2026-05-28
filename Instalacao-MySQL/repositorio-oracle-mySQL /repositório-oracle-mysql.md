# Instalação MySQL Ubuntu via Terminal

> Guia de instalação do MySQL Server e MySQL Workbench no Ubuntu via repositório oficial da Oracle/MySQL.

---

## MySQL Server

### 1.1 Baixar o pacote de configuração do repositório oficial

Acesse o site oficial e baixe o pacote mais recente:
[https://dev.mysql.com/downloads/repo/apt/](https://dev.mysql.com/downloads/repo/apt/)

Ou baixe diretamente pelo terminal:

```bash
wget -c https://repo.mysql.com//mysql-apt-config_0.8.22-1_all.deb
```

> O `wget` baixa arquivos da internet via terminal. O `-c` permite retomar o download caso seja interrompido.
> **Atenção:** Este pacote não é o MySQL em si — ele apenas configura o repositório oficial da Oracle no Ubuntu para que o apt saiba onde buscar o MySQL.

### 1.2 Instalar o pacote do repositório

```bash
sudo dpkg -i mysql-apt-config_0.8.22-1_all.deb
```

> O `dpkg -i` instala um pacote `.deb` local. Ao rodar esse comando, uma tela roxa de configuração será aberta perguntando qual produto MySQL deseja configurar.

**Na tela de configuração:**
- O sistema já vem com **MySQL Server & Cluster** selecionado por padrão
- Use a tecla **seta para baixo** até chegar em **OK**
- Pressione **Tab** para ir até o botão **Ok** e pressione **Enter**

### 1.3 Atualizar a lista de pacotes

```bash
sudo apt update
```

> Após configurar o repositório, é necessário atualizar a lista de pacotes para que o apt reconheça os pacotes do MySQL disponíveis no novo repositório.

### 1.4 Instalar o MySQL Server

```bash
sudo apt install mysql-server
```

Pressione **Enter** para confirmar e depois **S** para aceitar.

> Instala o MySQL Server a partir do repositório oficial da Oracle. Durante a instalação, uma tela será aberta pedindo a senha do root do MySQL.

**Na tela de senha:**
- Pressione **Tab** → **Enter** para ir ao campo de senha
- Digite sua senha
- Confirme a senha novamente
- Será perguntado sobre o método de autenticação — selecione **Use Strong Password Encryption (RECOMMENDED)**
- Pressione **Tab** → **Ok** → **Enter**

⚠️ **Importante:** A senha do root do MySQL é diferente da senha do seu usuário Linux. Anote-a em local seguro.

### 1.5 Configuração de segurança

```bash
sudo mysql_secure_installation
```

> Executa um script de segurança interativo. Informe a senha criada na instalação quando solicitado.

Responda às perguntas da seguinte forma:

| Pergunta | Resposta | Motivo |
|---|---|---|
| Continuar com a senha atual? | **Y** | Confirma a senha criada |
| Remove anonymous users? | **Y** | Remove acessos desnecessários |
| Disallow root login remotely? | **Y** | Segurança: root só via localhost |
| Remove test database? | **Y** | Remove banco de teste desnecessário |
| Reload privilege tables now? | **Y** | Aplica todas as mudanças |

Ao final, aparecerá a mensagem **All done!** indicando sucesso.

> **Obs:** A senha não aparece enquanto você digita — isso é normal e esperado.

### 1.6 Verificar o status do serviço

```bash
sudo systemctl status mysql
```

> Verifica se o MySQL está rodando. Deve aparecer **active (running)** em verde.

Se estiver fora do ar:

```bash
sudo systemctl start mysql
```

Se ainda não funcionar, tente:

```bash
sudo apt-get update
sudo apt-get upgrade
```

Reinicie o computador e rode novamente:

```bash
sudo systemctl status mysql
```

### 1.7 Habilitar o MySQL na inicialização do sistema

```bash
sudo systemctl enable mysql
```

> Configura o MySQL para iniciar automaticamente sempre que o computador ligar. Não exibe mensagem quando bem-sucedido.

---

## MySQL Workbench

### 2.1 Atualizar o sistema

```bash
sudo apt update && sudo apt dist-upgrade -y
```

> Atualiza a lista de pacotes e aplica todas as atualizações disponíveis antes de instalar o Workbench.

### 2.2 Baixar o pacote do Workbench

Acesse o site oficial e baixe a versão `.deb` compatível com seu Ubuntu:
[https://dev.mysql.com/downloads/workbench/](https://dev.mysql.com/downloads/workbench/)

Ou baixe diretamente pelo terminal (ajuste o nome do arquivo conforme a versão disponível):

```bash
wget http://cdn.mysql.com/Downloads/MySQLGUITools/mysql-workbench-community_8.0.29-1ubuntu20.04_amd64.deb -O mysql-workbench-community.deb
```

> Baixa o pacote `.deb` do Workbench e salva com o nome `mysql-workbench-community.deb`. Ajuste o link conforme a versão mais recente disponível no site.

### 2.3 Instalar o Workbench

```bash
sudo dpkg -i mysql-workbench-community.deb
```

> Instala o pacote `.deb` do Workbench. Se aparecer algum erro de dependências, rode `sudo apt install -f` para corrigir automaticamente.

### 2.4 Conectar ao banco de dados

1. Abra o MySQL Workbench
2. Clique em **Local instance**
3. Digite a senha do root do MySQL criada durante a instalação
4. Clique em **OK**

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

> Abre o terminal interativo do MySQL como usuário root. Digite a senha quando solicitado.
