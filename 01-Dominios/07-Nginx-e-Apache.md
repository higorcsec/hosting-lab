# Nginx e Apache

Quando acessamos um site, existe um software responsável por receber a requisição do navegador, localizar os arquivos da aplicação e devolver a resposta ao usuário. Esse software é chamado de **servidor web (Web Server)**.

Os dois servidores web mais utilizados do mercado são o **Apache HTTP Server** e o **Nginx**. Ambos cumprem o mesmo objetivo, porém possuem arquiteturas diferentes e são indicados para cenários distintos.

---

# O que é um servidor web?

Um servidor web é responsável por:

- Receber requisições HTTP e HTTPS.
- Localizar os arquivos do site.
- Processar aplicações dinâmicas (PHP, por exemplo).
- Retornar páginas HTML, imagens, CSS, JavaScript e outros arquivos ao navegador.
- Gerenciar conexões simultâneas de usuários.

Fluxo simplificado de uma requisição:

```text
Usuário
    │
    ▼
 Navegador
    │
    ▼
Servidor Web (Apache ou Nginx)
    │
    ▼
Aplicação (WordPress, Laravel, etc.)
    │
    ▼
Banco de Dados (MySQL/MariaDB)
    │
    ▼
Resposta ao navegador
```

---

# O Apache

O **Apache HTTP Server** é um dos servidores web mais antigos e populares do mercado. Criado em 1995 pela Apache Software Foundation, ele é conhecido pela estabilidade, grande compatibilidade e facilidade de configuração.

Por muitos anos foi o servidor web padrão das hospedagens compartilhadas.

## Principais características

- Open Source.
- Compatível com Linux e Windows.
- Grande quantidade de módulos.
- Excelente compatibilidade com aplicações PHP.
- Muito utilizado em hospedagens compartilhadas.

---

# Como o Apache funciona?

O Apache recebe a requisição do navegador e identifica qual site deve responder através da configuração do servidor (Virtual Hosts).

Caso a aplicação utilize PHP, o Apache envia a requisição para o interpretador PHP, que executa o código e gera a página antes de devolvê-la ao usuário.

Fluxo:

```text
Cliente
    │
    ▼
Apache
    │
    ▼
PHP
    │
    ▼
MySQL
    │
    ▼
Resposta
```

---

# Arquivo .htaccess

Uma das maiores vantagens do Apache é o suporte ao arquivo **`.htaccess`**.

Esse arquivo permite alterar configurações do site sem modificar a configuração principal do servidor.

Exemplos:

- Redirecionamentos.
- Regras de URL amigável.
- Bloqueio de IP.
- Proteção por senha.
- Cache.
- Compressão.

Por esse motivo, muitos sistemas como o WordPress utilizam automaticamente o `.htaccess`.

---

# O Nginx

O **Nginx** (pronuncia-se "Engine-X") foi lançado em 2004 com foco em alto desempenho e baixo consumo de memória.

Hoje ele é um dos servidores web mais utilizados do mundo, principalmente em aplicações de grande escala.

Além de servir sites, o Nginx também pode atuar como:

- Reverse Proxy.
- Load Balancer.
- Proxy para APIs.
- Servidor de arquivos estáticos.

---

# Como o Nginx funciona?

O Nginx utiliza uma arquitetura baseada em eventos (**event-driven**), permitindo atender milhares de conexões simultaneamente utilizando poucos processos.

Quando um usuário acessa um site:

```text
Cliente
    │
    ▼
Nginx
    │
    ▼
PHP-FPM
    │
    ▼
MySQL
    │
    ▼
Resposta
```

Diferente do Apache, o Nginx normalmente trabalha em conjunto com o **PHP-FPM**, responsável por interpretar os arquivos PHP.

---

# Nginx como Reverse Proxy

Um dos usos mais comuns do Nginx é funcionar como **Reverse Proxy**.

Nesse cenário ele recebe todas as requisições e as encaminha para outro serviço interno.

Exemplo:

```text
Internet
      │
      ▼
    Nginx
   /      \
  ▼        ▼
API      WordPress
```

Essa arquitetura é muito utilizada com Docker, Node.js, Django, Laravel e outras aplicações.

---

# Apache x Nginx

| Característica | Apache | Nginx |
|----------------|---------|--------|
| Ano de criação | 1995 | 2004 |
| Arquitetura | Processos/Threads | Baseada em eventos |
| Consumo de memória | Maior | Menor |
| Arquivo `.htaccess` | Sim | Não |
| PHP | Integrado ou PHP-FPM | PHP-FPM |
| Arquivos estáticos | Bom | Excelente |
| Muitas conexões simultâneas | Bom | Excelente |

---

# Qual utilizar?

Não existe um servidor melhor em todos os cenários.

O **Apache** costuma ser uma excelente escolha para:

- Hospedagens compartilhadas.
- WordPress.
- Aplicações legadas.
- Ambientes que utilizam `.htaccess`.

O **Nginx** é muito utilizado em:

- VPS.
- Cloud.
- Docker.
- APIs.
- Aplicações com alto volume de acessos.
- Reverse Proxy.

Em muitos ambientes profissionais os dois trabalham juntos:

```text
Internet
     │
     ▼
Nginx
     │
     ▼
Apache
     │
     ▼
PHP
     │
     ▼
MySQL
```

Nesse modelo, o Nginx recebe as conexões externas e o Apache processa a aplicação.

---

# Arquivos de configuração

## Apache

Normalmente os arquivos de configuração ficam em:

```text
/etc/apache2/
/etc/httpd/
```

O arquivo principal costuma ser:

```text
apache2.conf
```

ou

```text
httpd.conf
```

---

## Nginx

As configurações geralmente ficam em:

```text
/etc/nginx/
```

O arquivo principal é:

```text
nginx.conf
```

Os sites costumam ser configurados em:

```text
sites-available/
sites-enabled/
```

---

# Resumo

Apache e Nginx são os servidores web mais utilizados atualmente. Ambos têm a função de receber requisições HTTP/HTTPS e entregar o conteúdo das aplicações aos usuários.

O Apache se destaca pela compatibilidade e facilidade de configuração, sendo muito comum em hospedagens compartilhadas. Já o Nginx oferece alto desempenho, baixo consumo de recursos e recursos avançados como Reverse Proxy e Load Balancer, tornando-se uma escolha frequente para VPS, aplicações em nuvem e ambientes com grande volume de acessos.
