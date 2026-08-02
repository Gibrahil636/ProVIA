# ProVIA · Laboratório de Imagens

Ferramenta aberta do projeto **ProVIA** (EEB José Arantes, Camboriú-SC) — pesquisa sobre
letramento midiático e identificação de imagens geradas por inteligência artificial,
desenvolvida para o 32.º Prêmio Jovem Cientista (CNPq / Fundação Roberto Marinho).

**Módulo 1 — Gerador de imagens multi-IA.** A pessoa escolhe de 3 a 15 imagens, decide
entre prompts aleatórios (banco do projeto, com dificuldade catalogada) ou um prompt
próprio, e o site distribui a geração igualmente entre os motores de IA conectados,
exibindo a galeria com etiqueta de proveniência (motor, modelo, dificuldade, data)
e manifesto em JSON.

## Privacidade (princípio do projeto)

O site é **estático**: não tem servidor próprio, não tem banco de dados e **não coleta
nada de ninguém**. As chaves de API são digitadas pela própria pessoa e enviadas
diretamente do navegador dela para a empresa do respectivo motor (Google, OpenAI ou
OpenRouter). Se a pessoa marcar "lembrar", as chaves ficam salvas apenas no
`localStorage` do aparelho dela.

## Como publicar (sem instalar nada)

1. Crie uma conta gratuita em [github.com](https://github.com).
2. Clique em **New repository**, nomeie `provia`, marque **Public** e crie.
3. Clique em **Add file → Upload files**, envie `index.html`, `README.md` e `LICENSE`,
   e confirme em **Commit changes**.
4. Vá em **Settings → Pages**; em *Branch*, escolha `main` e pasta `/ (root)`; salve.
5. Em 1–2 minutos o site fica no ar em `https://SEU-USUARIO.github.io/provia/`.

## Chaves de API suportadas

| Motor | Onde criar | Custo |
|---|---|---|
| Google Gemini (imagem) | [aistudio.google.com/apikey](https://aistudio.google.com/apikey) | Gratuito, com cota diária; no nível grátis o Google pode usar o conteúdo para aprimorar modelos, e as imagens carregam marca-d'água invisível SynthID |
| OpenAI (GPT Image mini) | [platform.openai.com/api-keys](https://platform.openai.com/api-keys) | Contas novas podem ter crédito de boas-vindas; depois, a partir de ~US$ 0,005/imagem |
| OpenRouter (avançado, beta) | [openrouter.ai/keys](https://openrouter.ai/keys) | Pago em centavos; dá acesso a vários modelos de imagem com uma chave |

Meta AI e Microsoft Copilot **não oferecem API pública** de geração de imagens (situação
verificada em ago/2026); no ProVIA eles participam pelo **modo assistido** (módulo 2):
a ferramenta fornece o prompt pronto para colar manualmente na plataforma.

## Roteiro dos próximos módulos

- **Módulo 2** — Estação assistida (Meta AI / Copilot) e imagens reais (COCO val2017 /
  Agência Brasil, com crédito), completando o catálogo de proveniência.
- **Módulo 3** — Montagem automática do formulário (pré/pós-teste) via Google Apps
  Script, no modelo "faça uma cópia" — o formulário nasce na conta de quem usa.
- **Módulo 4** — Bloco de análise: pareamento por código anônimo e teste de Wilcoxon.

## Licença

Código sob licença [MIT](LICENSE). Conteúdos do instrumento de pesquisa serão
disponibilizados sob Creative Commons BY 4.0 nos módulos seguintes.
