# Boas Práticas de Segurança

A segurança é um dos pilares de qualquer ambiente de hospedagem. Seja em uma hospedagem compartilhada ou em uma VPS, adotar boas práticas reduz significativamente o risco de invasões, vazamento de informações e indisponibilidade dos serviços.

Embora em uma hospedagem compartilhada muitas configurações sejam gerenciadas pelo provedor, ainda existem diversas medidas que podem ser adotadas pelo usuário. Em uma VPS, a responsabilidade pela segurança é ainda maior, pois o administrador possui controle total sobre o servidor.

---

# Hospedagem Compartilhada

Em hospedagens compartilhadas o usuário normalmente não possui acesso root, portanto a segurança depende tanto do provedor quanto das boas práticas adotadas na aplicação.

## Utilize senhas fortes

Evite senhas simples como:

```text
123456
admin
senha123
meusite2025
```

Prefira senhas longas contendo:

- Letras maiúsculas;
- Letras minúsculas;
- Números;
- Caracteres especiais.

Exemplo:

```text
M3uS!t3@2026#
```

---

## Mantenha o CMS atualizado

Caso utilize WordPress, Joomla, Drupal ou outro CMS, mantenha sempre atualizados:

- Núcleo do sistema;
- Plugins;
- Temas.

Grande parte das invasões ocorre por falhas já corrigidas em versões mais recentes.

---

## Remova plugins e temas não utilizados

Mesmo desativados, plugins vulneráveis podem representar riscos.

Remova tudo aquilo que não estiver sendo utilizado.

---

## Utilize HTTPS

Sempre utilize certificados SSL.

Além de proteger os dados transmitidos, o HTTPS aumenta a confiança do usuário e melhora o posicionamento em mecanismos de busca.

---

## Faça backups frequentes

Nunca dependa apenas do backup realizado pela empresa de hospedagem.

Sempre que possível mantenha uma cópia própria.

---

## Utilize autenticação em dois fatores (2FA)

Se o painel da hospedagem ou o WordPress oferecerem autenticação em dois fatores, mantenha esse recurso ativado.

---

## Proteja o acesso administrativo

Evite utilizar usuários como:

```text
admin
administrator
root
```

Prefira nomes menos previsíveis.

Além disso:

- Utilize senhas fortes;
- Restrinja quem possui acesso administrativo.

---

## Utilize apenas plugins confiáveis

Instale plugins e temas apenas de fontes oficiais ou desenvolvedores reconhecidos.

Evite versões modificadas ("nulled"), pois frequentemente contêm códigos maliciosos.

---

# VPS

Em uma VPS, além das boas práticas anteriores, o administrador é responsável pela segurança do sistema operacional.

---

## Mantenha o sistema atualizado

Ubuntu/Debian

```bash
apt update
apt upgrade
```

Rocky Linux / AlmaLinux

```bash
dnf update
```

Atualizações corrigem vulnerabilidades conhecidas.

---

## Utilize um firewall

Permita apenas as portas realmente necessárias.

Exemplo utilizando UFW:

```bash
ufw allow 22
ufw allow 80
ufw allow 443
```

Bloqueie todo o restante.

---

## Evite utilizar o usuário root

O recomendado é criar um usuário administrativo e utilizar privilégios elevados apenas quando necessário.

Isso reduz o impacto de acessos indevidos.

---

## Utilize autenticação por chave SSH

Sempre que possível, utilize chaves SSH em vez de autenticação por senha.

Exemplo para gerar uma chave:

```bash
ssh-keygen
```

Esse método oferece maior segurança contra ataques de força bruta.

---

## Desabilite o login direto do root

Quando possível, configure o SSH para impedir o login direto do usuário root.

Assim, um invasor precisará comprometer primeiro um usuário comum antes de tentar obter privilégios administrativos.

---

## Utilize Fail2Ban

O Fail2Ban monitora tentativas de login e bloqueia automaticamente endereços IP com múltiplas falhas de autenticação.

É uma das ferramentas mais utilizadas para proteger serviços como SSH.

---

## Monitore os logs

Verifique regularmente arquivos de log.

Exemplos:

```text
/var/log/auth.log
/var/log/syslog
/var/log/nginx/error.log
/var/log/apache2/error.log
```

Os logs ajudam a identificar acessos suspeitos e falhas no sistema.

---

## Faça backups automatizados

Utilize scripts e tarefas agendadas (cron) para manter backups atualizados.

Também é recomendável armazenar cópias em outro servidor ou na nuvem.

---

## Proteja o banco de dados

Boas práticas:

- Não utilize o usuário root na aplicação;
- Utilize senhas fortes;
- Conceda apenas as permissões necessárias;
- Restrinja acessos remotos quando possível.

---

## Mantenha apenas serviços necessários

Cada serviço em execução aumenta a superfície de ataque.

Remova ou desative aplicações que não estejam sendo utilizadas.

---

# Boas práticas para ambos os ambientes

Independentemente do ambiente, algumas recomendações são sempre válidas.

- Utilize senhas fortes.
- Faça backups periódicos.
- Utilize HTTPS.
- Mantenha sistemas atualizados.
- Instale apenas softwares confiáveis.
- Monitore logs.
- Revise permissões de acesso.
- Limite usuários administrativos.
- Evite compartilhar credenciais.
- Documente alterações importantes.

---

# Erros comuns

Alguns erros aumentam significativamente os riscos de segurança.

- Utilizar senhas fracas.
- Deixar sistemas desatualizados.
- Instalar plugins de origem desconhecida.
- Não realizar backups.
- Utilizar o mesmo usuário e senha em vários serviços.
- Ignorar alertas de segurança.
- Conceder permissões excessivas a usuários ou arquivos.

---

# Checklist de Segurança

Antes de colocar um site em produção, verifique:

- [ ] O sistema está atualizado?
- [ ] O certificado SSL está instalado?
- [ ] Existem backups recentes?
- [ ] As senhas são fortes?
- [ ] Apenas usuários necessários possuem acesso?
- [ ] Os plugins utilizados são confiáveis?
- [ ] O firewall está configurado? (VPS)
- [ ] O SSH utiliza autenticação segura? (VPS)
- [ ] Os logs estão sendo monitorados?
- [ ] Os serviços desnecessários foram removidos?

---

# Resumo

A segurança deve fazer parte da rotina de qualquer profissional que trabalhe com hospedagem de sites e servidores Linux. Em hospedagens compartilhadas, grande parte da infraestrutura é administrada pelo provedor, mas cabe ao usuário manter aplicações atualizadas, utilizar senhas fortes e realizar backups. Em uma VPS, o administrador assume total responsabilidade pelo ambiente, incluindo atualizações do sistema, firewall, autenticação SSH, monitoramento de logs e proteção dos serviços. A adoção dessas boas práticas reduz riscos e contribui para um ambiente mais seguro e estável.
