# Diretrizes para realizar pull requests no GitHub

Este guia assume que você já tem familiaridade com os conceitos básicos de Git e GitHub, e tem como objetivo fornecer instruções para criar pull requests (PRs) que sejam fáceis para a equipe do Stride revisar e mesclar.

Para entender melhor como contribuir com o Stride, consulte o nosso [fluxo de contribuição](index.md).

Ao enviar um pull request, você utilizará um [modelo](https://github.com/stride3d/stride/blob/master/.github/pull_request_template.md) que ajuda a fornecer todas as informações necessárias para uma revisão eficiente. Esse modelo inclui seções para um resumo das alterações, uma descrição detalhada, eventuais issues relacionados, a motivação por trás das mudanças e o tipo de alteração proposta.

Um dos pontos mais importantes do modelo é o checklist, que inclui tarefas como:
- Verificar se há necessidade de atualizar a documentação;
- Adicionar testes para novos recursos;
- Garantir que todos os testes estejam passando;
E, principalmente, confirmar que você **construiu e executou o editor** para testar suas alterações localmente. Esse último passo é essencial, pois demonstra cuidado ao validar a funcionalidade do que foi proposto, facilitando a revisão e evitando problemas futuros na integração.

Estrutura do modelo de pull request:
- **Resumo**: Uma visão geral rápida das alterações.
- **Descrição**: Explicação detalhada do que foi feito.
- **Issue relacionado**: Links para bugs ou discussões relacionadas.
- **Motivação e contexto**: O porquê das mudanças.
- **Tipos de alterações**: Classificação do tipo de alteração.
- **Checklist**: Itens de verificação para garantir completude e testes.

Esse formato sistematizado ajuda a equipe do Stride a entender, revisar e aceitar as contribuições com mais agilidade e clareza.

## Mesclando pull requests

### Prefixos no título

Ao mesclar um PR, o título deve conter um prefixo baseado nos rótulos (labels):

- Para rótulos genéricos, use colchetes com a categoria do Stride à qual o PR pertence, por exemplo:
`[Assets]`, `[OpenXR]`, `[Tests]`, `[Graphics]`, `[Physics]`, `[UI]`,
`[Audio]`, `[Input]`, `[Launcher]`, `[GameStudio]`, `[Build]`,
`[Doc]`, `[Samples]`, `[Shaders]`, `[Performance]`, `[Engineering]`
ou qualquer outra categoria que o mantenedor julgar adequada.
- Para rótulos específicos do Stride, o prefixo deve seguir a convenção de commits, por exemplo:
`feat:`, `fix:`, `perf:`, `docs:`, `style:`, `refactor:`, `test:`, `chore:`
ou outro prefixo apropriado.

### Rotulação

Após o PR ser mesclado, a equipe do Stride aplicará um único rótulo para categorizar o PR com base no tipo de alteração introduzida. Esses rótulos são utilizados pela automação do GitHub Releases para organizar as mudanças no changelog.****

A categorização é definida no arquivo [release.yml](https://github.com/stride3d/stride/blob/master/.github/release.yml).

A comunidade decidiu usar uma categorização híbrida baseada em categorias genéricas e categorias específicas do Stride.

Os rótulos devem ser aplicadas com base nas seguintes regras e ordem de prioridade:

**Categorias genéricas:**

- `breaking-change`: Se o PR introduz uma mudança incompatível com versões anteriores.
- `enhancement`: Se o PR traz uma nova funcionalidade ou melhoria.
- `bug-fix`: Se o PR corrige um erro.

**Categorias específicas do Stride:**

- `performance`
- `engineering`
- `area-Asset`
- `area-Audio`
- `area-Build`
- `area-Doc`
- `area-GameStudio`
- `area-Graphics`
- `area-Input`
- `area-Launcher`
- `area-Physics`
- `area-Samples`
- `area-Shaders`
- `area-UI`
- `area-Rendering`

PRs com outros rótulos ou sem rótulos serão automaticamente incluídos na categoria **Other Changes**.

> [!NOTE]
> Se múltiplos rótulos forem aplicados, a automação de versão priorizará a categoria genérica primeiro, seguida pela específica do Stride. Isso significa que apenas um rótulo será usada automaticamente nas notas de versão

## Exemplos

Exemplos de títulos de PRs gerados. Observe os diferentes prefixos utilizados para as categorias genéricas e as categorias específicas do Stride:

### 💥 Quebras de compatibilidade
- [Physics] Bepu codebase refactoring and clean-up

### 🎉 Novas funcionalidades
- [Input] Add haptic support to OpenVR and Oculus runtimes

### 🐞 Correções de bugs

- [Audio] fix: Audio emitter multiple references to same asset bugfix

### 🔧 Engenharia

- feat: Add editor settings for the camera speed increase/decrease hotkeys

### ⌨️ Entrada

- fix: Fixes mouse release for Winforms
- fix: Fixes detecting WinForms right shift key (fixes #754, fixes #929)

### ⚙️ Física

- fix: Fixes inconsistent box2D collision, see #1707 and #2019
- feat: Add ray test flags

## Squash de commits

Ao mesclar um pull request, a equipe do Stride pode fazer squash dos commits em um único commit. Isso mantém o histórico do Git mais limpo e facilita o entendimento das mudanças no futuro.