# ProVIA · Laboratório de Imagens

Ferramenta aberta do projeto **ProVIA** (EEB José Arantes, Camboriú-SC) — pesquisa sobre
letramento midiático e identificação de imagens geradas por inteligência artificial,
desenvolvida para o 32.º Prêmio Jovem Cientista (CNPq / Fundação Roberto Marinho).

**Módulo 1 — Laboratório de imagens (modo assistido).** Em três passos:
(1) quantidade (3 a 15); (2) prompts — o gerador interno do ProVIA escreve um por
imagem com nível de dificuldade selecionável (🔄 troca a linha, ✏️ edita), ou a pessoa
escreve os seus; (3) apps — o lote é dividido igualmente entre **Gemini, ChatGPT,
Copilot e Meta AI**, e cada imagem vira um cartão com o prompt pronto, link direto
(ChatGPT e Copilot já abrem com o prompt preenchido) e devolução por **Ctrl+V**,
arrastar da outra aba ou envio de arquivo. Galeria com etiqueta de proveniência
(app, prompt, dificuldade, data) e manifesto em JSON. **Sem chave de API, sem
cadastro e sem custo** — usa as contas gratuitas que a pessoa já tem nos aplicativos.

## Privacidade (princípio do projeto)

O site é **estático**: não tem servidor próprio, não tem banco de dados e **não coleta
nada de ninguém**. As imagens coladas existem apenas na tela até serem baixadas;
fechar a página apaga tudo. A única coisa salva no aparelho é a preferência de
quantidade e modo de prompt.

## Como publicar (sem instalar nada)

1. Crie uma conta gratuita em [github.com](https://github.com).
2. Clique em **New repository**, nomeie `provia`, marque **Public** e crie.
3. Clique em **Add file → Upload files**, envie `index.html`, `README.md` e `LICENSE`,
   e confirme em **Commit changes**.
4. Vá em **Settings → Pages**; em *Branch*, escolha `main` e pasta `/ (root)`; salve.
5. Em 1–2 minutos o site fica no ar em `https://SEU-USUARIO.github.io/provia/`.

## Por que sem chaves de API?

Em 2026 o Google fechou a geração de imagens do nível gratuito para contas novas e
passou a exigir saldo pré-pago; os demais provedores cobram ou não têm API. O modo
assistido devolve o acesso a todos — inclusive estudantes — usando os aplicativos de
consumo gratuitos, e mantém a promessa central: o site não tem servidor, não pede
conta e não guarda nada.

## Módulos 2 e 3 (já incluídos)

**Imagens reais:** sorteio equilibrado entre dois bancos externos, carregados da pasta
`dados/` deste repositório:

| Arquivo | Conteúdo |
|---|---|
| `dados/coco_val2017.json` | **180** imagens do COCO val2017 **hospedadas no próprio repositório** (`reais/coco/`), com legenda oficial traduzida para o português. Sem dependência do servidor do dataset. |
| `dados/agencia_brasil.json` | **162** fotos da Agência Brasil com crédito do fotógrafo e licença CC BY 3.0 BR, todas verificadas uma a uma (2 hospedadas em `reais/`, o restante via URL da EBC). |

Cada cartão exibe a descrição, **de onde vem a descrição** (legenda do dataset ou título
da reportagem), a fonte, o crédito e o link. Imagens que falharem ao carregar são
substituídas automaticamente. Sem os arquivos de `dados/`, o site funciona com listas
menores embutidas.

**Sorteio por baralho.** Cada fonte tem uma fila embaralhada e persistente: uma imagem
só pode reaparecer depois que todo o ciclo se esgota, e o que saiu há pouco é jogado
para o fim do ciclo seguinte. Medição com 1800 exibições (12 sessões × 25 sorteios de 6) sobre as 342 imagens:
**0 repetições dentro da mesma tela, 0 em relação ao sorteio anterior, 0 reaparições em
até 3 sorteios**, distância média de 56,3 sorteios e uso uniforme (5× a 6× por imagem,
ideal 5,3×).

**Prévia e geração do formulário:** com as reais confirmadas e as sintéticas
devolvidas, a prévia mostra os itens na ordem do Forms (↑ ↓ e 🔀), com as perguntas
fixas (real/IA + confiança) e as opcionais por imagem (indícios com limite de 2 e
justificativa). O botão **Gerar formulário** baixa `provia_form.gs` — um Apps Script
com a sua configuração embutida que, colado em script.google.com, cria o Google Forms
em modo quiz (gabarito automático) na conta de quem executa — mais o
`provia_form_config.json` de proveniência completa.

## Próximo módulo

- **Módulo 4** — Bloco de análise: pareamento por código anônimo e teste de Wilcoxon.

## Licença

Código sob licença [MIT](LICENSE). Conteúdos do instrumento de pesquisa serão
disponibilizados sob Creative Commons BY 4.0 nos módulos seguintes.
