# wiki-automation

This action sync your repository wiki with the contents of one of your folders. So you can document your project along with your codebase.

## Use case

There is a reason project documentation is hard: **we tend to overlook writing docs**. 

This is particularly true, when your docs tooling are totally separate from your codebase:

> _Docstrings?_ They need to be compiled, and they too rigid.  
> _Wiki pages?_ Yeah, but you need to abandon your IDE to update them 

By using this action we can automate [Github Wiki management](https://docs.github.com/en/communities/documenting-your-project-with-wikis/about-wikis), while we edit our documentation files along with our codebase. This is our proposed workflow:

- Dedicate a folder in your code-base to host your documentaion. Say `~/docs`
- Write down all your docs in `.md` files.
- Use [mermaid](https://github.blog/developer-skills/github/include-diagrams-markdown-files-mermaid/) to draw diagrams.
- Add a preview [extension in your IDE](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid). So you get instant feedback on how it looks.
- When you push to main, the action will update your repository wiki.

And you are done.

## How to use this action?

These are the action's available parameters:

| Name | Required | Description |
| ---  | ---      | ---         |
| token | Yes | GITHUB_TOKEN or PAT with appropiate permissions |
| repository | Yes | Use `${{ github.repository }}` |
| docs-folder | Yes | The folder to be sync-ed with your repository's Wiki |
| user-name | No | Your `git config user.name` (Default: `BOT`) |
| user-email | No | Your `git config user.email` (Default: `bot@bot.com` |

Assuming you wrote your documentation at `~/docs`, this is an example workflow to on `push`: 

```yml
on:
    push:
        branches: main
        paths:
            - docs/**

concurrency:
  group: update-wiki
  cancel-in-progress: true

jobs:
  update-wiki:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - uses: victor-public/wiki-automation@master
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          repository: ${{ github.repository }}
          docs-folder: docs
```


## Did you find this action useful?

Support me, so I can keep publishing good stuff:

[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/victor-public)
