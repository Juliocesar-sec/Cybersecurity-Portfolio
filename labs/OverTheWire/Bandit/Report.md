# OverTheWire Bandit – Relatório de Resolução

## 📌 Visão geral

Este documento registra a resolução progressiva dos níveis iniciais do wargame **OverTheWire Bandit**, focado em conceitos fundamentais de Linux, manipulação de arquivos, busca e decodificação de dados.

---

## 🧠 Ferramentas utilizadas

* SSH
* ls / cd / cat
* grep
* find
* sort / uniq
* strings
* base64

---

## 🔐 Level 0 → 1

![Level 0 → 1](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/3838ce94eafbac104adbd57d64c9b689d85e1076/labs/OverTheWire/Bandit/Screenshot/Screenshot_0.png)

### Objetivo

Conectar via SSH ao servidor do jogo.

### Conexão

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

### Credenciais

* Usuário: bandit0
* Senha: bandit0

### Aprendizado

* Uso básico de SSH
* Conexão remota em porta não padrão

---

## 📁 Level 1 → 2

### Objetivo

Acessar arquivo com nome especial (`-`).

### Solução

```bash
cat ./-
```

### Aprendizado

* Arquivos com nomes interpretados como argumentos
* Uso de `./` para evitar ambiguidades

---

## 📁 Level 2 → 3

### Objetivo

Arquivo com espaços no nome.

### Solução

```bash
cat "--spaces in this filename--"
```

### Aprendizado

* Escape de espaços
* Uso de aspas em nomes de arquivos

---

## 📂 Level 3 → 4

### Objetivo

Encontrar arquivo oculto na pasta `inhere`.

### Solução

```bash
cd inhere
ls -la
cat .hidden
```

### Aprendizado

* Arquivos ocultos (prefixo ".")
* Uso de `ls -la`

---

## 📄 Level 4 → 5

### Objetivo

Encontrar único arquivo legível por humanos.

### Solução

```bash
cd inhere
file ./*
cat <arquivo_ASCII>
```

### Aprendizado

* Identificação de tipos de arquivos
* Uso do comando `file`

---

## 📏 Level 5 → 6

![Level 5 → 6](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/44f9d7dbc4c156b15354373ebdab9b65bc2890d8/labs/OverTheWire/Bandit/Screenshot/Screenshot_5.png)

### Objetivo

Arquivo com:

* 1033 bytes
* legível
* não executável

### Solução

```bash
find . -type f -size 1033c ! -executable
cat <arquivo_encontrado>
```

### Aprendizado

* Uso avançado do `find`
* Filtragem por tamanho e permissões

---

## 🔍 Level 6 → 7

### Objetivo

Arquivo em qualquer lugar do sistema com:

* usuário bandit7
* grupo bandit6
* 33 bytes

### Solução

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat <arquivo>
```

### Aprendizado

* Busca em todo sistema
* Redirecionamento de erros (`2>/dev/null`)

---

## 🔎 Level 7 → 8

### Objetivo

Encontrar palavra "millionth" em data.txt

### Solução

```bash
grep "millionth" data.txt
```

### Aprendizado

* Filtragem de texto com `grep`

---

## 🔁 Level 8 → 9

### Objetivo

Encontrar linha única em arquivo com duplicatas

### Solução

```bash
sort data.txt | uniq -u
```

### Aprendizado

* Ordenação de dados
* Filtragem de ocorrências únicas

---

## 🧩 Level 9 → 10

### Objetivo

Encontrar string legível precedida por "===" em arquivo binário

### Solução

```bash
strings data.txt | grep "="
```

### Aprendizado

* Extração de strings de binários
* Filtragem com grep

---

## 🔐 Level 10 → 11

### Objetivo

Decodificar conteúdo em Base64 presente no arquivo `data.txt`.

### Solução

```bash
base64 -d data.txt
```

### Aprendizado

* Decodificação de dados em Base64
* Reconhecimento de formatos de encoding comuns

---

## 🔐 Level 11 → 12


![Level 10 → 11](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/3838ce94eafbac104adbd57d64c9b689d85e1076/labs/OverTheWire/Bandit/Screenshot/Screenshot_11.png)


### Objetivo

O conteúdo do arquivo `data.txt` está codificado usando ROT13 (cifra de César com deslocamento 13) aplicada a letras maiúsculas e minúsculas.

### Solução

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

