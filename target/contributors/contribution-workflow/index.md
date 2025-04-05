# Fluxo de contribuição para projetos Stride

Este guia descreve o fluxo de trabalho fundamental para contribuir com diversos projetos do Stride, incluindo o motor Stride, o site do Stride e a documentação do Stride. Seja você um colaborador experiente ou esteja começando agora, este fluxo garante que suas contribuições sejam integradas de forma eficaz.

## Visão geral

O processo de contribuição envolve várias etapas-chave, desde o fork do repositório até a integração das suas alterações ao projeto principal. Esse fluxo é aplicável às contribuições para o motor de jogos, o site e a documentação do Stride.

``` mermaid
%% Define styles
%% Main Graph
graph TB
%% Nodes
    Start[Início]
    A[Faça um fork do repositório]
    B[Crie um branch 'X']
    C[Realize as alterações no branch 'X']
    D{O repositório original foi atualizado?}
    E["Sincronize/Mescle o repositório original com seu fork <br>(branch main)"]
    F[Sincronize/Mescle o branch main do fork com o branch 'X']
    G[Teste suas alterações]
    H["Crie um Pull Request (PR)"]
    I[Revisão dos mantenedores]
    J[Responda ao feedback do PR]
    K[Revise e atualize o PR se necessário]
    L[Aguarde a mesclagem do PR pelos mantenedores]
    M[Sincronize/Mescle o repositório original com o seu fork do branch main]
    N[Atualize ou adicione a documentação relevante]
    O{Gostaria contribuir mais?}
    Z[Fim]
%% Edges
    Start --> A --> B --> C --> D
    D -->|Sim| E
    D -->|Não| G
    E --> F --> G
    G --> H --> I --> J --> K --> L --> M --> N --> O
    O -->|Sim| B
    O -->|Não| Z
```

## Passos detalhados

1. **Faça um fork do repositório**: Comece fazendo um fork do repositório do projeto com o qual deseja contribuir. Isso criará uma cópia pessoal do repositório para você trabalhar.
1. **Crie um branch 'X'**: No seu fork, crie um novo branch, nomeando-o de forma apropriada para refletir as alterações que pretende fazer.
1. **Realize as alterações no branch 'X'**: Implemente suas mudanças neste novo branch. Garanta que suas modificações estejam em conformidade com os padrões e diretrizes do projeto.
1. **Garanta que suas modificações estejam em conformidade com os padrões e diretrizes do projeto. Manter seu fork sincronizado evita conflitos e melhora a compatibilidade.**
1. **Sincronize/Mescle o repositório original com o seu fork (branch main)**: Caso existam atualizações, aplique-as ao seu fork para mantê-lo atualizado com o projeto original.
1. **Sincronize/Mescle o branch main do fork com o branch 'X'**: Mantenha também seu branch de trabalho atualizado com as alterações mais recentes do seu branch principal.
1. **Teste suas alterações**: Teste cuidadosamente suas alterações para garantir que estão funcionando corretamente e que não causam novos problemas.
1. **Crie um pull request (PR)**: Quando estiver satisfeito com suas alterações e os testes, [submeta um pull request](github-pull-request-guidelines.md) para o repositório original.
1. **Revisão dos mantenedores**: Os mantenedores do projeto irão revisar seu PR. Esse processo garante que as contribuições estejam alinhadas com os objetivos do projeto.
1. **Responda ao feedback do PR**: Caso receba sugestões ou observações dos mantenedores ou de outros colaboradores, ajuste seu PR conforme necessário. Essa colaboração ajuda a melhorar a qualidade do projeto.
1. **Revise e atualize o PR se necessário**: Continue ajustando seu PR até que ele atenda aos padrões do projeto e esteja pronto para ser mesclado.
1. **Aguarde a mesclagem do PR pelos mantenedores**: Após a aprovação, os mantenedores irão mesclar seu PR no repositório principal. Assim, sua contribuição será oficialmente integrada ao projeto.
1. **Sincronize/Mescle o repositório original com o seu fork (branch main)**: Depois da mesclagem, atualize o branch principal do seu fork com as últimas mudanças.
1. **Atualize ou Adicione a Documentação Relevante**: [Contribua com a documentação do projeto](xml-comments-and-docs.md) para refletir suas mudanças e ajudar outros usuários e colaboradores a entenderem as novas funcionalidades ou correções.
1. **Gostaria de contribuir mais?**: Avalie se deseja fazer novas contribuições. Se sim, reinicie o processo criando um novo branch.
1. **Fim**: Finalize o ciclo de contribuição atual. Seja para continuar contribuindo ou fazer uma pausa, suas mudanças já foram integradas ao projeto.

## Boas práticas
1. Garanta que suas contribuições estejam alinhadas com os objetivos e diretrizes do projeto.
1. Mantenha seu fork sincronizado com o repositório principal para evitar conflitos.
1. Participe da comunidade do Stride para obter suporte e colaborar com outros desenvolvedores.

Para diretrizes específicas de cada projeto, consulte a documentação de contribuição correspondente.