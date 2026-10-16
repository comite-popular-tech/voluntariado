# voluntariado

Quer ajudar numa iniciativa de tecnologia do comitê? **[Peça acesso aqui](../../issues/new?template=pedido-de-acesso.yml)**.

1. Abra a issue com a conta do GitHub que você vai usar e escolha a iniciativa.
2. Logo depois de enviada, o pedido segue para o núcleo da iniciativa, num lugar privado, e a issue daqui é esvaziada e fechada. É normal.
3. Aprovado, você recebe por e-mail um convite do GitHub para entrar na org `comite-popular-tech`. Aceite o convite para ver os repositórios.

Não escreva dados pessoais na issue.

## Como funciona

O workflow [`triagem.yml`](.github/workflows/triagem.yml) copia cada pedido para o repositório privado onde o acesso é concedido e esvazia, fecha e tranca a issue daqui. Ele usa um GitHub App só com permissão de issues.

O GitHub guarda o histórico de edição: o texto original da issue continua visível em *edited*. Para apagar de vez, um admin apaga a issue.

Configuração, uma vez:

- variável `APP_CLIENT_ID` e segredo `APP_CHAVE_PRIVADA`: do App de transferência;
- segredo `REPOSITORIO_DESTINO`: nome do repositório que recebe os pedidos.

Ao criar ou remover uma iniciativa, atualizem a lista em [`pedido-de-acesso.yml`](.github/ISSUE_TEMPLATE/pedido-de-acesso.yml).
