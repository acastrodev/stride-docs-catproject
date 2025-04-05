# Comentários XML e documentação

Contribuir com o Stride não envolve apenas alterações no código, mas também requer manter a [documentação](https://doc.stride3d.net/latest/en/index.html) — incluindo a [Documentação da API](https://doc.stride3d.net/latest/en/api/index.html) e o [Manual](https://doc.stride3d.net/latest/en/manual/index.html) — atualizado e abrangente.

## Garantindo as atualizações na documentação

A equipe do Stride prioriza a documentação como parte do processo de revisão de Pull Requests (PR), a fim de manter a precisão e a integridade das informações. Garantir atualizações na documentação com cada alteração ajuda usuários e colaboradores a entender e utilizar os recursos do Stride de forma eficaz.

## Documentação da API

Para beneficiar tanto usuários da IDE quanto aqueles que utilizam a documentação da API gerada, é fundamental que todas as interfaces, classes, métodos e propriedades `públicas` em C# sejam devidamente documentadas com [comentários XML](https://dotnet.github.io/docfx/docs/basic-concepts.html). Essa prática permite que os usuários recebam informações contextuais diretamente nas IDEs e contribui para gerar uma documentação da API completa.

**Pontos-Chave para a Documentação da API:**

- **Comentários XML:** Todos os membros `públicos` destinados ao uso devem conter comentários XML descritivos. Esses comentários são essenciais para gerar a documentação da API útil e fornecem orientações diretamente na IDE.
- **Informações Descritivas:** Os comentários devem descrever claramente o propósito, os parâmetros, os valores de retorno e quaisquer exceções lançadas pelo método ou propriedade. Essas informações são inestimáveis para os desenvolvedores que integram esses recursos em seus projetos.
- **Utilize `<remarks></remarks>`:** para incluir contexto adicionais ou exemplos de uso, a marca `<remarks>` pode ser usada dentro dos comentários XML para fornecer informações complementares. Isso aumenta a compreensão e demonstrar aplicações práticas dos elementos da API.

## Atualizando o Manual
Mudanças significativas, como a introdução de novos recursos ou modificações em funcionalidades existentes, exigem atualizações no manual do usuário do Stride. É essencial que essas atualizações reflitam com precisão as mudanças, fornecendo aos usuários as informações mais recentes sobre como utilizar os recursos do Stride.

Cabe à equipe do Stride, junto com nossos incríveis colaboradores, garantir que qualquer nova contribuição inclua também as atualizações necessárias no manual. Essa parceria com a equipe de revisão ajuda a manter a documentação um recurso rico e valioso para toda a comunidade.

## ReleaseNotesNext.md

O arquivo [ReleaseNotesNext.md](https://doc.stride3d.net/latest/en/ReleaseNotes/ReleaseNotesNext.html) é um documento crucial que deve ser continuamente atualizado com resumos dos PRs importantes ou com grandes alterações que foram mesclados e são relevantes para a comunidade, como novos recursos.

Esse documento serve como um registro contínuo de todas as mudanças significativas previstas para a próxima versão. Manter esse documento atualizado é essencial para garantir que as notas de versão sejam precisas e completas, **facilitando o processo de lançamento**.