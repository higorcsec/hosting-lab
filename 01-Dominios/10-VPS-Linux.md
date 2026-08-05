# VPS Linux

Uma **VPS (Virtual Private Server)** é um servidor virtual criado dentro de um servidor físico. Cada VPS possui seu próprio sistema operacional, recursos dedicados (CPU, memória e armazenamento) e acesso administrativo, funcionando de forma semelhante a um servidor físico.

Ela é muito utilizada para hospedar sites, APIs, bancos de dados, aplicações web, servidores de jogos e diversos outros serviços.

---

# Como funciona uma VPS?

Um servidor físico pode ser dividido em várias máquinas virtuais através de um **hipervisor**, permitindo que cada cliente tenha seu próprio ambiente isolado.

Exemplo:

```text
                Servidor Físico
        ┌─────────────────────────────┐
        │ CPU • RAM • SSD • Rede      │
        └─────────────┬───────────────┘
                      │
               Hipervisor (Virtualização)
        ┌─────────────┼───────────────┐
        │             │               │
     VPS 1         VPS 2          VPS 3
   Ubuntu         Debian         CentOS
   Site A         API B          Banco C
```

Cada VPS possui:

- Sistema operacional próprio;
- Endereço IP;
- Recursos dedicados;
- Usuários independentes;
- Serviços próprios.

---

# VPS x Hospedagem Compartilhada

| Hospedagem Compartilhada | VPS |
|--------------------------|-----|
| Recursos compartilhados | Recursos dedicados |
| Menor liberdade de configuração | Controle total do servidor |
| Sem acesso root | Acesso root (na maioria dos casos) |
| Ideal para sites pequenos | Ideal para aplicações maiores |
| Configuração simplificada | Exige conhecimentos em Linux |

---

# Distribuições Linux mais utilizadas

As distribuições mais comuns em VPS são:

- Ubuntu Server
- Debian
- Rocky Linux
- AlmaLinux
- CentOS (legado)

A escolha depende da necessidade do projeto e da familiaridade do administrador.

---

# Acessando uma VPS

O acesso normalmente é realizado utilizando o protocolo **SSH**.

```bash
ssh root@IP_DO_SERVIDOR
```

Exemplo:

```bash
ssh root@192.168.1.100
```

Na primeira conexão será exibida a confirmação da chave do servidor.

Digite:

```text
yes
```

Depois informe a senha.

---

# Atualizando o sistema

Após acessar a VPS, uma das primeiras tarefas é atualizar os pacotes do sistema.

Ubuntu/Debian

```bash
apt update
apt upgrade
```

Rocky Linux / AlmaLinux

```bash
dnf update
```

Manter o sistema atualizado ajuda a corrigir falhas de segurança e melhorar a estabilidade.

---

# Estrutura de diretórios

Alguns diretórios importantes em servidores Linux:

```text
/
├── etc        → Arquivos de configuração
├── home       → Diretórios dos usuários
├── var        → Logs e aplicações
├── usr        → Programas instalados
├── tmp        → Arquivos temporários
├── root       → Diretório do usuário root
└── opt        → Aplicações opcionais
```

---

# Serviços mais comuns em uma VPS

Uma VPS pode executar diversos serviços.

Exemplos:

- Apache
- Nginx
- PHP
- MySQL
- MariaDB
- PostgreSQL
- Docker
- Node.js
- Python
- Redis
- FTP
- SSH

É possível hospedar diversos sites ou aplicações em uma única VPS, dependendo da quantidade de recursos disponíveis.

---

# Verificando uso de recursos

Memória RAM

```bash
free -h
```

Espaço em disco

```bash
df -h
```

Uso dos diretórios

```bash
du -sh *
```

Processos em execução

```bash
ps aux
```

Monitoramento em tempo real

```bash
top
```

ou

```bash
htop
```

---

# Gerenciamento de serviços

Em distribuições modernas, os serviços são controlados pelo **systemd**.

Verificar o status:

```bash
systemctl status nginx
```

Iniciar:

```bash
systemctl start nginx
```

Parar:

```bash
systemctl stop nginx
```

Reiniciar:

```bash
systemctl restart nginx
```

Habilitar na inicialização:

```bash
systemctl enable nginx
```

---

# Transferindo arquivos

Uma forma simples de enviar arquivos para a VPS é utilizando o comando `scp`.

Enviar um arquivo:

```bash
scp arquivo.zip root@IP_DO_SERVIDOR:/var/www/html
```

Baixar um arquivo da VPS:

```bash
scp root@IP_DO_SERVIDOR:/home/backup.sql .
```

Também é comum utilizar clientes SFTP, como FileZilla ou WinSCP.

---

# Segurança básica

Após criar uma VPS, é recomendável realizar algumas configurações iniciais.

- Alterar a senha padrão.
- Criar um usuário administrativo.
- Desabilitar o login direto como root (quando possível).
- Utilizar autenticação por chave SSH.
- Manter o sistema atualizado.
- Configurar firewall.
- Fazer backups periódicos.

Essas práticas ajudam a reduzir riscos de acesso não autorizado.

---

# Casos de uso

Uma VPS Linux pode ser utilizada para:

- Hospedar sites em WordPress.
- Executar aplicações Laravel.
- Hospedar APIs em Node.js ou Django.
- Executar containers Docker.
- Servidores de banco de dados.
- Ambientes de desenvolvimento.
- Hospedagem de múltiplos domínios.
- Reverse Proxy com Nginx.

---

# Vantagens

- Maior desempenho.
- Recursos dedicados.
- Controle total do ambiente.
- Instalação de qualquer software compatível.
- Escalabilidade.
- Melhor isolamento entre aplicações.

---

# Desvantagens

- Exige conhecimentos em Linux.
- O administrador é responsável pela manutenção.
- Atualizações e backups dependem da configuração realizada.
- Configurações incorretas podem comprometer a segurança do servidor.

---

# Resumo

Uma VPS Linux oferece um ambiente flexível e isolado para hospedar aplicações, sites e serviços. Diferente da hospedagem compartilhada, ela permite maior controle sobre o sistema operacional, instalação de softwares e gerenciamento dos recursos. Por isso, é amplamente utilizada por profissionais de infraestrutura, DevOps e administradores de sistemas que necessitam de maior desempenho e liberdade de configuração.
