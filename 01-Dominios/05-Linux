# Comandos básicos do Linux (pastas e arquivos)

Esses são os comandos mais utilizados no dia a dia para navegar pelo sistema, criar arquivos, pesquisar informações e manipular diretórios. Todos podem ser executados sem privilégios de administrador (root), exceto onde indicado.

---

# Navegação

## `pwd`
Exibe o caminho completo do diretório atual.

```bash
pwd
```

Exemplo de saída:

```text
/home/higor/projetos
```

---

## `ls`
Lista os arquivos e diretórios do local atual.

```bash
ls
```

---

## `ls -la`
Lista todos os arquivos, incluindo os ocultos, com informações detalhadas.

```bash
ls -la
```

---

## `cd`
Entra em um diretório.

```bash
cd documentos/
```

---

## `cd ..`
Volta um nível na estrutura de diretórios.

```bash
cd ..
```

---

## `tree`
Exibe a estrutura de pastas em formato de árvore.

```bash
tree
```

Exemplo:

```text
projeto/
├── index.html
├── css
│   └── style.css
└── js
    └── script.js
```

> Caso o comando não exista, instale o pacote `tree` na distribuição Linux.

---

# Criando, copiando, movendo e removendo arquivos

## `mkdir`
Cria um diretório.

```bash
mkdir minha-pasta
```

---

## `mkdir -p`
Cria vários diretórios de uma única vez.

```bash
mkdir -p projetos/api/logs
```

---

## `touch`
Cria um arquivo vazio.

```bash
touch arquivo.txt
```

Também pode ser usado para atualizar a data de modificação de um arquivo existente.

---

## `cp`
Copia um arquivo.

```bash
cp origem.txt destino.txt
```

---

## `cp -r`
Copia uma pasta inteira.

```bash
cp -r pasta1/ pasta2/
```

A opção `-r` significa **recursivo**, copiando todos os arquivos e subpastas.

---

## `mv`
Move ou renomeia arquivos e diretórios.

Mover:

```bash
mv arquivo.txt documentos/
```

Renomear:

```bash
mv antigo.txt novo.txt
```

---

## `rm`
Remove um arquivo.

```bash
rm arquivo.txt
```

---

## `rm -r`
Remove um diretório e todo o seu conteúdo.

```bash
rm -r pasta/
```

> **Atenção:** esse comando remove tudo sem enviar para a lixeira.

---

## `rmdir`
Remove apenas diretórios vazios.

```bash
rmdir pasta-vazia
```

---

# Visualizando arquivos

## `cat`
Exibe todo o conteúdo do arquivo.

```bash
cat arquivo.txt
```

---

## `less`
Permite navegar pelo conteúdo de arquivos grandes.

```bash
less arquivo.txt
```

Pressione **Q** para sair.

---

## `head`
Mostra as primeiras linhas do arquivo.

```bash
head arquivo.txt
```

Por padrão exibe 10 linhas.

---

## `tail`
Mostra as últimas linhas do arquivo.

```bash
tail arquivo.txt
```

---

## `tail -f`
Acompanha um arquivo em tempo real.

```bash
tail -f log.txt
```

Muito utilizado para monitorar logs de aplicações e servidores.

---

# Compactação de arquivos

## Compactando em ZIP

```bash
zip -r projeto.zip pasta/
```

---

## Extraindo ZIP

```bash
unzip projeto.zip
```

Extrair para outro diretório:

```bash
unzip projeto.zip -d destino/
```

---

## Compactando em TAR.GZ

```bash
tar -czvf projeto.tar.gz pasta/
```

Parâmetros:

- `c` → cria o arquivo
- `z` → utiliza compressão Gzip
- `v` → modo detalhado
- `f` → nome do arquivo

---

## Extraindo TAR.GZ

```bash
tar -xzvf projeto.tar.gz
```

---

## Listando conteúdo sem extrair

```bash
tar -tzvf projeto.tar.gz
```

---

# Pesquisando arquivos e textos

## `find`
Localiza arquivos pelo nome.

```bash
find . -name "*.php"
```

O ponto (`.`) indica o diretório atual.

---

## `grep`
Procura um texto dentro de um arquivo.

```bash
grep "erro" arquivo.log
```

---

## `grep -r`
Pesquisa um texto em todos os arquivos de uma pasta.

```bash
grep -r "erro" logs/
```

---

## `which`
Mostra onde um programa está instalado.

```bash
which php
```

Exemplo:

```text
/usr/bin/php
```

---

# Permissões

## `chmod`
Altera as permissões de arquivos e diretórios.

Arquivo comum:

```bash
chmod 644 arquivo.txt
```

Diretório:

```bash
chmod 755 pasta/
```

Tabela rápida:

| Código | Permissões |
|---------|------------|
| 644 | rw-r--r-- |
| 755 | rwxr-xr-x |
| 777 | rwxrwxrwx (não recomendado) |

---

## `umask`
Exibe a máscara padrão de permissões.

```bash
umask
```

Essa máscara determina as permissões padrão para novos arquivos e diretórios.

> O comando `chown` normalmente exige permissões de administrador (root), por isso não costuma ser utilizado em hospedagens compartilhadas.

---

# Comandos de rede

## `ping`
Verifica se um host está respondendo na rede.

```bash
ping google.com
```

---

## `curl`
Realiza requisições HTTP.

Visualizar apenas os cabeçalhos da resposta:

```bash
curl -I https://google.com
```

Muito utilizado para testar APIs e sites.

---

## `wget`
Baixa arquivos pela linha de comando.

```bash
wget https://site.com/arquivo.zip
```

---

## `dig`
Consulta registros DNS detalhados.

```bash
dig google.com
```

Muito útil para verificar propagação de DNS.

---

## `nslookup`
Outra ferramenta para consultar registros DNS.

```bash
nslookup google.com
```

---

## `host`
Mostra informações rápidas sobre um domínio.

```bash
host google.com
```

---

# Resumo

Esses comandos fazem parte da rotina de qualquer profissional que administra servidores Linux, VPS ou hospedagens de sites. Dominar esses comandos facilita tarefas como gerenciamento de arquivos, análise de logs, pesquisa de informações, compactação de backups e diagnósticos de rede.
