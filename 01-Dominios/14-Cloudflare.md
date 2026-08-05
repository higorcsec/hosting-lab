# Cloudflare

A **Cloudflare** é uma plataforma de segurança, desempenho e infraestrutura que fica entre o visitante e o servidor onde o site está hospedado.

Ela atua como uma camada intermediária (Proxy Reverso), recebendo todas as requisições dos usuários antes de encaminhá-las para o servidor de origem.

Além de melhorar o desempenho, a Cloudflare oferece recursos como proteção contra ataques, CDN, gerenciamento de DNS, certificados SSL e cache.

---

# Como a Cloudflare funciona?

Sem Cloudflare:

```text
Usuário
    │
    ▼
Servidor de Hospedagem
    │
    ▼
Site
```

Com Cloudflare:

```text
Usuário
    │
    ▼
Cloudflare
    │
    ▼
Servidor de Hospedagem
    │
    ▼
Site
```

Nesse modelo, o visitante nunca acessa diretamente o servidor. Primeiro a requisição passa pela Cloudflare.

---

# Principais funcionalidades

A Cloudflare reúne diversos serviços em uma única plataforma.

Entre os principais estão:

- CDN (Content Delivery Network)
- Gerenciamento de DNS
- Certificados SSL
- Cache de conteúdo
- Proteção contra ataques DDoS
- Firewall (WAF)
- Redirecionamentos
- Compressão de arquivos
- Otimização de imagens
- Estatísticas de acesso

---

# CDN (Content Delivery Network)

A CDN distribui cópias dos arquivos do site em servidores espalhados pelo mundo.

Quando um visitante acessa o site, ele recebe os arquivos do servidor mais próximo.

Exemplo:

```text
Visitante (Brasil)
        │
        ▼
Servidor Cloudflare (São Paulo)
        │
        ▼
Servidor Principal (Estados Unidos)
```

Isso reduz a latência e melhora o tempo de carregamento.

---

# Cache

A Cloudflare pode armazenar temporariamente arquivos estáticos.

Exemplos:

- Imagens
- CSS
- JavaScript
- Fontes
- Arquivos HTML (quando configurado)

Assim, nem todas as requisições precisam chegar ao servidor de hospedagem.

Isso reduz:

- Uso de CPU
- Consumo de banda
- Tempo de resposta

---

# DNS

Um dos serviços mais utilizados da Cloudflare é o gerenciamento de DNS.

É possível criar registros como:

- A
- AAAA
- CNAME
- MX
- TXT
- NS

Alterações podem ser feitas diretamente pelo painel da Cloudflare.

---

# SSL

A Cloudflare também oferece certificados SSL gratuitos.

Ela permite diferentes modos de funcionamento:

## Off

Sem HTTPS.

---

## Flexible

A conexão entre o visitante e a Cloudflare utiliza HTTPS.

Entre a Cloudflare e o servidor utiliza HTTP.

```text
Usuário

HTTPS

Cloudflare

HTTP

Servidor
```

Esse modo não é recomendado para ambientes de produção por oferecer menor segurança.

---

## Full

A comunicação utiliza HTTPS entre todas as partes.

```text
Usuário

HTTPS

Cloudflare

HTTPS

Servidor
```

O certificado instalado no servidor pode ser autoassinado.

---

## Full (Strict)

Também utiliza HTTPS em toda a comunicação, porém exige um certificado válido instalado no servidor.

É o modo mais seguro e recomendado.

---

# Proxy

Ao criar um registro DNS na Cloudflare, é possível escolher entre dois modos.

## DNS Only

```text
☁️ Cinza
```

A Cloudflare apenas responde pelo DNS.

O visitante acessa diretamente o servidor.

---

## Proxied

```text
🟧 Nuvem Laranja
```

Todo o tráfego passa pela Cloudflare.

Nesse modo ficam disponíveis recursos como:

- CDN
- Cache
- Firewall
- Proteção DDoS
- SSL

---

# Firewall (WAF)

A Cloudflare possui um Firewall de Aplicação (WAF).

Ele ajuda a bloquear:

- Bots maliciosos;
- Ataques automatizados;
- SQL Injection;
- Cross Site Scripting (XSS);
- Exploração de vulnerabilidades conhecidas.

---

# Proteção DDoS

Ataques DDoS tentam sobrecarregar um servidor enviando milhares ou milhões de requisições.

Como a Cloudflare recebe essas conexões antes do servidor, ela consegue filtrar grande parte desse tráfego malicioso.

---

# Erros comuns

Alguns erros exibidos pela Cloudflare são bastante conhecidos.

## Erro 521

O servidor recusou a conexão.

Possíveis causas:

- Nginx parado.
- Apache parado.
- Firewall bloqueando.
- Porta incorreta.

---

## Erro 522

A Cloudflare conseguiu localizar o servidor, porém não recebeu resposta dentro do tempo esperado.

Pode ocorrer por:

- Servidor sobrecarregado.
- Firewall.
- Problemas de rede.

---

## Erro 523

A Cloudflare não conseguiu localizar o servidor de origem.

Normalmente está relacionado ao DNS ou ao IP configurado.

---

## Erro 524

A conexão foi estabelecida, porém o servidor demorou mais do que o tempo permitido para responder.

Geralmente ocorre em:

- Consultas muito pesadas.
- Banco de dados lento.
- Aplicações com processamento excessivo.

---

# Hospedagem Compartilhada

Em hospedagens compartilhadas, normalmente basta alterar os **Nameservers** do domínio para os fornecidos pela Cloudflare.

Depois disso, todo o gerenciamento de DNS passa a ser realizado pelo painel da Cloudflare.

Não é necessário instalar nenhum software no servidor.

---

# VPS

Em uma VPS, além da configuração dos Nameservers, normalmente é necessário:

- Configurar SSL corretamente.
- Liberar as portas HTTP (80) e HTTPS (443).
- Configurar Nginx ou Apache.
- Ajustar regras de Firewall.
- Garantir que o servidor aceite conexões provenientes da Cloudflare.

---

# Vantagens

- CDN gratuita.
- Melhor desempenho.
- Proteção contra ataques DDoS.
- DNS rápido.
- SSL gratuito.
- Cache de conteúdo.
- Firewall de Aplicação (WAF).
- Estatísticas detalhadas.
- Fácil integração com hospedagens.

---

# Desvantagens

- Algumas funcionalidades avançadas são pagas.
- Configurações incorretas podem causar erros de cache.
- Modo SSL inadequado pode gerar loops de redirecionamento.
- É necessário compreender o funcionamento do Proxy para evitar problemas.

---

# Boas práticas

- Utilize o modo **Full (Strict)** sempre que possível.
- Mantenha os registros DNS atualizados.
- Limpe o cache após alterações importantes no site.
- Utilize HTTPS em todo o ambiente.
- Monitore os erros retornados pela Cloudflare.
- Utilize regras de Firewall apenas quando necessário.

---

# Resumo

A Cloudflare é uma plataforma que combina gerenciamento de DNS, CDN, certificados SSL, cache, firewall e proteção contra ataques em um único serviço. Ela atua como um intermediário entre o visitante e o servidor, aumentando a segurança, melhorando o desempenho e reduzindo a carga sobre a infraestrutura. Por esses motivos, é amplamente utilizada em hospedagens compartilhadas, VPS e ambientes corporativos.
