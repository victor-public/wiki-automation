# wiki-automation

Action to sync your WIKI with one of the folders in your repository.

## Use case

## Parameters

| Name | Required | Description |
| ---  | ---      | ---         |
| token | Yes | GITHUB_TOKEN or PAT with appropiate permissions |
| repository | Yes | Use `${{ github.repository}}` |
| docs-folder | Yes | The folder to be sync-ed with your repository's Wiki |
| user-name | No | Your `git config user.name` (Default: `BOT`) |
| user-email | No | Your `git config user.email` (Default: `bot@bot.com` |

## Example workflows


## Did you find this action useful?

Support me, so I can keep publishing good stuff:

[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/victor-public)
