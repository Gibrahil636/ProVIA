[README(5).md](https://github.com/user-attachments/files/30928854/README.5.md)
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
justificativa). Antes de gerar, escolhe-se o tipo do formulário — **Pré-teste** (tema azul),
**Pós-teste** (tema laranja) ou **nome personalizado** — e, opcionalmente, o link de um
formulário próprio para servir de modelo visual.

O botão **Gerar formulário** baixa `provia_form.gs` — um Apps Script com a configuração
embutida que, colado em script.google.com, monta o Google Forms na conta de quem executa:
termo de assentimento, campo de código, quebra de seção, e para cada imagem as perguntas
de classificação (modo quiz, 1 ponto, gabarito automático), confiança, indícios (com
limite de 2) e justificativa. Vem junto o `provia_form_config.json` com a proveniência.

**Geração direta (ponte).** Além do caminho manual, o ProVIA cria o formulário sem sair
da página: a pessoa publica uma vez um pequeno Apps Script na própria conta
(*Implantar → App da Web*), cola o endereço `/exec` no ProVIA, e a partir daí o botão
**Gerar formulário agora** envia o lote inteiro — imagens sintéticas em base64, imagens
reais por URL — e devolve na tela os links de edição e de resposta. O endereço da ponte
fica salvo no navegador; nada trafega por servidor do projeto.

**Sobre o tema visual:** o Google não expõe API para cor e banner de formulários. Por
isso o ProVIA oferece o caminho da **cópia de modelo** — o script duplica um formulário
existente e troca só as perguntas, preservando tema, banner e configurações. Sem modelo,
o tema é aplicado à mão na paleta do Forms, em dois cliques.

## Painéis laterais

Quatro abas fixas na lateral abrem painéis:

- **Como usar o ProVIA** — apresentação da ferramenta, os cinco passos e o cuidado ético
  antes de aplicar em turma. Abre sozinha a cada visita, e pode ser desligada.
- **Análise dos resultados** — recebe as duas planilhas de respostas (CSV, TSV, XLSX ou
  colagem direta), pareia os participantes pelo `[Código]`, mostra quantos ficaram
  pareados e aplica o **teste de Wilcoxon pareado** sobre os pontos de acerto. Lista
  todas as justificativas escritas para avaliação com a rubrica 0/1/2 — as notas ficam
  salvas no navegador — e roda o teste também sobre as justificativas e sobre a
  pontuação total (0 a 8). Exporta os resultados em CSV.

  *Implementação:* postos médios para empates, descarte de diferenças nulas, valor de
  **p exato** (distribuição completa de W⁺) quando há até 22 pares sem empates, e
  aproximação normal com correção de continuidade e correção de empates nos demais
  casos, com tamanho de efeito r = |Z|/√n. Conferido contra o `scipy.stats.wilcoxon`
  nos dados reais da pesquisa (W = 434,5 · p = 0,63792 nos dois) e em casos de p exato.

- **Critérios do ProVIA** — os seis critérios de análise visual, a escala de leitura
  (0–1 provavelmente real · 2–3 sem certeza · 4–6 provavelmente gerada) e a rubrica de
  três níveis usada para pontuar as justificativas escritas.
- **Material do artigo** — os oito prompts exatos das imagens sintéticas (com ferramenta
  e função de cada uma, e botão de copiar), os créditos e licenças das oito imagens
  reais, a composição dos instrumentos e as opções de indícios do formulário.

Cada painel tem botão **🖨 imprimir**, com folha de estilo própria: sai só o conteúdo do
painel, sem a interface do site e sem quebrar tabelas ou fichas no meio.

Na prévia do formulário, marcar a **pergunta de indícios** abre um editor: no mínimo dois
indícios escritos por imagem, com botões para adicionar, remover, preencher com os seis
indícios padrão do ProVIA, ou cancelar tudo (o que desmarca a pergunta). O formulário só
é gerado quando toda imagem marcada tem ao menos dois indícios preenchidos, e cada
imagem leva a sua própria lista para o Google Forms.

## Próximo módulo

- **Módulo 4** — Bloco de análise: pareamento por código anônimo e teste de Wilcoxon.

## Licença

Código sob licença [MIT](LICENSE). Conteúdos do instrumento de pesquisa serão
disponibilizados sob Creative Commons BY 4.0 nos módulos seguintes.
