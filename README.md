# .github

Arquivos padrão da organização no GitHub.

O GitHub usa este repositório como fonte de arquivos padrão para todos os repositórios da organização que não têm uma versão própria desses arquivos. Assim, uma configuração feita aqui passa a valer em todos os repositórios, sem precisar replicar arquivo por arquivo.

Este repositório precisa ser público para que o GitHub aplique os arquivos padrão. Por isso, nada aqui pode conter informação interna: credenciais, URLs internas, nomes de clusters, contas ou detalhes de infraestrutura.

## O que está configurado

### Template de Pull Request

O arquivo `pull_request_template.md` preenche a descrição de todo PR aberto na organização com o campo do card no Azure DevOps:

```markdown
## Card

AB#
```

Basta completar com o número do card, por exemplo `AB#17017`. Com a integração do Azure Boards com o GitHub, essa referência vincula o PR ao card, e o PR passa a aparecer na seção **Development** do card.

O template só vale para repositórios que não têm um template próprio. Se um repositório tiver um `pull_request_template.md` na raiz, em `.github/` ou em `docs/`, o dele prevalece. Nesse caso, inclua o `AB#` no template do repositório também.

## Como alterar

Toda alteração neste repositório passa por PR, com aprovação de alguém do time de DevOps. Antes de abrir o PR, confira se o conteúdo pode ser público.

Mudanças aqui afetam todos os repositórios da organização que usam os arquivos padrão. Vale avisar o time quando algo novo entrar.

## Próximos passos possíveis

Algumas ideias para evoluir o uso deste repositório:

**Check de presença do `AB#`.** O template é um lembrete, mas não impede um PR sem número de card. Um workflow reutilizável que procura `AB#` seguido de número na descrição do PR, configurado como check obrigatório num ruleset da organização, transforma o lembrete em regra.

**Templates de workflow.** Arquivos na pasta `workflow-templates/` aparecem como opção em **Actions** > **New workflow** em todos os repositórios da organização. Serve para padronizar pipelines comuns, como build de imagem, deploy ou scan de segurança, sem copiar YAML entre repositórios. Os templates ficam públicos, então devem ser genéricos e receber os valores específicos por variáveis.

**Templates de issue.** Arquivos em `.github/ISSUE_TEMPLATE/` padronizam a abertura de issues, com formulários para bug, solicitação de acesso ou pedido de infraestrutura.

**`CONTRIBUTING.md`.** Um guia curto de contribuição, com convenção de branches, mensagens de commit e fluxo de PR, aparece como link nas telas de PR e issue de todos os repositórios.

**`SECURITY.md`.** Orienta como reportar uma vulnerabilidade de forma privada, em vez de abrir uma issue pública.

**README de perfil da organização.** Um arquivo em `profile/README.md` aparece na página da organização no GitHub. Como este repositório é público, esse README fica visível para qualquer pessoa. Para um conteúdo visível só para membros, o caminho é um repositório separado chamado `.github-private`.