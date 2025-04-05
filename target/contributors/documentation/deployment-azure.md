# Implantação

Nossa equipe explorou diversas opções de implantação, optando, por fim, pelo método descrito neste guia devido à sua eficácia. Além disso, para fins de demonstração, consulte a seção [Implantação de páginas no GitHub](deployment-azure.md#deployment-to-github-pages) para conhecer estratégias alternativas de implantação que você pode usar para apresentar suas atualizações.

## Implantação do Azure Aplicativo Web (Windows) com IIS

Este guia foi elaborado para pessoas que já possuem acesso a uma subscrição Azure. Ele oferece instruções passo a passo para configurar um novo Azure Web App, especificamente voltado para ambientes de staging (pré-produção). Observe que o processo para configurar um ambiente de produção é semelhante, mas exige um nome distinto para o aplicativo web.

As implantações no Azure Web Apps são automatizadas por meio do GitHub Actions, integrando-se ao nosso processo de Integração Contínua / Entrega Contínua (CI/CD). O pipeline CI/CD está configurado para acionar implantações automaticamente ao mesclar alterações nas branches `staging` ou `release`.

> [!NOTE]
> O processo de implantação descrito aqui já está estabelecido e em execução, hospedado no Azure e patrocinado pela .NET Foundation. Este guia serve principalmente como referência para mantenedores, caso seja necessário configurar uma nova implantação.

### Configurando um novo Azure Aplicativo Web

Siga atentamente estas instruções para criar seu Azure Web App em um ambiente de staging. Para implantar em produção, repita estes passos utilizando um nome diferente para o aplicativo web.

1. Acesse o [Azure Portal](https://portal.azure.com/)
1. Selecione **Criar um recurso**
1. Escolha **Criar Aplicativo Web**
1. Na aba Básico
   - Escolha sua assinatura e grupo de recursos existentes
   - Em Detalhes da instância, insira:
      - Nome: **stride-docs-staging**
      - Publicar: **Code**
      - Pilha de runtime: **ASP.NET V4.8**
      - Sistema Operacional **Windows**
      - Região: a mesma do app web atualizado
      - Plano de Preço – Um plano do Serviço de Aplicativo existente deve aparecer, caso a região e o grupo de recursos sejam os mesmos do aplicativo web atual. Atualmente usamos **Standard S1**.
      - Clique em **Avançar**
1. Na aba Implantação – Esta etapa pode ser feita depois, se preferir.
   - Habilite a opção Implantação contínua
   - Selecione a conta, organização `Stride`, repositório `stride-docs` e branch `staging`
   - Clique em **Avançar**
1. Na aba Monitorar + proteger
   - Deixe todas as configurações como padrão
   - Clique em **Avançar**
1. Aba Monitorar + proteger
   - Desabilite o Application Insights – Isso não é necessário neste estágio
   - Clique em **Avançar**
1. Na aba Rótulos
   - Deixe em branco, a menos que deseje adicionar rótulos
   - Clique em **Avançar**
1. Na aba Revisar + criar
   - Revise suas configurações
   - Clique em **Criar**
   - Uma GitHub Action será adicionada ao repositório e executada automaticamente. Ela falhará neste ponto, mas isso será resolvido nas etapas seguintes.

> [!CAUTION]
> Se você concluiu o processo da aba **Implantação**, certifique-se de que o perfil de implantação inclua a propriedade **DeleteExistingFiles**. Essa propriedade pode precisar ser definida como `False` ou `True` dependendo das necessidades específicas da sua implantação. Por exemplo, a implantação do Stride Docs mantém arquivos de versões anteriores, permitindo múltiplas versões como `4.2`, `4.1`, etc. Ajuste essa configuração conforme necessário.

### Ajustando a configuração do Aplicativo Web

1. Acesse o Aplicativo Web recém-criado
1. Clique em **Configuração**
1. Selecione **Configurações Gerais**
1. Altere a `versão Http` para **2.0**
1. Altere o `estado Ftp ` para **somente  FTPS**
1. Altere `somente HTTPS ` para **Ligado**
1. Clique em **Salvar** para aplicar as alterações

### Modificando a GitHub Action

A etapa anterior terá adicionado uma GitHub Action ao seu repositório, que pode falhar inicialmente. Para corrigir isso, você precisa alterar a GitHub Action:

1. Acesse o repositório
1. Selecione **Actions**
1. Você pode interromper a execução atual da action
1. Localize o novo arquivo da GitHub Action *(stride-docs/blob/master/.github/workflows/some-file-name.yml)* que foi gerado automaticamente pelo Azure Portal. Precisamos extrair os valores de `app-name` e `publish-profile` dele e desabilitar o acionador de push.
   - Para desativar o acionador de push, mantenha apenas o **workflow_dispatch** (acionador manual), conforme abaixo:
    ```
    on:
    #  push:
    #    branches:
    #      - staging
        workflow_dispatch:
    ```
1. Abra o workflow `stride-docs-staging-azure.yml` e atualize-o com os valores obtidos na etapa anterior. Salve as alterações.
1. Esse workflow também pode precisar ser adicionado à branch `master`, caso ainda não esteja presente.
1. Execute o workflow `stride-docs-staging-azure.yml`. Certifique-se de selecionar a branch correta `staging` e clique em **Run workflow**. Essa ação implantará o site no Aplicativo Web.

### GitHub Actions

- `stride-website-github.yml`: Permite implantação manual no GitHub Pages em um repositório forkado, usado principalmente para demonstrar atualizações.
- `stride-docs-release-azure.yml`: Automatiza a implantação em produção ao mesclar alterações na branch `release`, com opção de acionador manual.
- `stride-docs-release-fast-track-azure.yml`: Permite implantação manual em produção, ignorando a criação de artefatos.
- `stride-docs-staging-azure.yml`: Facilita a implantação automática para [staging](https://stride-doc-staging.azurewebsites.net/latest/en/index.html) quando mudanças são mescladas na branch `staging`, com opção de execução manual.
- `stride-docs-staging-fast-track-azure.yml`: Permite implantação manual em staging, ignorando a criação de artefatos.
- `stride-website-wiki.yml`: Implanta automaticamente no GitHub Wiki quando mudanças são feitas na pasta `wiki` da branch `master`, incluindo a opção de acionador manual.

## Implantação no GitHub Pages

Para apresentar suas atualizações, especialmente úteis no caso de alterações de design pendentes de revisão, você pode implantar o site da documentação em sua própria infraestrutura ou no GitHub Pages, um serviço gratuito de hospedagem. Após a implantação, compartilhe o link conosco para revisão.

### Pré-requisitos

No seu repositório `stride-docs`:

1. Acesse **Settings** → **Actions** → **General** → **Workflow Permissions**
   - Escolha **Read and write permissions**

### Executar a GitHub Action

1. Acesse **Actions**, selecione **Build Stride Docs for GitHub Staging**
   - Clique em **Run workflow**; você pode selecionar uma branch, se desejar
2. Acompanhe os logs de compilação enquanto a ação estiver em andamento
3. Após a compilação bem-sucedida, uma branch `gh-pages` será criada
4. cesse **Settings** → **Pages** → seção **Branch**
   - Escolha a branch `gh-pages` com a opção root e clique em **Save**
5. Após salvar, uma GitHub Action interna **pages build and deployment** será automaticamente criada e acionada, implantando o conteúdo no site do GitHub Pages
6. O site estará acessível em `https://[seu-usuário].github.io/stride-docs/4.2/en`
   - Altere a versão na URL conforme necessário. Você pode ver alguns erros de JS, relacionados a arquivos esperados no nível raiz.

### Adicionando um domínio personalizado

Opcionalmente, você pode adicionar um domínio personalizado. Isso deve resolver erros de URL relacionados a arquivos JS.

1. Acesse **Settings** → **Pages** → **Custom domain**
   - Insira seu domínio personalizado e siga as instruções para verificação
1. Após salvar, a ação **pages build and deployment** será acionada novamente, adicionando um arquivo `CNAME` contendo seu domínio personalizado à branch `gh-pages`
1. Seu site agora deve estar totalmente operacional em seu domínio personalizado, por exemplo: `https://stride-docs.vaclavelias.com/4.2/en/`, hospedado no GitHub Pages