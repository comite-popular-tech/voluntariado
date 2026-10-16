# voluntariado

Quer ajudar numa iniciativa de tecnologia do comitê? **[Peça acesso aqui](../../issues/new?template=pedido-de-acesso.yml)**.

1. Abra a issue com a conta do GitHub que você vai usar e escolha a iniciativa.
2. A issue sai daqui logo depois de enviada e vai para um lugar privado, onde o núcleo da iniciativa avalia o pedido. Por isso o link dela passa a dar "página não encontrada": é normal.
3. Aprovado, você recebe por e-mail um convite do GitHub para entrar na org `comite-popular-tech`. Aceite o convite para ver os repositórios.

Não escreva dados pessoais na issue.

## Como funciona

O workflow [`triagem.yml`](.github/workflows/triagem.yml) transfere cada issue nova para o repositório privado onde o acesso é concedido, para o username de quem pede não ficar público. Ele usa um GitHub App só com permissão de issues, e o texto da issue nem é lido aqui.

Configuração, uma vez:

- variável `APP_CLIENT_ID` e segredo `APP_CHAVE_PRIVADA`: do App de transferência;
- segredo `REPOSITORIO_DESTINO`: nome do repositório que recebe os pedidos.

Ao criar ou remover uma iniciativa, atualizem a lista em [`pedido-de-acesso.yml`](.github/ISSUE_TEMPLATE/pedido-de-acesso.yml).
