# Módulo 3 — Linux do Zero

Um dos módulos mais importantes. Dominar o Linux pelo terminal é o que separa quem "mexe" de
quem "sabe". Vá com calma e refaça tudo no Kali.

**Neste módulo:** [3.1](#31-a-árvore-de-diretórios) · [3.2](#32-navegando-entre-pastas) ·
[3.3](#33-criando-copiando-movendo-e-apagando) · [3.4](#34-lendo-o-conteúdo-de-arquivos) ·
[3.5](#35-procurando-arquivos-e-procurando-dentro-de-arquivos) ·
[3.6](#36-canos-pipes-e-redirecionamento) · [3.7](#37-usuários-permissões-e-o-poder-de-administrador) ·
[3.8](#38-processos-e-serviços) · [Revisão](#revisão-rápida) · [Exercícios](#exercícios) ·
[Gabarito](#gabarito-comentado)

---

## 3.1 A árvore de diretórios

No Windows existem "C:" e "D:". No Linux há **uma única raiz**, a barra `/`, e tudo fica pendurado
nela como galhos de uma árvore. Pastas são chamadas de **diretórios**.

| Diretório | Serve para |
|---|---|
| `/` | A raiz de tudo. Todo caminho começa aqui |
| `/home` | Pastas pessoais dos usuários (ex.: `/home/kali`) |
| `/root` | Pasta pessoal do administrador (usuário root) |
| `/etc` | Arquivos de configuração do sistema e dos programas |
| `/bin`, `/usr/bin` | Os programas (comandos) instalados |
| `/var` | Dados que mudam muito, como logs (`/var/log`) |
| `/tmp` | Arquivos temporários (apagados ao reiniciar) |
| `/dev` | Representações dos dispositivos (discos etc.) |

**Atalhos:** `~` = sua pasta pessoal (`/home/kali`) · `.` = pasta atual · `..` = pasta de cima.

## 3.2 Navegando entre pastas

`cd` (*Change Directory*) entra numa pasta. Combine com `pwd` (onde estou) e `ls` (o que tem aqui).

```bash
cd ~            # vai para sua pasta pessoal (cd sozinho também faz isso)
cd Downloads    # entra na pasta Downloads (dentro da atual)
cd ..           # sobe um nível
cd /etc         # vai direto pelo caminho completo
cd -            # volta para a pasta anterior
```

Dois jeitos de indicar um caminho:

- **Absoluto:** começa na raiz `/`. Ex.: `/home/kali/Downloads`. Funciona de qualquer lugar, é o endereço completo.
- **Relativo:** começa de onde você está. Ex.: estando em `/home/kali`, basta `Downloads`.

💡 **Dica:** use **Tab** para autocompletar. Digite `cd Dow` e aperte Tab: o terminal completa
`Downloads/` sozinho. Duas vezes Tab mostra todas as opções. Evita erro de digitação.

## 3.3 Criando, copiando, movendo e apagando

```bash
mkdir projeto                       # cria uma pasta (MaKe DIRectory)
touch anotacoes.txt                 # cria arquivo vazio (ou atualiza a data de um existente)
cp anotacoes.txt backup.txt         # copia origem para destino (CoPy)
mv backup.txt copia_seguranca.txt   # move ou renomeia (MoVe)
rm copia_seguranca.txt              # remove um arquivo (ReMove)
rm -r projeto                       # remove pasta e tudo dentro (-r = recursivo)
```

> 🚨 **Atenção / Risco:** no Linux o `rm` **não manda para a lixeira**: apaga de verdade, na hora,
> sem perguntar. Um erro clássico e perigoso é `rm -rf /` (apaga o sistema inteiro). **Nunca digite isso.**
> Antes de apagar com `-r`, confira com `ls` se está na pasta certa. Na dúvida, use `rm -i` (pergunta antes de cada remoção).

## 3.4 Lendo o conteúdo de arquivos

```bash
cat anotacoes.txt           # mostra tudo de uma vez (bom para arquivos pequenos)
less /var/log/syslog        # página por página (bom para arquivos grandes). Sai com q
head arquivo.txt            # só as primeiras 10 linhas
tail /var/log/syslog        # só as últimas 10 linhas (ótimo para o fim de um log)
tail -f /var/log/syslog     # acompanha o log em tempo real
```

O `tail -f` é muito usado em segurança para observar logs **ao vivo** enquanto algo acontece. Guarde ele.

## 3.5 Procurando arquivos e procurando dentro de arquivos

Duas tarefas diferentes, dois comandos diferentes:

```bash
find /home -name "*.txt"          # procura ARQUIVOS pelo nome, a partir de uma pasta
grep "senha" anotacoes.txt        # procura um TEXTO dentro de arquivos
grep -r -i "erro" /var/log        # recursivo (-r), ignorando maiúsc./minúsc. (-i)
```

O `grep` é uma das ferramentas mais valiosas do Linux. Em segurança, você o usa o tempo todo para
"pescar" uma linha específica no meio de milhares (ex.: achar um IP suspeito num log gigante).

## 3.6 Canos (pipes) e redirecionamento

Você pode ligar a **saída** de um comando na **entrada** de outro, montando uma linha de montagem.
Isso é o **pipe**, representado por `|`.

```bash
ps aux | grep firefox                          # lista processos e filtra só os "firefox"
cat /etc/passwd | wc -l                        # conta quantas linhas tem um arquivo
tail -n 20 /var/log/auth.log | grep "failed"   # últimas 20 linhas do log, só as com "failed"
```

Redirecionando a saída para um arquivo, em vez da tela:

```bash
ls -la > lista.txt      # > salva a saída (APAGA o que tinha antes)
date >> lista.txt       # >> adiciona ao final (sem apagar)
```

💡 **Dica:** pense no pipe como um cano de encanamento. `comando1 | comando2` = "pegue o resultado
do comando1 e entregue para o comando2 trabalhar". É a base da automação (Módulo 6).

## 3.7 Usuários, permissões e o poder de administrador

O Linux foi feito para vários usuários no mesmo computador, então controla **quem pode fazer o quê**.
O usuário especial **root** (administrador) pode tudo. Usuários comuns têm poderes limitados, e isso
é bom para a segurança: se um programa comum for invadido, o estrago fica contido.

```bash
sudo apt update     # roda um comando como administrador (Super User DO). Pede sua senha
sudo su             # vira root por completo (cuidado!). Volte ao normal com: exit
```

### Lendo as permissões

Cada arquivo e pasta diz quem pode **ler (r)**, **escrever (w)** e **executar (x)**. Ao rodar `ls -l`:

```
-rwxr-xr--  1 kali kali 1024 out 29 10:00 script.sh
```

```
-  rwx  r-x  r--
│   │    │    └── outros: só ler
│   │    └─────── grupo:  ler e executar
│   └──────────── dono:   ler, escrever e executar
└──────────────── tipo: "-" arquivo · "d" diretório
```

### Mudando permissões com `chmod` (*CHange MODe*)

```bash
chmod +x script.sh      # dá permissão de execução (necessária para rodar um script)
chmod -w arquivo.txt    # tira a permissão de escrita de todos
```

> 🚨 **Atenção / Risco:** o `sudo` é poder de verdade: serve para consertar ou destruir o sistema.
> Só use quando o comando realmente precisar (instalar programa, mexer em configuração do sistema).
> No dia a dia, trabalhe como usuário comum. **Nunca cole no terminal, como root, um comando que
> você não entende**: é assim que muita gente é enganada a se auto-sabotar.

## 3.8 Processos e serviços

Todo programa em execução é um **processo**. Ver e controlar processos é essencial para
diagnosticar problemas e detectar coisas suspeitas.

```bash
ps aux          # lista todos os processos em execução (uma "foto" do momento)
top             # mostra os processos ao vivo, atualizando. Sai com q
kill 1234       # encerra um processo pelo número (PID), que aparece no ps/top
```

**Serviços (daemons)** são processos que rodam em segundo plano o tempo todo, como o servidor de
SSH ou o de rede. No Kali são controlados pelo `systemctl`:

```bash
sudo systemctl status ssh       # vê o estado de um serviço
sudo systemctl start ssh        # inicia
sudo systemctl stop ssh         # para
sudo systemctl restart ssh      # reinicia
```

### 📝 Anote no seu caderno
- **Raiz = `/`.** `~` = pasta pessoal · `.` = pasta atual · `..` = pasta de cima.
- Pastas-chave: `/etc` (configurações), `/var/log` (logs), `/home` (usuários), `/root` (admin).
- Navegação: `cd` (entrar) · `pwd` (onde estou) · `ls` (listar). **Tab** autocompleta.
- Arquivos: `mkdir` (criar pasta) · `touch` (criar arquivo) · `cp` (copiar) · `mv` (mover/renomear) · `rm` (apagar, **sem lixeira!**) · `rm -r` (apaga pasta).
- Ler: `cat` (tudo) · `less` (por página, sai com `q`) · `head`/`tail` (início/fim) · `tail -f` (ao vivo).
- Buscar: `find -name` (arquivos pelo nome) · `grep "texto"` (texto dentro de arquivos).
- Pipe `|` liga a saída de um comando à entrada de outro. `>` salva em arquivo, `>>` adiciona ao fim.
- Permissões: `r` ler, `w` escrever, `x` executar. `chmod +x` dá execução. `sudo` = roda como admin.
- Processos: `ps aux` (lista) · `top` (ao vivo) · `kill PID` (encerra). `systemctl` controla serviços.

---

## Revisão rápida

1. **O que significam `~`, `.` e `..`?**
   *R:* `~` é a sua pasta pessoal; `.` é a pasta atual; `..` é a pasta de cima (um nível acima).
2. **Por que o `rm` é perigoso no Linux?**
   *R:* Porque apaga de verdade, imediatamente, sem mandar para a lixeira e, por padrão, sem perguntar.
3. **O que faz `cat auth.log | grep "failed"`?**
   *R:* Pega todo o conteúdo do `auth.log` e, pelo pipe, filtra mostrando só as linhas com "failed" (tentativas de login que falharam).
4. **Em `-rwxr-xr--`, o que o "grupo" pode fazer?**
   *R:* Ler e executar (`r-x`), mas não escrever.
5. **Qual comando mostra os processos em execução ao vivo?**
   *R:* `top` (ou `ps aux` para uma "foto" do momento).

## Exercícios

1. Crie na sua pasta pessoal uma pasta chamada `laboratorio`. Entre nela, crie dentro um arquivo `notas.txt` e confirme que ele está lá.
2. Escreva "primeira linha" dentro de `notas.txt` usando redirecionamento (`echo "primeira linha" > notas.txt`) e depois adicione "segunda linha" **sem apagar** a primeira. Mostre o conteúdo final.
3. Copie `notas.txt` para `notas_backup.txt`, depois renomeie o backup para `backup_final.txt`.
4. Procure, dentro de `/etc`, todos os arquivos cujo nome termina em `.conf` (dica: `find /etc -name "*.conf"`). O que significam esses arquivos?
5. Liste os processos em execução e filtre apenas os que contêm a palavra "bash".
6. **Desafio:** conte quantos usuários existem listados no arquivo `/etc/passwd` usando um pipe com `wc -l`.

## Gabarito comentado

1. `mkdir laboratorio`, `cd laboratorio`, `touch notas.txt`, `ls` (deve aparecer `notas.txt`).
2. `echo "primeira linha" > notas.txt` e depois `echo "segunda linha" >> notas.txt`. Mostre com `cat notas.txt`: devem aparecer as duas linhas. Repare: `>` cria/sobrescreve, `>>` acrescenta.
3. `cp notas.txt notas_backup.txt` e depois `mv notas_backup.txt backup_final.txt`.
4. `find /etc -name "*.conf"`. São **arquivos de configuração** de programas e serviços: definem como cada software se comporta. Em segurança, configurações mal feitas são uma fonte comum de vulnerabilidades.
5. `ps aux | grep bash`.
6. `cat /etc/passwd | wc -l` (ou `wc -l /etc/passwd`). Cada linha representa uma conta, incluindo contas de sistema, não só pessoas.

---

⬅️ [Módulo 2](modulo-02-informatica-kali.md) · [Índice](README.md)
