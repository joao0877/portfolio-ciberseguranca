# Módulo 2 — Informática Básica e o Kali Linux

Agora a mão vai na massa. Antes das ferramentas de segurança, você precisa se sentir em casa
dentro do computador e do Kali.

**Neste módulo:** [2.1](#21-como-um-computador-funciona-o-essencial) ·
[2.2](#22-o-que-é-um-sistema-operacional) · [2.3](#23-o-que-é-o-kali-linux-e-por-que-usá-lo) ·
[2.4](#24-a-interface-gráfica) · [2.5](#25-o-terminal-por-que-ele-é-tão-importante) ·
[2.6](#26-seus-primeiríssimos-comandos) · [2.7](#27-pedindo-ajuda) ·
[2.8](#28-instalando-atualizando-e-removendo-programas) · [Revisão](#revisão-rápida) ·
[Exercícios](#exercícios) · [Gabarito](#gabarito-comentado)

---

## 2.1 Como um computador funciona (o essencial)

| Peça | Analogia | Função |
|---|---|---|
| **Processador (CPU)** | Cérebro | Faz os cálculos e executa as instruções dos programas |
| **Memória RAM** | Mesa de trabalho | Guarda o que está em uso agora. Rápida, mas **apaga ao desligar**. Dados sensíveis às vezes ficam nela |
| **Disco (HD/SSD)** | Armário | Guarda arquivos e programas **de forma permanente** |
| **Placa de rede** | Porta de entrada | Conecta à rede/internet (cabo ou Wi-Fi). Toda comunicação passa por ela |
| Placa de vídeo, fonte, placa-mãe | — | Completam o conjunto, menos relevantes para o foco |

A informação vive em **três estados**: no **disco** (parada), na **RAM** (em uso) e **em trânsito**
pela rede. A cibersegurança protege a informação nos três.

## 2.2 O que é um sistema operacional

O **sistema operacional (SO)** é o programa principal que faz o computador funcionar e serve de
ponte entre você, os outros programas e o hardware. Exemplos: Windows, macOS e Linux.

O **Linux** é livre e de código aberto (qualquer um pode ver e modificar). Vem em vários "sabores",
as **distribuições (distros)**: Ubuntu, Debian, Fedora e o **Kali Linux**. Todas compartilham o
mesmo "coração" (o **kernel** Linux), mas mudam os programas instalados e o visual.

## 2.3 O que é o Kali Linux e por que usá-lo

Distribuição baseada no **Debian**, criada e mantida pela **Offensive Security**, focada em testes
de segurança e pentest. Já vem com centenas de ferramentas (Nmap, Wireshark, Metasploit...), o que
poupa muito tempo de configuração. Por isso é o padrão para estudo.

> 🚨 **Atenção / Risco:** o Kali é uma ferramenta poderosa, feita para profissionais. **Não** é o
> sistema ideal para o dia a dia (navegar, assistir vídeo), e muita coisa nele roda como administrador.
> Use-o para estudar segurança e, de preferência, **dentro de uma máquina virtual**. Se algo der
> errado, seu computador "de verdade" não é afetado.

## 2.4 A interface gráfica

O Kali geralmente usa o ambiente **Xfce** (leve e rápido). O que você vai usar sempre:

- **Barra superior** — menu de aplicativos, relógio e atalhos.
- **Menu de aplicativos** — ferramentas agrupadas por categoria (ex.: *Information Gathering*, *Web Application Analysis*).
- **Terminal** — o programa mais importante: uma janela preta onde se digitam comandos.
- **Gerenciador de arquivos** — equivalente ao "Explorador de Arquivos" do Windows.

💡 Deixe sempre um terminal aberto enquanto estuda.

## 2.5 O terminal: por que ele é tão importante

O **terminal** (ou **CLI**, *Command Line Interface*) é onde você digita comandos em texto e o
sistema responde em texto. Parece assustador, mas é a forma mais **poderosa, rápida e precisa** de
usar o Linux. Quase todas as ferramentas de segurança são usadas por ali.

Comparação: copiar 500 arquivos com um critério específico na interface gráfica = centenas de
cliques. No terminal = um comando. E comandos podem ser guardados em **scripts** e repetidos
automaticamente.

O **prompt** é o terminal dizendo "estou pronto":

```
┌──(kali㉿kali)-[~]
└─$
```

- `kali` (primeiro) = seu **usuário**; `kali` (segundo) = nome da **máquina**.
- `[~]` = pasta onde você está (`~` é a sua pasta pessoal).
- `$` = usuário comum. `#` indicaria **administrador**.

## 2.6 Seus primeiríssimos comandos

Cada comando é uma palavra digitada e confirmada com **Enter**.

```bash
pwd         # onde estou? (Print Working Directory)
ls          # lista arquivos e pastas (LiSt)
date        # data e hora atuais
whoami      # meu nome de usuário
clear       # limpa a tela
```

Um comando é como um **verbo**: `ls` = "liste", `pwd` = "onde estou?", `whoami` = "quem sou eu?".
A maioria é abreviação de uma palavra em inglês, o que ajuda a lembrar.

**Opções** (*flags*) mudam o comportamento e costumam começar com `-`:

```bash
ls              # simples
ls -l -a        # detalhes (long) + arquivos ocultos (all)
ls -la          # opções juntadas
```

A saída de `ls -la` mostra permissões, dono, tamanho e data (entendidos no Módulo 3).

## 2.7 Pedindo ajuda

Ninguém decora todos os comandos. O profissional é quem **sabe procurar rápido**.

```bash
man ls          # manual completo (sai com q)
ls --help       # ajuda rápida e resumida
whatis ls       # o que o comando faz, em uma linha
```

💡 **Dica:** dentro do `man`, use as setas para rolar, `/palavra` para buscar e `q` para sair.
Travou? Tente `q`; se não funcionar, `Ctrl + C` cancela o que está rodando.

## 2.8 Instalando, atualizando e removendo programas

No Linux você não baixa "instaladores" de sites. Os programas vêm de **repositórios** (uma loja
oficial) e são gerenciados por um **gerenciador de pacotes**. No Kali/Debian, o **APT**.

Mexer no sistema exige poder de administrador, então se coloca `sudo` na frente:

```bash
sudo apt update            # atualiza a LISTA de programas disponíveis (faça primeiro)
sudo apt upgrade           # instala as atualizações dos programas já instalados
sudo apt install nano      # instala um programa novo
sudo apt remove nano       # remove um programa
apt search wireshark       # procura um programa pelo nome
```

> 🚨 **Atenção / Risco:** rode `sudo apt update` **antes** de instalar qualquer coisa, senão o
> sistema pode tentar baixar uma versão que não existe mais e dar erro. Cuidado com `apt remove`:
> removendo um programa importante por engano, você pode quebrar parte do sistema. Leia o que o
> terminal pergunta antes de confirmar.

### 📝 Anote no seu caderno
- **Hardware:** CPU (processa), RAM (temporária, apaga ao desligar), Disco (permanente), Placa de rede (conecta).
- **SO** = sistema operacional. **Distro** = sabor do Linux. **Kali** = distro focada em segurança.
- **Terminal / CLI** = janela de comandos em texto. É onde tudo acontece.
- Comandos iniciais: `pwd` (onde estou) · `ls` (listar) · `whoami` (quem sou) · `clear` (limpar) · `date` (data/hora) · `ls -la` (detalhes + ocultos).
- Ajuda: `man comando` (sai com `q`) · `comando --help` · `whatis comando`.
- APT: `sudo apt update` (lista) · `sudo apt upgrade` (programas) · `sudo apt install nome` · `sudo apt remove nome`.

---

## Revisão rápida

1. **Qual a diferença entre RAM e disco (HD/SSD)?**
   *R:* A RAM guarda o que está em uso agora e apaga ao desligar (temporária); o disco guarda os arquivos de forma permanente.
2. **O que é uma distribuição (distro) Linux? Cite duas.**
   *R:* Um "sabor" do Linux, com conjunto próprio de programas e visual. Ex.: Kali e Ubuntu (também Debian, Fedora).
3. **Para que serve `sudo apt update` e por que fazê-lo antes de instalar?**
   *R:* Atualiza a lista de programas dos repositórios. Feito antes, evita erros de versão desatualizada.
4. **Você esqueceu como um comando funciona. O que digita?**
   *R:* `man comando` (manual completo) ou `comando --help` (ajuda resumida).

## Exercícios

1. Abra o terminal e descubra em que pasta você está, quem é o seu usuário e que dia é hoje. Anote os três comandos usados.
2. Liste o conteúdo da sua pasta pessoal mostrando arquivos ocultos. Quantos itens ocultos apareceram?
3. Abra o manual do `ls`, procure o que faz a opção `-h` e depois saia do manual.
4. Atualize a lista de pacotes do seu Kali e, em seguida, instale o editor `nano`. Confirme abrindo-o com `nano` (saia com `Ctrl + X`).
5. **Desafio:** descubra, usando `--help` ou `man`, o que faz o comando `uname -a` e anote o que ele mostrou sobre o seu sistema.

## Gabarito comentado

1. `pwd` (pasta atual), `whoami` (usuário), `date` (data/hora).
2. `ls -la` (ou `ls -a`). Itens ocultos são os que começam com ponto, como `.bashrc` e `.config`. A quantidade varia por máquina.
3. `man ls`, depois `/-h` e Enter para buscar. A opção `-h` mostra tamanhos "legíveis para humanos" (ex.: 4K, 2M). Saia com `q`.
4. `sudo apt update` e depois `sudo apt install nano`. Ao abrir o `nano`, o editor aparece; `Ctrl + X` fecha.
5. `uname -a` mostra nome do kernel, nome da máquina, versão do kernel e arquitetura (ex.: `x86_64`). Útil para saber exatamente qual sistema você está usando.

---

⬅️ [Módulo 1](modulo-01-fundamentos.md) · [Índice](README.md) · ➡️ [Módulo 3](modulo-03-linux-do-zero.md)
