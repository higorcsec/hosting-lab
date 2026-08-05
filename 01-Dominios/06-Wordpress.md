# Instalando o WordPress via SSH (Hospedagem Compartilhada)

O **WordPress** é o CMS (**Content Management System**) mais utilizado do mundo para criação de sites, blogs, lojas virtuais e portais.

Ele é desenvolvido principalmente em **PHP** e utiliza um banco de dados **MySQL** ou **MariaDB** para armazenar informações como páginas, usuários, configurações e posts.

Uma das vantagens do WordPress é sua facilidade de instalação. Em hospedagens compartilhadas, normalmente existe um instalador automático (Softaculous, Installatron, etc.), porém muitos profissionais preferem realizar a instalação manual via **SSH**, pois ela oferece mais controle sobre os arquivos e permite automatizar processos.

---

# Pré-requisitos

Antes de iniciar, você deve possuir:

- Acesso SSH habilitado pela hospedagem;
- Um domínio ou subdomínio apontando para a hospedagem;
- Banco de dados MySQL criado;
- Usuário e senha do banco de dados;
- PHP instalado no servidor (geralmente já disponível em hospedagens compartilhadas).

---

# Conectando ao servidor

Conecte-se utilizando SSH.

```bash
ssh usuario@servidor.com
```

Exemplo:

```bash
ssh user@meusite.com.br
```

Após informar sua senha, você terá acesso ao terminal do servidor.

---

# Acessando a pasta do site

Na maioria das hospedagens compartilhadas existe uma pasta onde ficam os arquivos públicos do site.

Alguns exemplos:

```text
public_html
htdocs
www
httpdocs
```

Entre na pasta correta.

```bash
cd public_html
```

Verifique se está no local correto.

```bash
pwd
```

---

# Baixando o WordPress

O WordPress disponibiliza sempre a versão mais recente em seu site oficial.

Baixe utilizando o comando:

```bash
wget https://wordpress.org/latest.tar.gz
```

Caso a hospedagem não possua o `wget`, utilize:

```bash
curl -O https://wordpress.org/latest.tar.gz
```

Após o download, confira se o arquivo foi baixado.

```bash
ls
```

Você deverá visualizar:

```text
latest.tar.gz
```

---

# Extraindo os arquivos

Extraia o conteúdo do arquivo.

```bash
tar -xzvf latest.tar.gz
```

Será criada uma pasta chamada:

```text
wordpress/
```

---

# Movendo os arquivos

Entre na pasta criada.

```bash
cd wordpress
```

Mova todos os arquivos para a pasta principal do site.

```bash
mv * ../
```



Volte para a pasta principal.

```bash
cd ..
```

Remova os arquivos temporários.

```bash
rm -rf wordpress
rm latest.tar.gz
```

