# O que é um domínio e como funciona

## O que é um domínio?

Um **domínio** é um nome legível que identifica um site na internet. Ele existe para facilitar o acesso aos serviços online, substituindo a necessidade de memorizar endereços IP.

Por exemplo, é muito mais fácil acessar:

```
google.com
```

do que lembrar de um endereço IP como:

```
142.250.219.14
```

Em outras palavras, o domínio funciona como um **apelido** para o endereço IP do servidor onde o site está hospedado.

---

# Como funciona?

Quando você acessa um site, ocorre o seguinte processo:

```
Você digita:

meusite.com.br
        │
        ▼
Seu computador consulta um servidor DNS
("Qual é o IP desse domínio?")
        │
        ▼
O servidor DNS responde:

200.150.10.5
        │
        ▼
Seu navegador estabelece conexão
com esse endereço IP
        │
        ▼
O servidor responde enviando
o conteúdo do site
```

Todo esse processo acontece em poucos milissegundos.

---

# Exemplo prático

Imagine que você deseja acessar:

```
www.exemplo.com
```

O navegador não sabe onde esse site está hospedado.

Primeiro, ele consulta o DNS.

O DNS responde:

```
www.exemplo.com
↓

192.168.100.50
```

Depois disso, o navegador envia uma requisição diretamente para esse endereço IP e o servidor retorna o site.

---
