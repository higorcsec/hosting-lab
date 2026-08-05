# Bancos de Dados

Um **banco de dados (Database)** é um sistema responsável por armazenar, organizar e recuperar informações de forma eficiente.

Praticamente toda aplicação moderna utiliza um banco de dados, seja um site institucional, um e-commerce, uma API, um sistema ERP ou um aplicativo mobile.

Exemplos de informações armazenadas:

- Usuários
- Produtos
- Pedidos
- Clientes
- Mensagens
- Arquivos
- Configurações
- Logs

Sem um banco de dados, essas informações precisariam ser armazenadas em arquivos, tornando o gerenciamento muito mais complexo.

---

# Como funciona?

Uma aplicação envia consultas ao banco de dados.

O banco processa essas consultas e retorna as informações solicitadas.

Exemplo:

```text
Usuário
    │
    ▼
Site / API
    │
    ▼
Banco de Dados
    │
    ▼
Resposta
```

Sempre que um usuário faz login, cadastra um produto ou publica um comentário, normalmente existe uma operação sendo realizada no banco de dados.

---

# Bancos de Dados Relacionais

Os bancos relacionais armazenam informações em tabelas.

Cada tabela possui:

- Colunas
- Linhas
- Relacionamentos

Exemplo:

## Tabela Clientes

| ID | Nome | Cidade |
|----|-------|---------|
|1|João|São Paulo|
|2|Maria|Curitiba|

## Tabela Pedidos

| Pedido | Cliente |
|---------|----------|
|1001|João|
|1002|Maria|

Os relacionamentos permitem conectar informações entre diferentes tabelas.

---

# SQL

A maioria dos bancos relacionais utiliza a linguagem **SQL (Structured Query Language)**.

Ela é utilizada para:

- Criar tabelas;
- Inserir dados;
- Alterar registros;
- Excluir informações;
- Consultar dados.

Exemplo:

```sql
SELECT * FROM clientes;
```

---

# Principais Bancos Relacionais

## MySQL

O MySQL é um dos bancos de dados mais utilizados no mundo.

É muito comum em:

- WordPress
- Joomla
- Drupal
- Laravel
- PHP puro
- Hospedagens compartilhadas

Vantagens:

- Fácil administração;
- Grande comunidade;
- Excelente integração com PHP;
- Disponível na maioria das hospedagens.

---

## MariaDB

O MariaDB surgiu como um fork do MySQL.

Na prática, é compatível com a maioria das aplicações que utilizam MySQL.

É bastante utilizado por:

- Provedores de hospedagem;
- Servidores Linux;
- Distribuições modernas.

Muitas hospedagens atualmente utilizam MariaDB como substituto do MySQL.

---

## PostgreSQL

O PostgreSQL é conhecido por oferecer recursos avançados e maior conformidade com os padrões SQL.

É muito utilizado em:

- Sistemas corporativos;
- APIs;
- Sistemas financeiros;
- Aplicações com grande volume de dados;
- Business Intelligence (BI).

Linguagens frequentemente utilizadas:

- Python (Django)
- Java
- C#
- Go
- Node.js

---

## Microsoft SQL Server

Desenvolvido pela Microsoft.

Muito comum em empresas que utilizam tecnologias Microsoft.

Utilizado em:

- Sistemas ERP
- Aplicações .NET
- Sistemas corporativos
- Power BI

Integra-se muito bem com:

- C#
- ASP.NET
- VB.NET

---

## Oracle Database

Banco de dados corporativo bastante utilizado em grandes empresas.

É comum encontrar Oracle em:

- Bancos
- Seguradoras
- Governo
- Grandes empresas

Seu foco é alta disponibilidade, segurança e processamento de grandes volumes de dados.

---

# Bancos Não Relacionais (NoSQL)

Os bancos NoSQL não armazenam dados necessariamente em tabelas.

Eles podem utilizar:

- Documentos
- Chave-valor
- Grafos
- Colunas

São muito utilizados em aplicações modernas que precisam de alta escalabilidade.

---

## MongoDB

O MongoDB armazena informações em documentos JSON.

Exemplo:

```json
{
    "nome": "João",
    "idade": 28,
    "cidade": "São Paulo"
}
```

É muito utilizado em:

- Node.js
- APIs REST
- Aplicações Web
- Sistemas em tempo real

---

## Redis

O Redis funciona principalmente como um banco de dados em memória.

É extremamente rápido.

Muito utilizado para:

- Cache
- Sessões
- Filas
- Rate Limit
- Armazenamento temporário

Diversas aplicações utilizam Redis junto com MySQL ou PostgreSQL para melhorar o desempenho.

---

# Banco de Dados x Linguagem

É importante entender que o banco de dados não depende de apenas uma linguagem de programação.

Diversas linguagens podem acessar o mesmo banco utilizando drivers específicos.

| Linguagem | Bancos mais utilizados |
|------------|------------------------|
| PHP | MySQL, MariaDB |
| Python | PostgreSQL, MySQL, SQLite |
| Java | PostgreSQL, Oracle, SQL Server |
| C# (.NET) | SQL Server, PostgreSQL |
| Node.js | MongoDB, PostgreSQL, MySQL |
| Go | PostgreSQL, MySQL |
| Laravel (PHP) | MySQL, MariaDB, PostgreSQL |
| Django (Python) | PostgreSQL, MySQL, SQLite |

A escolha normalmente depende da aplicação e da necessidade do projeto.

---

# Banco de Dados em Hospedagem Compartilhada

Em hospedagens compartilhadas, normalmente estão disponíveis:

- MySQL
- MariaDB

O gerenciamento costuma ser realizado pelo painel da hospedagem.

Ferramentas comuns:

- phpMyAdmin
- Adminer (alguns provedores)

O usuário normalmente não possui acesso às configurações do servidor de banco de dados.

---

# Banco de Dados em VPS

Em uma VPS o administrador possui controle total.

É possível instalar diversos bancos, como:

- MySQL
- MariaDB
- PostgreSQL
- MongoDB
- Redis

Também é possível configurar:

- Backups automáticos;
- Usuários;
- Permissões;
- Replicação;
- Monitoramento;
- Otimizações de desempenho.

---

# Qual banco escolher?

| Situação | Banco recomendado |
|----------|-------------------|
| WordPress | MySQL ou MariaDB |
| Site PHP | MySQL ou MariaDB |
| Laravel | MySQL, MariaDB ou PostgreSQL |
| Django | PostgreSQL |
| API Node.js | PostgreSQL ou MongoDB |
| Sistema Corporativo | PostgreSQL ou SQL Server |
| ERP Empresarial | PostgreSQL, Oracle ou SQL Server |
| Cache | Redis |

---

# Boas práticas

- Faça backups regularmente.
- Utilize usuários com permissões limitadas.
- Nunca utilize o usuário root na aplicação.
- Monitore o espaço em disco.
- Mantenha o banco atualizado.
- Utilize índices para melhorar consultas.
- Proteja o acesso ao banco com senhas fortes.

---

# Resumo

Os bancos de dados são responsáveis por armazenar e organizar as informações utilizadas pelas aplicações. Os bancos relacionais, como MySQL, MariaDB e PostgreSQL, são amplamente utilizados em sites e sistemas corporativos, enquanto soluções NoSQL, como MongoDB e Redis, atendem cenários específicos de escalabilidade e desempenho. A escolha do banco depende da linguagem utilizada, do tipo de aplicação e das necessidades do projeto. Em hospedagens compartilhadas, normalmente estão disponíveis MySQL e MariaDB, enquanto uma VPS oferece liberdade para instalar e configurar diferentes bancos de dados conforme a necessidade.
