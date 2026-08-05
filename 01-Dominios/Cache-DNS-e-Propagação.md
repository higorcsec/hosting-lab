# Cache DNS e Propagação

Quando um registro DNS é alterado, a mudança **não acontece instantaneamente** em toda a internet.

Isso ocorre porque os servidores DNS armazenam informações temporariamente em **cache**, reduzindo o número de consultas e tornando a navegação mais rápida.

Por esse motivo, após alterar um registro DNS, pode demorar alguns minutos ou até horas para que todos os usuários passem a enxergar a nova configuração.

---

# O que é Cache DNS?

O **cache DNS** é um armazenamento temporário das consultas DNS.

Sempre que um computador ou servidor consulta um domínio, a resposta é salva por um determinado período.

Em vez de perguntar novamente ao servidor DNS a cada acesso, o sistema reutiliza essa informação até que ela expire.

Isso torna a navegação muito mais rápida e reduz o tráfego na infraestrutura DNS.

---

# Como funciona?

Imagine o seguinte cenário:

```
Você acessa

meusite.com
      │
      ▼
Servidor DNS responde

203.0.113.10
      │
      ▼
Seu computador salva essa informação
em cache
      │
      ▼
Nos próximos acessos
não será necessário consultar
o servidor DNS novamente
```

Quando o tempo de cache expirar, uma nova consulta será realizada.

---

# O que é Propagação DNS?

A **propagação DNS** é o período necessário para que uma alteração seja reconhecida por todos os servidores DNS espalhados pelo mundo.

Por exemplo, imagine que você alterou o endereço IP do seu site.

Antes:

```
meusite.com

↓

203.0.113.10
```

Depois da alteração:

```
meusite.com

↓

198.51.100.20
```

Nem todos os usuários verão imediatamente o novo IP.

Quem ainda possui o registro antigo em cache continuará acessando o servidor antigo até que o cache expire.

---

# Por que isso acontece?

Existem diversos caches espalhados pela internet.

Entre eles:

- Computador do usuário
- Navegador
- Provedor de internet (ISP)
- Servidores DNS públicos (Google DNS, Cloudflare, OpenDNS)
- Sistemas operacionais

Cada um possui seu próprio tempo de armazenamento.

---

# Relação com o TTL

O **TTL (Time To Live)** informa por quanto tempo um registro poderá permanecer em cache.

Exemplo:

```
TTL = 300

↓

5 minutos
```

Após esse período, será realizada uma nova consulta ao servidor DNS.

Outro exemplo:

```
TTL = 86400

↓

24 horas
```

Nesse caso, alguns usuários poderão continuar utilizando o endereço antigo durante um dia inteiro.

---

# Exemplo prático

Imagine que você migrou seu site para outro servidor.

Antes:

```
Registro A

meusite.com

↓

203.0.113.10
```

Depois:

```
Registro A

meusite.com

↓

198.51.100.20
```

Usuário A:

```
Ainda possui o IP antigo em cache.

↓

Acessa o servidor antigo.
```

Usuário B:

```
O cache expirou.

↓

Recebe o novo IP.
```

Por isso é comum ouvir a frase:

> "Aqui já abriu, mas para meu cliente ainda não."

Na maioria dos casos, trata-se apenas do cache DNS.

---

# Como verificar a propagação?

Existem diversas formas de verificar se a alteração já foi propagada.

### Consultando pelo terminal

Linux:

```
dig meusite.com
```

```
nslookup meusite.com
```

Windows:

```cmd
nslookup meusite.com
```

Esses comandos mostram qual endereço IP está sendo retornado pelo servidor DNS consultado.

---

# Como limpar o cache DNS?

Em alguns casos é possível limpar o cache local.

### Windows

```
ipconfig /flushdns
```

### Linux (systemd)

```
sudo resolvectl flush-caches
```

> O comando pode variar conforme a distribuição Linux utilizada.

Também pode ser necessário limpar o cache do navegador.

---

# Boas práticas

- Reduza o TTL antes de realizar uma migração.
- Aguarde a propagação completa antes de remover o servidor antigo.
- Sempre teste utilizando diferentes servidores DNS.
- Utilize ferramentas como `dig` e `nslookup` para confirmar as alterações.

---

# Resumo

O cache DNS melhora o desempenho da internet armazenando temporariamente os registros DNS.

Já a propagação DNS é o tempo necessário para que uma alteração seja reconhecida pelos diversos servidores DNS ao redor do mundo.

Por isso, alterações em registros DNS normalmente não são aplicadas de forma imediata.


