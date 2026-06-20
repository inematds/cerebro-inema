<div align="center">

# 🧠 Cérebro INEMA

**Um segundo cérebro de IA com 3 cérebros — em português, roda no Linux.**

Obsidian + Claude Code · Local · Privado · Um comando

</div>

```
   Você joga o material cru
          │
          ▼
  ┌──────────────────────┐
  │   0-inbox/  (captura) │
  └──────────┬───────────┘
       /triagem roteia
   ┌───────┼───────────────┐
   ▼       ▼               ▼
1-projeto 2-self    3-conhecimento
(o que    (quem eu   (fatos do mundo,
 rolou)    sou/penso)  o que aprendi)
   └───────┴───────────────┘
              │  Claude Code lê este vault
              ▼
     IA que já sabe quem você é,
     o que você está fazendo,
     e o que você já aprendeu —
     antes de você digitar uma palavra.
```

---

## O que é

A maioria dos "segundos cérebros" trata tudo como um monte só de notas. O
**Cérebro INEMA** parte de uma distinção: existem **3 tipos de memória com
necessidades opostas**, e misturá-las incha o cérebro. Então ele separa em três:

| Cérebro | Guarda | Por quê |
|---|---|---|
| **1. Projeto** | o que rolou, decisões, estado | é episódico — muda todo dia, depois arquiva |
| **2. Self** | valores, pensamentos, dúvidas abertas | é identidade — muda devagar, é *seu* |
| **3. Conhecimento** | fatos, o que você aprendeu | é referência — só acumula, é consultável |

Cada um tem sua pasta, sua regra e sua skill. Os `[[wikilinks]]` cruzam entre
os três — separação dá ordem, links dão o cérebro pensando junto.

> A teoria completa (3 cérebros × 4 camadas, comparação com outros projetos)
> está no repositório de pesquisa [`2cerebrox`](https://github.com/inematds/2cerebrox).

## Como funciona

O truque é simples: **o Claude Code lê os arquivos do diretório no início de
toda sessão.** Se esses arquivos contêm seu contexto, ele já sabe tudo sobre
você antes de você digitar. O `CLAUDE.md` é o **roteador** — o mapa que diz
onde cada coisa mora e as regras de como agir.

Não é software com banco de dados escondido. **A memória é o seu sistema de
arquivos.** Por isso ele sobrevive ao hype: é só texto. Bane-se um modelo, vem
um melhor amanhã — você troca o motor e o cérebro fica.

## Início rápido

### Linux / macOS

```bash
git clone https://github.com/inematds/cerebro-inema.git
cd cerebro-inema
./setup.sh
```

O `setup.sh` cria o vault com a estrutura dos 3 cérebros, instala as skills, e
roda o `/setup-cerebro` para te entrevistar e personalizar o `CLAUDE.md`.

## As skills

| Skill | O que faz | Cérebro |
|---|---|---|
| `/setup-cerebro` | entrevista em texto livre e personaliza o vault | — |
| `/triagem` | roteia o que está no `0-inbox/` pro cérebro certo | 0 |
| `/daily` | começa o dia com contexto de projeto | 1 |
| `/tldr` | salva o resumo da sessão no lugar certo | 1/3 |
| `/nota` | destila uma fonte crua em nota-wiki válida | 3 |
| `/socratica` | a LLM te **questiona** em vez de concordar | 2 |

## As 4 camadas (opcional)

O core é **organização**. Por baixo, pode acoplar:

- **Formato** — [`kepano/obsidian-skills`](https://github.com/kepano/obsidian-skills):
  faz o Claude escrever `[[wikilinks]]`, `.base`, `.canvas` válidos. Recomendado
  para o cérebro 3. Ver [`docs/kepano-integracao.md`](docs/kepano-integracao.md).
- **Recuperação** — [`graphify`](https://github.com/safishamsi/graphify): grafo +
  MCP que o *agente* consulta. Opcional, melhor para código.
- **Visualização** — [`brain-map`](https://github.com/zubair-trabzada/brain-map):
  grafo que o *humano* explora. Opcional / demo.

## Ingestão de arquivos (cérebro 3)

Tem PDFs, planilhas, docs? O `/nota` e o processador Gemini extraem e destilam:

```bash
pip install -r requirements.txt
cp .env.example .env   # coloque sua GEMINI_API_KEY
python scripts/process_files_with_gemini.py 3-conhecimento/sources/
```

## Filosofia em uma frase

Um vault, **três cérebros que não se misturam**, uma inbox na entrada, skills
roteadas por cérebro, e wikilinks cruzando tudo — cada um com seu ritmo, sua
regra e sua ferramenta, conversando com a mesma LLM.

---

<div align="center">
Um projeto <a href="https://inema.club">INEMA.CLUB</a> · feito com Claude Code
</div>
