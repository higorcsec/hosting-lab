# Tipos de registros DNS (Apontamentos)

Os **registros DNS** são responsáveis por informar para onde um domínio deve apontar e quais serviços ele utilizará, como sites, e-mails e verificações de propriedade.

Cada tipo de registro possui uma finalidade específica.

---

# Registro A

O registro **A (Address Record)** é o tipo de apontamento mais utilizado.

Sua função é associar um domínio ou subdomínio a um **endereço IPv4**, permitindo que os usuários acessem o servidor onde o site está hospedado.

## Exemplo

```
Domínio

meusite.com
      │
      ▼
Registro A
      │
      ▼
200.150.10.5
```

Quando alguém acessa **meusite.com**, o DNS informa ao navegador que esse domínio está hospedado no endereço **200.150.10.5**.

### Quando utilizar?

- Hospedagem de sites
- APIs
- Servidores VPS
- Servidores dedicados

---

# Registro AAAA

O registro **AAAA** possui a mesma função do registro **A**, porém é utilizado para endereços **IPv6**.

## Exemplo

```
Domínio

meusite.com
      │
      ▼
Registro AAAA
      │
      ▼
2001:db8::1
```

Enquanto o registro **A** aponta para um endereço IPv4, o **AAAA** aponta para um endereço IPv6.

---

# Registro CNAME

O registro **CNAME (Canonical Name)** cria um **apelido** para outro domínio.

Diferente do registro A, ele **não aponta para um endereço IP**, mas sim para outro nome de domínio.

## Exemplo

```
www.meusite.com
        │
        ▼
CNAME
        │
        ▼
meusite.com
```

Quando um usuário acessa **www.meusite.com**, o DNS primeiro consulta **meusite.com** para descobrir o endereço IP correspondente.

### Casos de uso

- Redirecionar o subdomínio **www**
- GitHub Pages
- Vercel
- Netlify
- Azure
- AWS
- Cloudflare Pages

### Importante

Um registro **CNAME não pode coexistir com outros registros no mesmo nome**.

Por exemplo, não é permitido:

```
www

CNAME → meusite.com

A → 200.150.10.5
```

No mesmo host deve existir apenas o CNAME.

---

# Registro MX

O registro **MX (Mail Exchange)** informa quais servidores serão responsáveis por receber os e-mails do domínio.

Também possui uma **prioridade**, onde quanto **menor o número**, maior será a prioridade.

## Exemplo

```
meusite.com
      │
      ▼
MX (Prioridade 10)
      │
      ▼
mail.meusite.com
```

Se houver mais de um servidor de e-mail:

```
Prioridade 10 → mail1.meusite.com

Prioridade 20 → mail2.meusite.com
```

Caso o primeiro servidor fique indisponível, o segundo será utilizado.

---

# Registro TXT

O registro **TXT (Text Record)** armazena informações em formato de texto.

Hoje ele é amplamente utilizado para validações e autenticação de serviços.

Entre os principais usos estão:

- Verificação de propriedade do domínio
- Google Workspace
- Microsoft 365
- Cloudflare
- OpenAI
- Facebook
- GitHub

Também é utilizado para autenticação de e-mails.

### SPF

Define quais servidores estão autorizados a enviar e-mails utilizando o domínio.

Exemplo:

```
v=spf1 include:_spf.google.com ~all
```

---

### DKIM

Adiciona uma assinatura criptográfica aos e-mails enviados, garantindo sua autenticidade.

---

### DMARC

Define como os servidores de destino devem tratar mensagens que falharem nas validações SPF e DKIM.

---

# Registro NS

O registro **NS (Name Server)** informa quais servidores DNS são responsáveis por responder pelas consultas do domínio.

## Exemplo

```
meusite.com
      │
      ▼
ns1.cloudflare.com

ns2.cloudflare.com
```

Isso significa que todas as configurações DNS desse domínio serão gerenciadas pela Cloudflare.

Outros exemplos:

- Hostinger
- HostGator
- AWS Route 53
- Google Cloud DNS

---

# TTL (Time To Live)

O **TTL (Time To Live)** determina por quanto tempo um registro DNS poderá permanecer armazenado em cache antes de ser consultado novamente.

O valor é informado em **segundos**.

## Exemplo

```
TTL = 300

↓

5 minutos
```

Após esse período, o resolvedor DNS fará uma nova consulta para verificar se houve alterações.

---

## TTL baixo

```
300 segundos
(5 minutos)
```

### Vantagens

- Alterações propagam mais rapidamente.
- Ideal durante migrações de sites.
- Facilita testes de configuração.

### Desvantagens

- Aumenta a quantidade de consultas ao servidor DNS.

---

## TTL alto

```
86400 segundos
(24 horas)
```

### Vantagens

- Menor quantidade de consultas DNS.
- Melhor desempenho.
- Redução da carga nos servidores DNS.

### Desvantagens

- Alterações podem demorar várias horas para serem propagadas.

---

# Resumo

| Registro | Finalidade |
|----------|------------|
| **A** | Aponta um domínio para um endereço IPv4. |
| **AAAA** | Aponta um domínio para um endereço IPv6. |
| **CNAME** | Cria um apelido para outro domínio. |
| **MX** | Define os servidores responsáveis pelos e-mails. |
| **TXT** | Armazena informações de autenticação e verificações. |
| **NS** | Define quais servidores gerenciam o DNS do domínio. |
| **TTL** | Determina por quanto tempo um registro permanece em cache. |

