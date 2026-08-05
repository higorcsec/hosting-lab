# E-mail em Hospedagens

Além de hospedar sites, muitas empresas de hospedagem também oferecem o serviço de **e-mail profissional**, permitindo criar endereços personalizados utilizando o próprio domínio da empresa.

Exemplo:

```text
contato@empresa.com.br
financeiro@empresa.com.br
suporte@empresa.com.br
```

Diferente de serviços gratuitos, como Gmail e Outlook.com, um e-mail profissional transmite mais credibilidade e fortalece a identidade da empresa.

---

# Como funciona um e-mail?

O envio e recebimento de mensagens envolve diferentes protocolos e servidores.

Fluxo simplificado:

```text
Remetente
      │
      ▼
Servidor de E-mail
      │
      ▼
Internet
      │
      ▼
Servidor de E-mail do Destinatário
      │
      ▼
Caixa de Entrada
```

Quando um usuário envia um e-mail, o servidor verifica o domínio do destinatário, consulta os registros DNS e encaminha a mensagem ao servidor responsável.

---

# Protocolos de e-mail

## SMTP

O **SMTP (Simple Mail Transfer Protocol)** é responsável pelo **envio** de mensagens.

Sempre que um usuário envia um e-mail, é o SMTP que realiza essa comunicação.

Portas mais comuns:

```text
25
465 (SSL)
587 (TLS)
```

---

## IMAP

O **IMAP (Internet Message Access Protocol)** permite acessar os e-mails mantendo as mensagens armazenadas no servidor.

Isso significa que a mesma caixa de entrada pode ser acessada em diferentes dispositivos.

Portas:

```text
143
993 (SSL)
```

---

## POP3

O **POP3 (Post Office Protocol)** também recebe e-mails, porém normalmente realiza o download das mensagens para o dispositivo.

Dependendo da configuração, os e-mails podem ser removidos do servidor após o download.

Portas:

```text
110
995 (SSL)
```

---

# Registros DNS utilizados

O funcionamento do e-mail depende de alguns registros DNS.

## MX

Define qual servidor é responsável por receber os e-mails do domínio.

Exemplo:

```text
empresa.com.br
MX
mail.empresa.com.br
```

Sem esse registro, outros servidores não saberão para onde entregar as mensagens.

---

## SPF

Define quais servidores estão autorizados a enviar e-mails utilizando aquele domínio.

Exemplo:

```text
v=spf1 include:_spf.provedor.com ~all
```

Ajuda a reduzir falsificações de remetente (spoofing).

---

## DKIM

Adiciona uma assinatura digital às mensagens enviadas.

Essa assinatura permite que o servidor destinatário verifique se o conteúdo não foi alterado durante o envio.

---

## DMARC

Define como outros servidores devem tratar mensagens que falharem nas verificações de SPF ou DKIM.

Também fornece relatórios sobre possíveis tentativas de fraude.

---

# Clientes de e-mail

Um cliente de e-mail é o programa utilizado para acessar a caixa postal.

Exemplos:

- Microsoft Outlook
- Mozilla Thunderbird
- Apple Mail
- Gmail (via IMAP)
- Outlook.com (via IMAP)

Esses programas utilizam SMTP para enviar mensagens e IMAP ou POP3 para recebê-las.

---

# Webmail

Muitas hospedagens disponibilizam um Webmail, permitindo acessar os e-mails diretamente pelo navegador.

Exemplo:

```text
https://webmail.seudominio.com.br
```

O Webmail elimina a necessidade de instalar programas no computador.

---

# Configurando uma conta de e-mail

Para configurar uma conta em um cliente de e-mail normalmente são necessárias as seguintes informações:

Servidor de entrada (IMAP):

```text
mail.seudominio.com.br / imap.seudominio.com.br
```

Servidor de saída (SMTP):

```text
mail.seudominio.com.br / smtp.seudominio.com.br
```

Usuário:

```text
contato@empresa.com.br
```

Senha:

```text
********
```

Portas:

```text
IMAP: 993 (SSL)

SMTP: 465 ou 587
```

Essas informações normalmente são fornecidas pela empresa de hospedagem.

---

# Problemas comuns

## Não recebe e-mails

Possíveis causas:

- Registro MX incorreto.
- Caixa postal cheia.
- DNS ainda propagando.
- Firewall bloqueando conexões.

---

## Não envia e-mails

Pode ocorrer quando:

- SMTP configurado incorretamente.
- Usuário ou senha inválidos.
- Porta bloqueada.
- SPF incorreto.

---

## Mensagens indo para Spam

As causas mais comuns são:

- SPF ausente.
- DKIM não configurado.
- DMARC inexistente.
- IP do servidor listado em blacklist.
- Conteúdo suspeito da mensagem.

---

# Boas práticas

- Utilize senhas fortes.
- Ative autenticação em dois fatores quando disponível.
- Configure SPF, DKIM e DMARC.
- Faça backups periódicos.
- Utilize conexões SSL/TLS.
- Nunca compartilhe senhas por e-mail.

---

# Resumo

O serviço de e-mail é um dos recursos mais importantes oferecidos por empresas de hospedagem. Seu funcionamento depende da integração entre protocolos como SMTP, IMAP e POP3, além da configuração correta de registros DNS como MX, SPF, DKIM e DMARC. Compreender esses conceitos facilita a configuração de clientes de e-mail, a resolução de problemas e a administração de ambientes de hospedagem.
