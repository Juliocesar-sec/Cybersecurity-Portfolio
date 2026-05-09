# OverTheWire Bandit – Relatório de Resolução

 📌 **Visão geral**

Este documento registra a resolução progressiva dos níveis iniciais do wargame **OverTheWire Bandit**, focado em conceitos fundamentais de Linux, manipulação de arquivos, busca e decodificação de dados.


**Ferramentas utilizadas**

* SSH
* ls / cd / cat
* grep
* find
* sort / uniq
* strings
* base64

---

##  Level 0 → 1

![Level 0 → 1](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/3838ce94eafbac104adbd57d64c9b689d85e1076/labs/OverTheWire/Bandit/Screenshot/Screenshot_0.png)

**Objetivo**

```
(The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.)
```
Conectar via SSH ao servidor do jogo.

**Conexão**

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

**Credenciais**

* Usuário: bandit0
* Senha: bandit0

**Aprendizado**

* Uso básico de SSH
* Conexão remota em porta não padrão

---

## Level 1 → 2

**Objetivo**

```
(The password for the next level is stored in a file called - located in the home directory)
```
Acessar arquivo com nome especial (`-`).

**Solução**

```bash
cat ./-
```

**Aprendizado**

* Arquivos com nomes interpretados como argumentos
* Uso de `./` para evitar ambiguidades

---

##  Level 2 → 3

**Objetivo**

```
(The password for the next level is stored in a file called --spaces in this filename-- located in the home directory)
```

 ler o arquvio `--spaces in this filename--`

**Solução**

```bash
cat "--spaces in this filename--"
```

**Aprendizado**

* Escape de espaços
* Uso de aspas em nomes de arquivos

---

## Level 3 → 4

**Objetivo**

```
(The password for the next level is stored in a hidden file in the inhere directory.)
```
Encontrar arquivo oculto na pasta `inhere`.

**Solução**

```bash
cd inhere
ls -la
cat .hidden
```

**Aprendizado**

* Arquivos ocultos (prefixo ".")
* Uso de `ls -la`

---

##  Level 4 → 5

**Objetivo**

```
(The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.)
```
Encontrar único arquivo legível por humanos.

**Solução**

```bash
cd inhere
file ./*
cat <arquivo_ASCII>
```

**Aprendizado**

* Identificação de tipos de arquivos
* Uso do comando `file`

---

##  Level 5 → 6

![Level 5 → 6](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/44f9d7dbc4c156b15354373ebdab9b65bc2890d8/labs/OverTheWire/Bandit/Screenshot/Screenshot_5.png)

**Objetivo**

```
(The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable)
```
Arquivo com:
```
* 1033 bytes
* legível
* não executável
```

**Solução**

```bash
find . -type f -size 1033c ! -executable
cat <arquivo_encontrado>
```

**Aprendizado**

* Uso avançado do `find`
* Filtragem por tamanho e permissões

---

##  Level 6 → 7

**Objetivo**

```
(The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size)
```
Arquivo em qualquer lugar do sistema com:
```
* usuário bandit7
* grupo bandit6
* 33 bytes
```
**Solução**

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat <arquivo>
```

**Aprendizado**

* Busca em todo sistema
* Redirecionamento de erros (`2>/dev/null`)

---

##  Level 7 → 8

**Objetivo**

```
(The password for the next level is stored in the file data.txt next to the word millionth)
```
Encontrar palavra "millionth" em data.txt

**Solução**

```bash
grep "millionth" data.txt
```

**Aprendizado**

* Filtragem de texto com `grep`

---

##  Level 8 → 9

**Objetivo**

```
(The password for the next level is stored in the file data.txt and is the only line of text that occurs only once)
```
Encontrar linha única em arquivo com duplicatas

**Solução**

```bash
sort data.txt | uniq -u
```

**Aprendizado**

* Ordenação de dados
* Filtragem de ocorrências únicas

---

##  Level 9 → 10

**Objetivo**

```
(The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.)
```

Encontrar string legível precedida por "===" em arquivo binário

**Solução**

```bash
strings data.txt | grep "="
```

**Aprendizado**

* Extração de strings de binários
* Filtragem com grep

---

##  Level 10 → 11

**Objetivo**

```
(The password for the next level is stored in the file data.txt, which contains base64 encoded data)
```

Decodificar conteúdo em Base64 presente no arquivo `data.txt`.

**Solução**

```bash
base64 -d data.txt
```

**Aprendizado**

* Decodificação de dados em Base64
* Reconhecimento de formatos de encoding comuns

 ---

##  Level 11 → 12


![Level 11 → 12](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/3838ce94eafbac104adbd57d64c9b689d85e1076/labs/OverTheWire/Bandit/Screenshot/Screenshot_11.png)


**Objetivo**

```
(The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions)
```

O conteúdo do arquivo `data.txt` está codificado usando ROT13 (cifra de César com deslocamento 13) aplicada a letras maiúsculas e minúsculas.

**Solução**

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

---

##  Level 12 → 13

![Level 12 → 13](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/5ea7e3ee9d1c38d42c0073fc32a5879e401ec412/labs/OverTheWire/Bandit/Screenshot/Screenshot_12.png)

**Objetivo**

```
(The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!))
```

O arquivo `data.txt` estava comprimido múltiplas vezes em diferentes formatos (gzip, bzip2 e tar), exigindo extração encadeada.

**Solução (resumo do processo)**

```bash
mktemp -d
cp data.txt /tmp/
cd /tmp/<dir>
file data.txt
mv data.txt data.gz
gunzip data.gz
file data
bzip2 -d data.bz2
tar -xf data.tar
```
(Repetido até obter o arquivo final legível)

```
cat data.txt
```

**Aprendizado**

Identificação de múltiplos formatos de compressão
Uso de file para inspeção
Extração encadeada de arquivos

---

##  Level 13 → 14

**Objetivo**

```
(The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.)
```

Acessar o próximo nível usando uma chave privada SSH fornecida.

**Solução**
```
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

**Aprendizado**

Autenticação via chave privada SSH
Permissões de arquivos .pem/.key

--- 

##  Level 14 → 15

**Objetivo**

```
(The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.)
```

Enviar a senha atual para uma porta local via conexão SSL.

**Solução**
```
echo "PASSWORD_ATUAL" | openssl s_client -connect localhost:30001 -quiet
```

**Aprendizado**

Comunicação via TLS/SSL com openssl
Interação com serviços locais por porta

---
##  Level 15 → 16

![Level 15 → 16](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/5ea7e3ee9d1c38d42c0073fc32a5879e401ec412/labs/OverTheWire/Bandit/Screenshot/Screenshot_16.png)

**Objetivo**

```
(The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.)
```

Encontrar portas abertas entre 31000–32000 e identificar o serviço correto TLS.

**Solução**

```
nmap -p 31000-32000 localhost
```

Testando portas:
```
echo "PASSWORD_ATUAL" | openssl s_client -connect localhost:<PORTA> -quiet
```
Porta correta retornou uma chave privada RSA.

**Aprendizado**

Escaneamento de portas com nmap
Identificação de serviços SSL/TLS
Análise de respostas de handshake

---

##  Level 16 → 17

**Objetivo**

```
(The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.)

Comparar dois arquivos e encontrar a senha alterada.
```

**Solução**

```
diff passwords.new passwords.old
```

Resultado:

```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

**Aprendizado**
Comparação de arquivos com diff
Identificação de alterações pontuais

---

##  Level 17 → 18

**Objetivo**

Acessar o servidor SSH, mas a sessão fecha automaticamente. A solução envolve executar comandos diretamente.

**Solução**
```
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```
Senha obtida:
```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

**Aprendizado**

Execução remota de comandos via SSH
Contorno de shells restritas

---

##  Level 18 → 19

**Objetivo**

```
(There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19)

```

Ao tentar login, o servidor encerra a sessão imediatamente.

**Solução**

Uso de execução direta de comando:
```
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

**Aprendizado**

Entendimento de shells restritas
Execução não interativa via SSH

---
##  Level 19 → 20

![Level 18 → 19](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/5ea7e3ee9d1c38d42c0073fc32a5879e401ec412/labs/OverTheWire/Bandit/Screenshot/Screenshot_19.png)

**Objetivo**

```
(The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.)
```

Usar um binário setuid para executar comandos como outro usuário (bandit20) e obter a senha em /etc/bandit_pass.

Análise do binário
```
./bandit20-do
```
Mostra:
```
Run a command as another user.
Example: ./bandit20-do whoami
```
Verificação de privilégios:
```
./bandit20-do id
```
Resultado:
```
uid=11019(bandit19) euid=11020(bandit20)
Tentativa inicial
./bandit20-do cat /etc/bandit_pass/bandiit20
```

Erro de caminho incorreto.

Solução correta
```
./bandit20-do cat /etc/bandit_pass/bandit20
```

**Aprendizado**

Uso de binários SUID
Diferença entre UID e EUID
Escalada de privilégio local controlada
Importância de caminhos corretos em Linux

---


