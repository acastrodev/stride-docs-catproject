# Contributing to the Stride website

This documentation serves as a comprehensive guide to help you navigate and contribute to the **Stride website**.

If you're looking to make minor changes, such as adding or updating a post or page, or fixing a typo, you can jump straight to the [Content Updates](content.md#content-updates) section.

For more extensive updates 🤯🤦‍♂️ and a deeper understanding of the website project, we recommend exploring all the sections provided. Happy browsing and contributing!

Technologies we use to build our website:

- [Eleventy](https://www.11ty.dev/docs/) (static site generator)
- Markdown
- Mainly [Liquid](https://shopify.github.io/liquid/) and a bit Nunjucks (template engines)
- Bootstrap
- Font Awesome
- HTML, JavaScript, CSS, SCSS, and JSON
- GitHub Actions (CI/CD)
  - Our [GitHub Actions](https://github.com/stride3d/stride-website/tree/master/.github/workflows) are already configured for deploying to both staging and release environments.
  - For personal testing or demonstration purposes, you may need to set up your own GitHub Actions. This is especially useful for showcasing proposed changes to maintainers for their approval. For guidance on this, refer to our [Deployment to GitHub Pages guide](deployment-azure.md#deployment-to-github-pages).

## Dependencies

Various Stride systems rely on content fetched and processed from either the Stride website or the Stride Docs website. It's crucial to ensure that the following links remain active and accessible. Please refrain from removing or altering these links unless the dependent systems have been updated accordingly to accommodate any changes.

1. https://www.stride3d.net/legal/privacy-policy/
   - This link is integral to the **Stride Installer**. It provides users with transparent information about data handling and privacy considerations associated with using Stride.
2. https://www.stride3d.net/feed.xml
   - The **Stride Launcher** utilizes this feed to keep users updated with the latest news, updates, and announcements from the Stride community.
3. https://doc.stride3d.net/latest/en/index.json
   - This JSON file is crucial for integrating the Stride Website's search functionality with the Stride Documentation. It ensures that search results are comprehensive, including relevant information from both the Stride website and Stride Docs.