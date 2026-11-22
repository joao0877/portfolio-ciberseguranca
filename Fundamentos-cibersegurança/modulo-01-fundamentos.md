# Módulo 1 — Fundamentos da Cibersegurança

Antes de tocar em qualquer ferramenta, é preciso entender o "campo de jogo".
Este módulo é só teoria, mas é a base de tudo.

**Neste módulo:** [1.1](#11-o-que-é-cibersegurança-e-segurança-da-informação) ·
[1.2](#12-a-tríade-cia-os-três-pilares) · [1.3](#13-ameaça-vulnerabilidade-e-risco) ·
[1.4](#14-tipos-de-ataque-mais-comuns) · [1.5](#15-tipos-de-hackers-e-ética-profissional) ·
[1.6](#16-leis-e-responsabilidade-no-brasil) · [Revisão](#revisão-rápida) ·
[Exercícios](#exercícios) · [Gabarito](#gabarito-comentado)

---

## 1.1 O que é cibersegurança e segurança da informação

- **Segurança da informação:** práticas para proteger a informação **em qualquer meio** —
  computador, papel, conversa, a cabeça de uma pessoa.
- **Cibersegurança:** a parte que trata especificamente do **mundo digital** — computadores,
  celulares, redes, internet, sistemas.

**Analogia da casa:** segurança da informação é cuidar de tudo (trancar a porta, não deixar
documentos na mesa do bar). Cibersegurança é cuidar da parte eletrônica (câmera, alarme,
senha do Wi-Fi).

**Por que importa?** Hoje quase tudo de valor é digital: dinheiro, conversas, fotos, dados de
clientes, prontuários. Se alguém mal-intencionado acessa, altera ou destrói isso, o estrago é real.

## 1.2 A tríade CIA: os três pilares

(Nada a ver com a agência americana: é a sigla, em inglês, de *Confidentiality, Integrity, Availability*.)

| Pilar | Ideia | Exemplo | Quando é quebrado |
|---|---|---|---|
| **C**onfidencialidade | Só quem tem permissão vê | Só você sabe a senha do seu e-mail | Alguém espia sua senha |
| **I**ntegridade | A informação não muda sem autorização | O saldo do banco é o valor real | Um invasor troca "100" por "100000" |
| **D**isponibilidade | Está acessível quando se precisa | O site do banco abre na hora de pagar | Um ataque derruba o site |

Todo ataque tenta quebrar **pelo menos um** pilar. Toda defesa existe para proteger **um** deles.

> 🪑 **Figura mental:** um banquinho de três pernas chamado "Informação Segura".
> Tire uma perna e ele cai.

### 📝 Anote no seu caderno
- Segurança da Informação = proteger a informação em qualquer meio.
- Cibersegurança = proteger a informação no meio digital.
- **Confidencialidade** = só quem pode, vê. **Integridade** = continua correta. **Disponibilidade** = acessível quando precisa.
- Todo ataque quebra pelo menos um pilar.

## 1.3 Ameaça, vulnerabilidade e risco

| Termo | Significado | Exemplo |
|---|---|---|
| **Vulnerabilidade** | Fraqueza, brecha | Janela destrancada; senha `123456`; programa desatualizado |
| **Ameaça** | Perigo que pode explorar a fraqueza | O ladrão na rua; o hacker; o vírus |
| **Risco** | Chance de a ameaça explorar a vulnerabilidade + tamanho do estrago | Alto risco de roubo |

```
Risco = Probabilidade (de acontecer) × Impacto (do estrago)
```

**Exemplo completo:** janela destrancada (vulnerabilidade) + ladrão rondando (ameaça) =
risco alto. Se você tranca a janela, elimina a vulnerabilidade e o risco despenca, mesmo
com o ladrão por perto.

Nem toda vulnerabilidade vira problema: uma janela destrancada num 20º andar sem acesso tem
risco baixo. Na prática, **prioriza-se** consertar primeiro as brechas de maior risco.

### 📝 Anote no seu caderno
- Vulnerabilidade = fraqueza (ex.: senha fraca).
- Ameaça = perigo que pode explorar a brecha (ex.: invasor, vírus).
- Risco = Probabilidade × Impacto.
- Resumo: a **ameaça explora a vulnerabilidade**, gerando um **risco**.

## 1.4 Tipos de ataque mais comuns

Visão geral (cada um será estudado em detalhe mais à frente):

- **Malware** — programa malicioso. Inclui:
  - *vírus*; *worm* (se espalha sozinho); *trojan* (disfarçado de programa bom);
  - *ransomware* (sequestra arquivos e pede resgate); *spyware* (espiona).
- **Phishing** — a pessoa é enganada para entregar dados ou clicar em algo perigoso, geralmente por e-mail ou mensagem falsa.
- **Engenharia social** — manipulação psicológica para enganar pessoas (o phishing é um tipo dela).
- **Negação de serviço (DoS/DDoS)** — sobrecarrega o sistema até ele parar. Ataca a **disponibilidade**.
- **Ataque a senhas** — força bruta (tentativa e erro) ou listas prontas.
- **Ataques web** — exploram falhas em sites (SQL Injection, XSS).
- **Interceptação (man-in-the-middle)** — o atacante se coloca "no meio" da comunicação para espionar ou alterar dados.

## 1.5 Tipos de hackers e ética profissional

"Hacker", originalmente, é quem tem **profundo conhecimento técnico e curiosidade** para entender
como as coisas funcionam por dentro. O que define o lado certo ou errado é **o que a pessoa faz**
com esse conhecimento. Os termos vêm do faroeste: o mocinho de chapéu branco, o bandido de preto.

| Tipo | Chapéu | O que faz |
|---|---|---|
| **White Hat** | Branco | Hacker ético. Testa sistemas **com autorização** para achar e corrigir falhas. |
| **Black Hat** | Preto | Criminoso. Invade sem autorização para roubar, destruir ou lucrar. |
| **Gray Hat** | Cinza | Meio-termo: às vezes age sem autorização, sem intenção claramente criminosa. Ainda assim pode estar cometendo crime. |

**Áreas de atuação:**
- 🔴 **Red Team** — ataca (simula o inimigo) para testar as defesas.
- 🔵 **Blue Team** — defende, monitora e responde a incidentes.
- 🟣 **Purple Team** — une os dois para melhorar a defesa.

> 🚨 **Atenção / Risco:** ter o conhecimento não dá o direito de usá-lo em qualquer sistema.
> A diferença entre um profissional respeitado e um criminoso preso é **autorização**.
> Antes de qualquer teste, pergunte: *"este sistema é meu, ou tenho permissão por escrito para testá-lo?"*
> Se a resposta não for um "sim" claro, **pare**.

### 📝 Anote no seu caderno
- Hacker = domínio técnico profundo (não é sinônimo de criminoso).
- White Hat = ético, com autorização. Black Hat = criminoso. Gray Hat = meio-termo.
- Red Team ataca (para testar). Blue Team defende. Purple Team une os dois.
- **Regra de ouro: sem autorização, não se toca.**

## 1.6 Leis e responsabilidade no Brasil

| Lei | Apelido | Em resumo |
|---|---|---|
| **12.737/2012** | Lei Carolina Dieckmann | Crime invadir dispositivo de informática alheio para obter, adulterar ou destruir dados sem autorização |
| **12.965/2014** | Marco Civil da Internet | Regras gerais para o uso da internet no Brasil |
| **13.709/2018** | LGPD | Como dados pessoais devem ser tratados e protegidos; vazar dados tem consequências sérias |

Na prática: você vai montar um **laboratório próprio** para praticar sem risco legal.
Nunca aponte uma ferramenta de ataque para site, Wi-Fi ou computador que não seja seu ou que
você não tenha permissão expressa para testar.

---

## Revisão rápida

1. **Quais são os três pilares da tríade CIA?**
   *R:* Confidencialidade (só quem pode, vê), Integridade (a informação não é alterada indevidamente) e Disponibilidade (acessível quando se precisa).
2. **Qual a diferença entre vulnerabilidade, ameaça e risco?**
   *R:* Vulnerabilidade é a fraqueza; ameaça é o perigo que pode explorá-la; risco é a combinação dos dois (Probabilidade × Impacto).
3. **O que diferencia um White Hat de um Black Hat?**
   *R:* A autorização e a intenção. O White Hat age com permissão para proteger; o Black Hat age sem permissão para prejudicar ou lucrar ilegalmente.
4. **Um antivírus que impede um vírus de apagar seus arquivos protege qual pilar?**
   *R:* Principalmente a Integridade (impede alteração/destruição indevida) e também a Disponibilidade (mantém os arquivos acessíveis).

## Exercícios

1. Explique, com um exemplo do seu dia a dia, cada pilar da tríade CIA.
2. Dê um exemplo de vulnerabilidade, uma ameaça que a exploraria e o risco resultante (pode ser do mundo físico).
3. Um site de notícias fica fora do ar depois de receber milhões de acessos falsos ao mesmo tempo. Qual pilar foi atacado? Que tipo de ataque é esse?
4. Uma pessoa encontra uma falha num site e avisa a empresa sem pedir nada em troca, mas testou a falha sem autorização. Que "chapéu" é esse?
5. Pesquise e escreva uma frase sobre o que a Lei Carolina Dieckmann proíbe.

## Gabarito comentado

1. **Confidencialidade:** a senha do meu Instagram, que só eu sei. **Integridade:** o valor do meu Pix chega exatamente igual ao que enviei. **Disponibilidade:** o app do banco abre quando preciso pagar uma conta.
2. **Vulnerabilidade:** deixar o carro destrancado. **Ameaça:** um ladrão de carros no bairro. **Risco:** alta chance de furto e prejuízo grande = risco alto.
3. Foi atacada a **Disponibilidade**. É uma **negação de serviço distribuída (DDoS)**: muitos acessos falsos simultâneos sobrecarregam e derrubam o serviço.
4. **Gray Hat.** A intenção não foi criminosa (avisou, não pediu nada), mas ele testou sem autorização, o que ainda pode configurar crime.
5. A lei criminaliza **invadir o dispositivo informático de outra pessoa, sem autorização, para obter, adulterar ou destruir dados**.

---

⬅️ [Voltar ao índice](README.md) · ➡️ [Módulo 2](modulo-02-informatica-kali.md)
