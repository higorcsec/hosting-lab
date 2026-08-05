# Backup e Restore

Fazer backup é uma das tarefas mais importantes na administração de servidores Linux, VPS e hospedagens compartilhadas. Um backup permite restaurar rapidamente um site, banco de dados ou aplicação em caso de falhas, exclusões acidentais, ataques, erros humanos ou problemas durante atualizações.

Independentemente do ambiente utilizado, recomenda-se manter uma rotina de backups e realizar testes periódicos de restauração para garantir que os dados possam ser recuperados quando necessário.

---

# O que deve ser incluído no backup?

Na maioria dos casos, um site é composto por duas partes principais:

- Arquivos da aplicação (WordPress, Laravel, HTML, CSS, JavaScript, etc.);
- Banco de dados (MySQL ou MariaDB).

Fazer backup apenas dos arquivos ou apenas do banco de dados normalmente não é suficiente para restaurar completamente o ambiente.

---

# Backup em Hospedagem Compartilhada

Em hospedagens compartilhadas, o usuário normalmente **não possui acesso root**, portanto algumas operações dependem dos recursos disponibilizados pela empresa de hospedagem.

## Backup pelo painel de controle

A maioria dos provedores oferece uma ferramenta de backup no painel (cPanel, hPanel, Plesk, DirectAdmin, entre outros).

Geralmente é possível:

- Baixar os arquivos do site;
- Exportar bancos de dados;
- Restaurar backups anteriores (quando disponível).

Essa costuma ser a opção mais simples para usuários iniciantes.

---

## Backup via SSH

Caso a hospedagem disponibilize acesso SSH, também é possível criar backups manualmente.

Compactando os arquivos do site:

```bash
tar -czvf backup-site.tar.gz public_html/
```

Caso o servidor utilize ZIP:

```bash
zip -r backup-site.zip public_html/
```

---

## Backup do banco de dados

Quando o comando `mysqldump` estiver disponível:

```bash
mysqldump -u usuario -p banco > backup.sql
```

Algumas hospedagens bloqueiam esse comando.

Nesses casos, o backup pode ser exportado pelo **phpMyAdmin**, disponível no painel de controle.

---

# Backup em VPS

Em uma VPS o administrador possui acesso total ao sistema operacional, permitindo realizar backups completos da aplicação.

## Backup dos arquivos

```bash
tar -czvf backup-site.tar.gz /var/www/html
```

---

## Backup do banco

```bash
mysqldump -u usuario -p banco > backup.sql
```

Também é possível realizar backups de múltiplos bancos ou automatizar todo o processo utilizando scripts.

---

# Backup completo

Uma prática bastante utilizada consiste em armazenar os arquivos e o banco de dados juntos.

Exemplo:

```text
backup/
├── site.tar.gz
└── banco.sql
```

Assim é possível restaurar completamente o ambiente caso seja necessário.

---

# Restaurando em Hospedagem Compartilhada

## Restaurando os arquivos

Caso possua acesso SSH:

```bash
tar -xzvf backup-site.tar.gz
```

Outra opção é utilizar o Gerenciador de Arquivos do painel da hospedagem.

---

## Restaurando o banco

Se o comando estiver disponível:

```bash
mysql -u usuario -p banco < backup.sql
```

Caso contrário, basta utilizar o **phpMyAdmin** e importar o arquivo SQL.

---

# Restaurando em VPS

Arquivos:

```bash
tar -xzvf backup-site.tar.gz -C /var/www/html
```

Banco:

```bash
mysql -u usuario -p banco < backup.sql
```

Após restaurar os arquivos, é recomendável verificar permissões e testar o funcionamento da aplicação.

---

# Compactando backups

Para reduzir espaço em disco, é comum compactar os backups.

Utilizando TAR.GZ:

```bash
tar -czvf backup-completo.tar.gz backup/
```

Ou ZIP:

```bash
zip -r backup.zip backup/
```

Além de economizar espaço, a compactação facilita o envio e armazenamento dos arquivos.

---

# Automatizando backups (VPS)

Em servidores Linux, normalmente utiliza-se o **cron** para executar backups automaticamente.

Exemplo:

```bash
0 2 * * * /home/usuario/scripts/backup.sh
```

Nesse exemplo, o script será executado diariamente às 02:00.

Em hospedagens compartilhadas, essa funcionalidade depende dos recursos disponibilizados pelo provedor.

---

# Onde armazenar os backups?

Um erro comum é manter o backup apenas no próprio servidor.

Se ocorrer uma falha no disco, invasão ou perda da VPS, o backup poderá ser perdido junto com os dados originais.

Boas opções para armazenamento:

- Outro servidor;
- Armazenamento em nuvem;
- NAS;
- HD externo;
- Serviços específicos de backup.

Sempre que possível, mantenha uma cópia fora do ambiente principal.

---

# Regra 3-2-1

Uma das estratégias mais utilizadas em infraestrutura é a regra **3-2-1**.

Ela consiste em manter:

- **3 cópias** dos dados;
- **2 tipos diferentes de armazenamento**;
- **1 cópia fora do ambiente principal (off-site).**

Exemplo:

```text
Servidor Principal
        │
        ▼
Backup em outro disco
        │
        ▼
Backup na nuvem
```

Essa estratégia reduz significativamente o risco de perda de informações.

---

# Frequência dos backups

A frequência depende da importância da aplicação.

| Tipo de sistema | Frequência recomendada |
|-----------------|-----------------------|
| Blog pessoal | Semanal |
| Site institucional | Diária |
| Loja virtual | Diária ou a cada poucas horas |
| Banco de dados crítico | Diversas vezes ao dia |

Quanto maior a frequência de alterações, menor deve ser o intervalo entre os backups.

---

# Testando os backups

Criar um backup não garante que ele poderá ser restaurado.

É importante realizar testes periódicos para verificar:

- Integridade dos arquivos;
- Integridade do banco de dados;
- Compatibilidade da restauração;
- Tempo necessário para recuperar o ambiente.

---

# Boas práticas

- Automatize backups sempre que possível.
- Faça backup antes de atualizações importantes.
- Armazene cópias em locais diferentes.
- Proteja os arquivos de backup com permissões adequadas.
- Monitore o espaço em disco utilizado pelos backups.
- Teste regularmente o processo de restauração.
- Nunca mantenha apenas uma única cópia dos dados.

---

# Resumo

Backups são fundamentais para garantir a continuidade de qualquer serviço hospedado. Em hospedagens compartilhadas, o processo normalmente é realizado pelo painel de controle ou por ferramentas disponibilizadas pelo provedor. Já em VPS, o administrador possui maior controle e pode automatizar todo o processo utilizando comandos, scripts e agendamentos. Independentemente do ambiente, manter backups atualizados e testados é uma das principais responsabilidades de qualquer profissional que trabalha com hospedagem e administração de servidores.
