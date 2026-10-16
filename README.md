# voluntariado

Quer ajudar numa iniciativa de tecnologia do comitê? **[Peça acesso aqui](../../issues/new?template=pedido-de-acesso.yml)**.

1. Abra a issue com a conta do GitHub que você vai usar e escolha a iniciativa.
2. Logo depois de enviada, o pedido segue para o núcleo da iniciativa, num lugar privado, e a issue daqui é esvaziada e fechada. É normal.
3. Aprovado, você recebe por e-mail um convite do GitHub para entrar na org `comite-popular-tech`. Aceite o convite para ver os repositórios.

Precisa de um repositório para uma iniciativa? **[Peça aqui](../../issues/new?template=novo-repositorio.yml)**. Escolha a iniciativa, ou "nova" para criar uma iniciativa com os times de núcleo e de voluntários vazios.

Alguém precisa entrar no núcleo de uma frente? **[Peça aqui](../../issues/new?template=membro-do-nucleo.yml)**, informando o usuário do GitHub e a frente. Qualquer pessoa pode pedir, para si ou para outra pessoa. O núcleo tem **acesso de escrita** aos repositórios da frente, então um admin da org confere quem é a pessoa, com o núcleo da frente, antes de aprovar.

Não escreva dados pessoais na issue.

Em todos os casos, a issue recebe um comentário com o link do pedido no repositório privado. Se você não consegue abrir o link, é normal: mande-o para quem pode aprovar (o núcleo da iniciativa, num pedido de acesso de voluntário, ou um admin da org, num pedido de núcleo ou de repositório novo).

## Como funciona

O workflow [`triagem.yml`](.github/workflows/triagem.yml) copia cada pedido para o repositório privado onde ele é atendido, comenta o link da cópia na issue daqui e a esvazia, fecha e tranca. Ele usa um GitHub App só com permissão de issues.

O GitHub guarda o histórico de edição: o texto original da issue continua visível em *edited*. Para apagar de vez, um admin apaga a issue.

Configuração, uma vez:

- variável `APP_CLIENT_ID` e segredo `APP_CHAVE_PRIVADA`: do App de transferência;
- segredo `REPOSITORIO_DESTINO`: nome do repositório que recebe os pedidos.

Ao criar ou remover uma iniciativa, atualizem as listas em [`pedido-de-acesso.yml`](.github/ISSUE_TEMPLATE/pedido-de-acesso.yml), [`membro-do-nucleo.yml`](.github/ISSUE_TEMPLATE/membro-do-nucleo.yml) e [`novo-repositorio.yml`](.github/ISSUE_TEMPLATE/novo-repositorio.yml) e o [`CODEOWNERS`](.github/CODEOWNERS).
