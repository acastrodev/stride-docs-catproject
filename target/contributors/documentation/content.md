# Conteúdo da documentação

## Atualizações de conteúdo

Se você deseja contribuir e atualizar o site, siga as instruções abaixo.

Pequenas atualizações podem ser feitas diretamente pela interface web do GitHub. Já para atualizações maiores, é necessário configurar um ambiente de desenvolvimento local, conforme descrito na seção [Instalação local](installation.md).

Você pode usar qualquer editor de texto para fazer modificações. Se estiver utilizando o **Visual Studio**, é possível abrir o arquivo de solução `Stride.Docs.sln`, localizado na raiz do repositório, e começar a editar a partir do próprio IDE.

Você também pode [criar uma issue](https://github.com/stride3d/stride-docs/issues) para discutir suas alterações antes de começar a trabalhar nelas.

### Pequenas atualizações

Criar uma issue não é obrigatório para pequenas atualizações, mas é recomendável avisar outros colaboradores sobre o que você está fazendo. Se estiver em dúvida se sua alteração é pequena ou não, prefira criar uma issue primeiro.

#### O que é considerado uma pequena atualização?

Consideramos pequenas atualizações aquelas que envolvem alterações no conteúdo do site, como:

- Atualizar o conteúdo de uma página existente (manual, tutorial ou nota de versão, etc.)
- Adicionar um [novo manual](#creating-new-manual-page) ou [tutorial](#creating-new-tutorial-page) ou qualquer outro conteúdo novo
- Corrigir erros de digitação

#### Etapas

> [!NOTA]
> Este guia parte do princípio de que você já está familiarizado com a atualização de arquivos no GitHub.

Para seguir as instruções abaixo, use o repositório oficial do Stride Docs no GitHub:[](https://github.com/stride3d/stride-docs)

[!INCLUDE [small-updates](../../includes/small-update-instructions.md)]

### Atualizações maiores

Para atualizações significativas, é **obrigatório** [criar uma issue](https://github.com/stride3d/stride-docs/issues), para que outros possam comentar e oferecer sugestões.

Atualizações maiores envolvem mudanças estruturais no site, onde é útil visualizar o impacto antes de efetivar a alteração. Exemplos:

- Atualização da versão do Docfx
- Modificações em layouts
- Reformulação de elementos visuais

Comece configurando seu ambiente de desenvolvimento local, conforme descrito na seção [Instalação local](installation.md). Após realizar e testar suas mudanças localmente, envie um pull request para mesclá-las na branch `master`.

Ao enviar um pull request, especialmente para mudanças grandes, recomenda-se incluir **capturas de tela** ou um link para a versão local do site. Essa abordagem ajuda os mantenedores a visualizar e avaliar suas alterações propostas de forma mais eficaz. Caso prefira usar a infraestrutura do GitHub para isso, consulte nosso [guia de implantação no GitHub Pages](deployment-azure.md#deployment-to-github-pages).

## Manual

Essas páginas contêm informações sobre como usar o Stride, um motor de jogos C# de código aberto.

> [!IMPORTANT]
> **Nota de SEO:** Certifique-se de que o nome do arquivo inclua palavras-chave essenciais relacionadas ao conteúdo do artigo. Isso é crucial porque o nome do arquivo determina a URL da página de conteúdo, o que desempenha um papel importante na otimização para motores de busca (SEO).

### Criando uma nova página de manual

1. Crie um novo arquivo na pasta `manual`, em uma das pastas já existentes (por exemplo, animation, audio, etc.) ou crie uma nova pasta dentro da pasta `manual`.
   - Se você criou uma nova pasta, certifique-se também de criar um arquivo `index.md` dentro dela.
1. Use qualquer página existente como modelo para a nova página.
1. Atualize o arquivo `toc.yml` (ou `toc.md`) dentro da pasta `manual` para incluir a nova página ou pasta. O arquivo `toc.yml` contém o índice das páginas do manual, que é exibido no lado esquerdo das páginas do manual. Essas páginas também são incluídas no arquivo PDF gerado opcionalmente.

### Convenção de nomes

Verifique as páginas e pastas existentes para seguir a convenção de nomes.

### Mídia

Observe que algumas pastas existentes possuem uma pasta `media`. Essa pasta contém imagens e vídeos usados nas páginas do manual. Você pode usar essa pasta ou criar uma nova dentro da sua própria pasta. Se possível, certifique-se de que as imagens estejam no formato `webp` e os vídeos no formato `.mp4`.

## Tutorial

Essas páginas contêm tutoriais sobre como usar o Stride, um motor de jogos C# de código aberto.

### Criando uma Nova Página de Tutorial

1. Crie uma nova pasta de tutorial dentro da pasta `tutorial`.
1. Crie um novo arquivo `index.md` dentro dessa pasta. Verifique os tutoriais existentes para ter uma referência do conteúdo desse arquivo.
1. Crie arquivos markdown para cada etapa do tutorial. Verifique a estrutura dos tutoriais existentes para basear o conteúdo desses arquivos.
1. Atualize o arquivo `toc.yml` na pasta `tutorial` para incluir a nova pasta de tutorial. O arquivo `toc.yml` contém o índice das páginas de tutorial, que é exibido no lado esquerdo das páginas de tutorial.

### Convenção de nomes

Verifique as páginas e pastas existentes para seguir a convenção de nomes.

### Mídia

Verifique que os tutoriais existentes possuem uma pasta `media`. Essa pasta contém imagens. Se possível, certifique-se de que as imagens estejam no formato `.webp`. Os vídeos devem estar no YouTube e incorporados nas páginas do tutorial.

## <g1>Outras seções</g1>

Além das seções Manual e Tutorial mencionadas acima, os mesmos princípios se aplicam a seções existentes e novas. Siga os formatos e convenções estabelecidos para garantir consistência e clareza em toda a documentação.

## Shortcodes e includes

O Docfx oferece suporte a sintaxes adicionais em markdown para enriquecer o conteúdo. Essas sintaxes são específicas do Docfx e **podem não ser renderizadas** corretamente em outras plataformas, como o GitHub.

Para mais informações, leia a documentação do Docfx sobre [markdown, shortcodes e includes](https://dotnet.github.io/docfx/docs/markdown.html?tabs=linux%2Cdotnet). Alguns recursos comuns incluem:

- **Alertas**: Blocos de citação com cores e ícones distintos, destacando a importância ou natureza do conteúdo.
- **Vídeo**: Incorpora conteúdo de vídeo diretamente na documentação.
- **Imagem**: Insere imagens para melhorar o aspecto visual da documentação.
- **Expressões matemáticas**: Integra notações e expressões matemáticas.
- **Diagramas Mermaid**: Incorpora [diagramas mermaid](https://mermaid.js.org/) para fluxogramas e outras representações gráficas.
- **Incluir arquivos markdown**: Inclui conteúdo de outros arquivos markdown de forma transparente.
- **Trecho de código**: Insere trechos de código para melhor clareza e demonstração.
- **Abas (Tabs)**: Organiza conteúdo em seções com abas para melhorar a legibilidade.

## Recursos web

Nossos principais recursos web incluem:

- `template/partials/affix.tmpl.partial` – Atualmente não funcional
- `template/partials/footer.tmpl.partial` – Atualmente não funcional
- `template/public/main.css` – Contém pequenas personalizações do CSS do Bootstrap
- `template/public/main.js`:
   - Define os ícones da navegação superior, como GitHub, Discord, Twitter
   - Injeta a seleção de versão da documentação do Stride acima do filtro na navegação lateral
   - Injeta a seleção de idioma da documentação do Stride na navegação superior
- `docfx.json` – O rodapé HTML está incluído na seção `_appFooter`

## Estilo

### Personalização do Bootstrap

Utilizamos o template `modern` fornecido pelo Docfx, que emprega o framework [Bootstrap](https://getbootstrap.com/) na versão **5.3**. Isso inclui o tema escuro, habilitado pelo Docfx.

> [!IMPORTANT]
> Priorize o uso dos estilos nativos do Bootstrap antes de aplicar quaisquer estilos personalizados. Você deve estar familiarizado com [Utilities do Bootstrap](https://getbootstrap.com/docs/5.3/utilities/api/), que ajudam a atender à maioria dos requisitos de estilo.

### Diretrizes de CSS

Nosso objetivo é escrever o mínimo possível de código CSS para manter o site leve, aproveitando ao máximo o framework Bootstrap.

## Submetendo suas alterações

[!INCLUDE [submitting-changes](../../includes/submitting-changes.md)]