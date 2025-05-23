# Website Content

## Atualizações de conteúdo

Se você deseja contribuir e atualizar o site, siga as instruções abaixo.

Pequenas atualizações podem ser feitas diretamente pela interface web do GitHub. Já para atualizações maiores, é necessário configurar um ambiente de desenvolvimento local, conforme descrito na seção [Instalação local](installation.md).

Você pode usar qualquer editor de texto para fazer modificações. If you are using **Visual Studio**, you can open `Stride.Web.sln` solution file in the root of the repository and start making your updates directly from this IDE.

Você também pode [criar uma issue](https://github.com/stride3d/stride-website) para discutir suas alterações antes de começar a trabalhar nelas.

### Pequenas atualizações

Criar uma issue não é obrigatório para pequenas atualizações, mas é recomendável avisar outros colaboradores sobre o que você está fazendo. Se estiver em dúvida se sua alteração é pequena ou não, prefira criar uma issue primeiro.

#### O que é considerado uma pequena atualização?

Consideramos pequenas atualizações aquelas que envolvem alterações no conteúdo do site, como:

- Update the content of an existing page
- Update the content of an existing blog post
- Add a [new page](#creating-new-page) or [blog post](#creating-new-post)
- Corrigir erros de digitação
- Minor navigation or footer update
    - This will update all pages containing the navigation or footer

#### Etapas

> [!NOTA]
> Este guia parte do princípio de que você já está familiarizado com a atualização de arquivos no GitHub.

For the following instructions, use the [Stride Website GitHub repository](https://github.com/stride3d/stride-website):

[!INCLUDE [small-updates](../../includes/small-update-instructions.md)]

### Atualizações maiores

Para atualizações significativas, é **obrigatório** [criar uma issue](https://github.com/stride3d/stride-website/issues), para que outros possam comentar e oferecer sugestões.

Atualizações maiores envolvem mudanças estruturais no site, onde é útil visualizar o impacto antes de efetivar a alteração. Exemplos:

- Adding new Eleventy shortcodes and Liquid includes
- Updating the Bootstrap library or other libraries
- Modificações em layouts
- Reformulação de elementos visuais

Comece configurando seu ambiente de desenvolvimento local, conforme descrito na seção [Instalação local](installation.md). Após realizar e testar suas mudanças localmente, envie um pull request para mesclá-las na branch `master`.

Ao enviar um pull request, especialmente para mudanças grandes, recomenda-se incluir **capturas de tela** ou um link para a versão local do site. Essa abordagem ajuda os mantenedores a visualizar e avaliar suas alterações propostas de forma mais eficaz. Caso prefira usar a infraestrutura do GitHub para isso, consulte nosso [guia de implantação no GitHub Pages](deployment-azure.md#deployment-to-github-pages).

## Creating New Post

To create a new blog post, you can follow one of these methods:

1. Copy an existing post and update the front matter and content. This is the fastest way to get started with a new post
1. Alternatively, create a new file in the `posts` folder, ensuring that the file name follows the appropriate naming convention

Either method will allow you to create a new blog post, so choose the one that best suits your needs.

### Post Naming Convention

`YYYY-MM-DD-post-title.md`

Replace `YYYY-MM-DD` with the date of the post and `post-title` with the title of the post.

> [!IMPORTANT]
> **SEO Note:** Ensure the file title includes essential keywords related to your post's content. This is crucial as the file title dictates the URL of the post, which plays a significant role in search engine optimization (SEO).

### Post Front Matter

The file should start with the following front matter:

```yaml
---
title: 'Post title'
# author's id, defined in the _data/site.json
author: vaclav
# optional, if not set, the default tags will be used, tags are merged with the default tags
# you can find all tags in the live site in the /tags/ page
tags: ['Announcement']
# optional, if not set, the default image will be used
# use webp format for best performance, images should be located in the /images/blog/YYYY-MM-DD-post-title folder
image: /images/blog/2023-04/new-home-page.webp
# optional, if true, the post will be featured in the popular section
pupular: true
# permlink is automatically generated based on the file name, but you can override it here
permalink: /blog/2023-04/my-custom-link/ # this is a custom link
---
```

The same example, without the comments:

```yaml
---
title: 'Post title'
author: vaclav
tags: ['Announcement']
image: /images/blog/2023-04/new-home-page.webp
pupular: true
permalink: /blog/2023-04/my-custom-link/
---
```

Default front matter, which is used for all posts, can be found in the `posts/posts.json` file.

```json
{
  "layout": "post",
  "eleventyComputed": {
    "year": "{{ page.date | date: '%Y' }}",
    "modified": "Last Modified"
  },
  "permalink": "/blog/{{ page.fileSlug }}/",
  "tags": [ "blog", "search" ]
}
```

#### Image

The image specified in the front matter serves dual purposes: It appears in the blog listing at [Stride Blog](https://www.stride3d.net/blog/) and is used as the **og:image** meta tag for social sharing. Here are three ways to specify this image:

- Not including an image in the front matter will use the default image
- Including an image in the front matter will override the default image. The size of the image should be minimum **1200 x 600px** e.g. `image: /images/blog/2023-04/new-home-page.webp`
- External image URL e.g. `image: https://i.imgur.com/7GVEiSR.jpg`
- If you are looking for Stride specific logo's or icons, have a look at the [Figma](figma.md) options

### Post Content

Check the previous posts for an example of the post content. Ideally you should use the same format as the previous posts to preserve the consistency of the blog.

You can use shortcodes and includes which are described in the [Shortcodes and Includes](#shortcodes-and-includes) section.

You can also use majority of the Bootstrap classes in your content if you combine HTML and Markdown.

> [!TIP]
> We have a folder called `_drafts` where you can store your drafts. These files are not published. Once you are ready to publish your post, you can move it to the `posts` folder.

### Excerpt

The excerpt is the first paragraph of the post. Separated from the rest of the content by three dashes `---`. The excerpt is used in the blog post list, meta description and in the RSS feed.

**Example**

```yaml
---
title: 'Stride 4.1 is Now Live'
author: aggror
tags: ['Tutorials','Release', 'Graphics']
---
Stride contributors are proud to announce a new release now running on .NET 6 supporting the latest C# 10. That means you can now head to the download page and start developing your games using the latest .NET technologies.
---
Additional content goes here...
```

## Creating New Page

To create a new page, create a new file in the root folder or create a new folder and add an `index.md` file to it. You can use any templating language supported by Eleventy. We use Markup, HTML, Nunjucks.

### Page Front Matter

The page front matter works the same way as the post front matter. The only difference is that the `layout` property is required.

**Example:** file `features.html`

```yaml
---
layout: default
title: Features
description: 'Stride supports an extensive list of features: Scene Editor, Physically Based Rendering, Particles, UI Editor, Prefabs, DX12 & Vulkan, C# Scripting, etc...'
# permlink is automatically generated based on the file name, but you can override it here
permalink: /my-features/ # otherwise it would be /features/
---
```

## Shortcodes e includes

To enhance the quality and functionality of the content, both pages and posts can incorporate [shortcodes and includes](content-shortcodes-and-includes.md). These tools offer a versatile way to enrich the presentation and interactivity of the content on the Stride website.

## Recursos web

Our main web assets are:

- `css/custom-bootstrap.scss` - Slightly modified Bootstrap theme
  - Some Bootstrap variables are overridden
  - Some Bootstrap parts are disabled so they don't bloat the website (e.g. button-group, breadcrumb, ..)
- `css/styles.scss` - Main stylesheet
  - Styles also Dark Mode
- `css/syntax-highlighting.scss` - Imported prismjs styling, Light and Dark Mode
- `assets/search.liquid` - Script for search
- `assets/site.liquid` - Not used
- `assets/theme-selector.liquid` - Script for Ligth and Dark Mode selection
- `search.liquid` - Renders as `search.json` contains search meta


## Estilo

### Personalização do Bootstrap

Our website uses the [Bootstrap](https://getbootstrap.com/) framework, version **5.3**.

> [!IMPORTANT]
> Priorize o uso dos estilos nativos do Bootstrap antes de aplicar quaisquer estilos personalizados. Você deve estar familiarizado com [Utilities do Bootstrap](https://getbootstrap.com/docs/5.3/utilities/api/), que ajudam a atender à maioria dos requisitos de estilo.

### Diretrizes de CSS

Our goal is to write as little CSS as possible to ensure the website remains lightweight. We maximize the utilization of the Bootstrap framework to achieve this.

Further, we are using also [FontAwesome](https://fontawesome.com/) free icons. The icons are loaded in the `src/_includes/css/main.css` file.

## Submetendo suas alterações

[!INCLUDE [submitting-changes](../../includes/submitting-changes.md)]