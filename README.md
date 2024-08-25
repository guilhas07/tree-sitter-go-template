## Announcement

The original author stopped using helm (which he mostly wrote this package for) on a daily basis, so he didn't really keep up with the development of tree sitter, and nvim-tree-sitter.
Some people have been found to keep the repo going, so if you have ideas for improvements feel free to open issues or pull requests.

# tree-sitter-go-template

[![Build/test](https://github.com/ngalaiko/tree-sitter-go-template/actions/workflows/ci.yaml/badge.svg)](https://github.com/ngalaiko/tree-sitter-go-template/actions/workflows/ci.yaml)

[Golang templates][] grammar for [tree-sitter][].

Also includes a [helm][] dialect. The concept of a dialect is that it uses the same parser, but can have different queries (e.g. for different injections).
More dialects could be added in the future (e.g. for html templates).

## NeoVim integration using [nvim-treesitter][]

-   Setup filetype detection:

    -   using [lua](https://neovim.io/doc/user/lua.html#vim.filetype):

    ```lua
    vim.filetype.add({
      extension = {
        gotmpl = 'gotmpl',
      },
      pattern = {
        [".*/templates/.*%.tpl"] = "helm",
        [".*/templates/.*%.ya?ml"] = "helm",
        ["helmfile.*%.ya?ml"] = "helm",
      },
    })
    ```

-   Install [nvim-treesitter][] as described here: [nvim-treesitter-install][]
-   Install the parser you want to use:

```vim
:TSInstall gotmpl
:TSInstall helm
```

> [!NOTE]
>
> If you are using helm, you should also install the yaml parser (:TSInstall yaml) to get [language injection][] for yaml

> [!TIP]
>
> If you are using [AstroNvim][] you can just install the [astrocommunity][] helm pack.

[tree-sitter]: https://github.com/tree-sitter/tree-sitter
[Golang templates]: https://golang.org/pkg/text/template/
[nvim-treesitter instructions]: https://github.com/nvim-treesitter/nvim-treesitter#adding-parsers
[nvim-treesitter-install]: https://github.com/nvim-treesitter/nvim-treesitter?tab=readme-ov-file#installation
[nvim-treesitter]: https://github.com/nvim-treesitter/nvim-treesitter
[helm]: https://helm.sh
[vim-helm]: https://github.com/towolf/vim-helm
[language injection]: https://tree-sitter.github.io/tree-sitter/syntax-highlighting#language-injection
[AstroNvim]: https://github.com/AstroNvim/AstroNvim
[astrocommunity]: https://github.com/AstroNvim/astrocommunity
