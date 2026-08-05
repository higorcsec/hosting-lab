# Site Fora do Ar

Um dos chamados mais comuns em empresas de hospedagem é o famoso:

> **"Meu site não está abrindo."**

Nem sempre o problema está no servidor. A indisponibilidade pode ser causada por DNS, SSL, banco de dados, PHP, permissões, firewall, configurações incorretas ou até mesmo pela conexão do próprio cliente.

Por isso, o ideal é seguir um processo de diagnóstico antes de realizar qualquer alteração.

---

# Fluxo de diagnóstico

```text
Site não abre
      │
      ▼
O domínio resolve?
      │
      ├── Não → Verificar DNS
      │
      ▼
O servidor responde?
      │
      ├── Não → Verificar VPS/Hospedagem
      │
      ▼
HTTPS funciona?
      │
      ├── Não → Verificar SSL
      │
      ▼
Servidor Web responde?
      │
      ├── Não → Apache/Nginx
      │
      ▼
PHP funcionando?
      │
      ├── Não → Verificar versão e erros
      │
      ▼
Banco de dados responde?
      │
      ├── Não → MySQL/MariaDB
      │
      ▼
Verificar Logs
```

---

# 1. Verificar o DNS

O primeiro passo é confirmar se o domínio está apontando corretamente.

Consultar o registro A:

```bash
dig meusite.com
```

ou

```bash
nslookup meusite.com
```

Caso o domínio não resolva para um IP válido, o problema provavelmente está no DNS.

Possíveis causas:

- Registro A incorreto.
- Nameservers errados.
- DNS ainda propagando.
- Domínio expirado.

---

# 2. Testar conectividade

Verifique se o servidor responde.

```bash
ping meusite.com
```

Caso não responda, teste diretamente o IP.

```bash
ping 192.168.1.10
```

> Alguns servidores bloqueiam ICMP (ping), portanto a ausência de resposta não significa necessariamente que o site esteja fora do ar.

---

# 3. Testar HTTP e HTTPS

Verifique a resposta do servidor.

```bash
curl -I https://meusite.com
```

Exemplo de resposta:

```text
HTTP/2 200 OK
```

Se retornar:

```text
500 Internal Server Error
```

Existe algum erro interno na aplicação.

Se retornar:

```text
404 Not Found
```

A página solicitada não foi encontrada.

Se retornar:

```text
403 Forbidden
```

O acesso está sendo bloqueado.

---

# 4. Verificar o certificado SSL

Problemas de SSL impedem o acesso via HTTPS.

Teste:

```bash
curl -Iv https://meusite.com
```

Possíveis problemas:

- Certificado expirado.
- Cadeia de certificados incompleta.
- Domínio diferente do certificado.
- Certificado não instalado.

---

# 5. Verificar o servidor Web

Se possuir acesso à VPS, confirme se o serviço está funcionando.

Apache

```bash
systemctl status apache2
```

ou

```bash
systemctl status httpd
```

Nginx

```bash
systemctl status nginx
```

Caso esteja parado:

```bash
systemctl restart nginx
```

ou

```bash
systemctl restart apache2
```

> Em hospedagens compartilhadas normalmente o cliente não possui acesso a esses comandos.

---

# 6. Verificar a aplicação PHP

Um erro em PHP pode impedir completamente o carregamento do site.

Erros comuns:

- Atualização incompatível.
- Plugin com erro.
- Tema com erro.
- Sintaxe inválida.

Verifique os logs da aplicação ou do servidor.

---

# 7. Verificar o banco de dados

Sites como WordPress dependem do banco de dados.

Erro comum:

```text
Error establishing a database connection
```

Verifique:

- Nome do banco.
- Usuário.
- Senha.
- Host.
- Serviço MySQL.

No WordPress essas informações ficam no arquivo:

```text
wp-config.php
```

---

# 8. Conferir permissões

Permissões incorretas impedem o servidor de acessar arquivos.

Arquivos:

```text
644
```

Diretórios:

```text
755
```

Permissões muito restritivas ou excessivamente abertas podem causar erros.

---

# 9. Verificar espaço em disco

Caso o servidor esteja sem espaço, diversas aplicações deixam de funcionar.

Verifique:

```bash
df -h
```

Se o disco estiver próximo de 100%, será necessário liberar espaço.

---

# 10. Analisar os logs

Os logs geralmente indicam exatamente onde está o problema.

Alguns exemplos:

Apache

```text
error.log
access.log
```

Nginx

```text
error.log
access.log
```

PHP

```text
php_error.log
```

WordPress (quando WP_DEBUG estiver habilitado)

```text
wp-content/debug.log
```

Acompanhar em tempo real:

```bash
tail -f error.log
```

---

# Problemas comuns

## DNS incorreto

Sintomas:

- Site não abre.
- Domínio não resolve.

Solução:

- Corrigir registros DNS.
- Aguardar propagação.

---

## Certificado SSL expirado

Sintomas:

- Navegador informa que a conexão não é segura.

Solução:

- Renovar ou reinstalar o certificado.

---

## Banco indisponível

Sintomas:

```text
Error establishing a database connection
```

Solução:

- Corrigir credenciais.
- Reiniciar o banco (quando possível).
- Restaurar backup caso necessário.

---

## Plugin com erro

Sintomas:

- Tela branca.
- Erro 500.

Solução:

- Desativar o plugin.
- Atualizar.
- Restaurar versão anterior.

---

## Permissões incorretas

Sintomas:

- Erro 403.
- Arquivos não carregam.

Solução:

- Ajustar permissões dos arquivos e diretórios.

---

## PHP incompatível

Sintomas:

- Site deixa de funcionar após alterar a versão do PHP.

Solução:

- Retornar para uma versão compatível.
- Atualizar plugins e temas.

---

## Site sem espaço em disco

Sintomas:

- Uploads falham.
- Banco para de gravar.
- Erros aleatórios.

Solução:

- Remover arquivos desnecessários.
- Limpar backups antigos.
- Aumentar o espaço em disco.

---

# Boas práticas

- Nunca altere configurações sem identificar a causa do problema.
- Sempre consulte os logs antes de tomar qualquer ação.
- Faça backup antes de alterações importantes.
- Documente a causa e a solução para futuras ocorrências.
- Monitore espaço em disco, validade do SSL e registros DNS periodicamente.

---

# Resumo

Quando um site está fora do ar, o problema pode estar em diferentes camadas da infraestrutura. Um diagnóstico organizado — verificando DNS, conectividade, SSL, servidor web, aplicação, banco de dados, permissões e logs — permite identificar a causa com mais rapidez e reduzir o tempo de indisponibilidade. Esse processo faz parte da rotina de analistas de suporte, administradores de sistemas e profissionais que trabalham com hospedagem de sites.
