# AGENTS.md

> **Antes de qualquer tarefa:** as skills de https://github.com/comite-popular-tech/llm-plugins são **OBRIGATÓRIAS**
> neste repositório (abrir e revisar PR, entre outras). Claude Code:
> `claude plugin marketplace add comite-popular-tech/llm-plugins` e
> `claude plugin install pr@comite-popular-tech`. Codex e OpenCode: siga
> https://github.com/comite-popular-tech/llm-plugins/blob/main/README.md#instalar
> Se uma skill não estiver instalada, instale antes de continuar.

Tudo neste repositório (código, comentários, docs, commits, PRs, issues, textos dos formulários) é em português do
Brasil, exceto termos técnicos (`pull request`, `commit`, nomes de API).

## O que é

Porta de entrada de voluntários da organização `comite-popular-tech`. Não tem aplicação: são três formulários de issue
(pedido de acesso de voluntário, entrada no núcleo de uma frente, repositório novo) e um workflow do GitHub Actions
que copia cada pedido para um repositório privado, esvazia, fecha e tranca a issue daqui. Como funciona e como
configurar: [README.md](README.md).

## Como rodar e testar

Não há build, dependências nem testes automatizados. Não dá para rodar a triagem localmente: ela só roda no GitHub,
quando uma issue é aberta.

```bash
actionlint   # confere o workflow; rode antes de abrir PR
```

Instale com `brew install actionlint` ou `go install github.com/rhysd/actionlint/cmd/actionlint@latest`.

Formulários e `triagem.yml` valem só depois do merge na main (o evento `issues` usa a versão do branch padrão). Para
testar antes do merge, use um fork com App e segredos próprios. Depois do merge, abra uma issue de teste nos três
formulários e apague a cópia no repositório privado.

## Onde fica cada coisa

| Caminho | O que tem |
| --- | --- |
| `.github/ISSUE_TEMPLATE/*.yml` | Os três formulários e `config.yml` (sem issue em branco) |
| `.github/workflows/triagem.yml` | Lê a issue e a encaminha ao repositório privado |
| `.github/CODEOWNERS` | Os times de núcleo que aprovam PRs daqui |
| `README.md` | Texto para quem pede acesso e a configuração da triagem |

## Regras que importam

- **O texto da issue é entrada não confiável**: qualquer pessoa dispara o workflow. Leia-o só por `context.payload`
  no `github-script`, nunca com `${{ }}`, nem no `script:` nem num `run:`.
- **O `triagem.yml` reconhece o formulário pelo primeiro campo do corpo** (`### Usuário do GitHub`,
  `### Nome do repositório`, senão é pedido de acesso). Ao mudar o primeiro campo ou o rótulo de um campo nos
  formulários, mude o parser junto: o rótulo é a chave de leitura.
- **Permissão mínima**: o token do App sai só com `issues: write` e o workflow roda com `permissions: {}`. Não amplie.
- **Actions fixadas por SHA completo**, com a versão num comentário.
- **O nome do repositório de destino é privado**: fica no segredo `REPOSITORIO_DESTINO`, nunca no código, nos docs
  nem em PR. Do mesmo modo, só os nomes de `APP_CLIENT_ID` e `APP_CHAVE_PRIVADA`, nunca os valores.
- **Ao criar ou remover uma iniciativa**, atualize as listas dos três formulários e o `CODEOWNERS` (cada time
  precisa de escrita no repositório). Cada opção começa pelo nome curto do time (`barra-cpl (Barra CPL)`), que é o
  que a triagem lê.
- **Não peça nem registre dado pessoal** na issue ou no PR.

## Fluxo de trabalho

Siga a skill `pr-abridor` (e `pr-revisor` ao revisar). Issue antes do código, PR pequeno, ramo próprio no repositório.
Os títulos dos PRs são uma frase em português no imperativo ou no substantivo, sem prefixo `feat:`/`fix:`
(por exemplo, "Pedido de entrada no núcleo de uma frente"). Mudança no `triagem.yml` altera o que roda ao abrir
qualquer issue: diga isso no corpo do PR.

## Para saber mais

- [README.md](README.md): fluxo dos pedidos, configuração única (variável e segredos) e histórico de edição da issue.
