# Ferramentas de Diagnóstico para Hospedagem

Durante o suporte a sites, servidores e domínios, é comum utilizar ferramentas online para verificar DNS, certificados SSL, registros de domínio e identificar possíveis problemas.

Abaixo estão algumas das ferramentas mais utilizadas por profissionais de hospedagem e infraestrutura.

---

# Registro.br - WHOIS

Site:

https://registro.br/tecnologia/ferramentas/whois

O WHOIS do Registro.br permite consultar informações sobre domínios registrados no Brasil (.br).

É possível verificar:

- Situação do domínio;
- Data de criação;
- Data de expiração;
- Servidores DNS (Nameservers);
- Status do domínio.

Quando utilizar:

- Confirmar se o domínio está ativo.
- Verificar se o domínio expirou.
- Conferir quais Nameservers estão configurados.

---

# NSLookup.io

Site:

https://www.nslookup.io

Ferramenta utilizada para consultar registros DNS de um domínio.

Permite visualizar:

- Registro A
- AAAA
- MX
- TXT
- CNAME
- NS
- SOA

Também permite consultar os registros utilizando servidores DNS de diferentes regiões do mundo.

Quando utilizar:

- Verificar apontamentos DNS.
- Confirmar alterações.
- Diagnosticar problemas de resolução.

---

# WhatsMyDNS

Site:

https://www.whatsmydns.net

Uma das ferramentas mais utilizadas para verificar a propagação de DNS.

Ela consulta servidores espalhados por diversos países e mostra como cada região está resolvendo um determinado registro DNS.

Suporta consultas:

- A
- AAAA
- MX
- TXT
- CNAME
- NS
- PTR

Quando utilizar:

- Após alterar registros DNS.
- Confirmar propagação mundial.
- Diagnosticar inconsistências entre regiões.

---

# SSL Shopper

Site:

https://www.sslshopper.com/ssl-checker.html

Ferramenta para verificar certificados SSL.

Ela informa:

- Validade do certificado.
- Data de expiração.
- Autoridade Certificadora (CA).
- Cadeia de certificados.
- Problemas na instalação.

Quando utilizar:

- Site apresenta erro de certificado.
- Navegador informa conexão insegura.
- Após instalar ou renovar um SSL.

---

# VirusTotal

Site:

https://www.virustotal.com

O VirusTotal é uma das ferramentas mais conhecidas para verificar a reputação de arquivos, URLs e domínios.

Ao informar uma URL, ela é analisada por dezenas de mecanismos de segurança diferentes.

A ferramenta pode identificar:

- Sites maliciosos.
- Phishing.
- Malware.
- Domínios suspeitos.
- Links utilizados em golpes.

Quando utilizar:

- Antes de acessar um site desconhecido.
- Validar links enviados por terceiros.
- Investigar possíveis ataques de phishing.

---

# Google Safe Browsing

Site:

https://transparencyreport.google.com/safe-browsing/search

O Google Safe Browsing verifica se um domínio foi identificado pelo Google como potencialmente perigoso.

Ele informa se o site foi marcado por:

- Malware;
- Engenharia social (phishing);
- Downloads perigosos.

Essa ferramenta é muito utilizada antes de liberar um domínio para clientes.

---

# MXToolbox

Site:

https://mxtoolbox.com

Uma das ferramentas mais completas para administração de e-mails e DNS.

Permite verificar:

- MX
- SPF
- DKIM
- DMARC
- Blacklists
- DNS
- SMTP

Muito utilizada por profissionais de suporte para diagnosticar problemas de envio e recebimento de e-mails.

---

# Down For Everyone Or Just Me

Site:

https://downforeveryoneorjustme.com

Permite verificar rapidamente se um site está indisponível para todos ou apenas para você.

Quando utilizar:

- Confirmar se o problema é global.
- Verificar indisponibilidade antes de iniciar um diagnóstico mais complexo.

---

# Resumo

| Ferramenta | Finalidade |
|------------|------------|
| Registro.br WHOIS | Consultar informações de domínios .br |
| NSLookup.io | Consultar registros DNS |
| WhatsMyDNS | Verificar propagação de DNS |
| SSL Shopper | Validar certificados SSL |
| VirusTotal | Verificar reputação de URLs e domínios |
| Google Safe Browsing | Consultar segurança de um site |
| MXToolbox | Diagnóstico de DNS e e-mail |
| Down For Everyone Or Just Me | Confirmar indisponibilidade de um site |

---

# Boas práticas

Antes de alterar qualquer configuração em um servidor ou hospedagem, utilize essas ferramentas para validar o problema. Muitas vezes a causa da indisponibilidade pode estar relacionada à propagação de DNS, certificados expirados ou configurações incorretas de e-mail, evitando alterações desnecessárias no ambiente.
