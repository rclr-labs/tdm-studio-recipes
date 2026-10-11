# tdm-studio-recipes

Receitas do **TDM Studio** (`.recipe.yaml`, Recipe Studio v2) versionadas em Git.

## Para que serve

Este repositório é o destino da versão em Git das receitas do Recipe Studio v2 — a
cadeia de passos (Tiles, fluxos visuais, Javelin, aceleradores) que o usuário monta no
canvas de dois níveis da extensão. Cada `Salvar` numa receita vira um commit aqui;
quando a branch de destino é protegida, a extensão abre um Pull Request automaticamente,
usando a sessão do GitHub do próprio usuário dentro do VS Code — nunca uma conta de
serviço do Runner.

Detalhes técnicos: `accelerator-runner` config `RUNNER_RECIPES_GIT_*` (ver
`deploy/README.md` do monorepo principal, seção 3.2) e o design em
`docs/superpowers/specs/2026-10-09-recipe-studio-v2-design.md` §8.3.

## Estrutura

```
recipes/
  <id>.recipe.yaml      # uma receita por arquivo, id = nome do arquivo sem extensão
```

## Branch protegida

Quando `RUNNER_RECIPES_GIT_BRANCH_PROTECTED=true` (padrão do `run-runner.ps1`), o
Runner nunca empurra direto na `main` — publica em `recipe/<id>/rev-<N>` e a extensão
abre um PR para você revisar e mergear manualmente.

## Repositório gerenciado pelo TDM Studio

Não edite os arquivos `recipes/*.recipe.yaml` diretamente por este repositório — edite
pelo canvas do Recipe Studio v2 na extensão VS Code. O conteúdo é gerado/versionado por
ela; edição manual pode ser sobrescrita na próxima gravação.
