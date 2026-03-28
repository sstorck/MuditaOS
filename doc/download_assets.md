# Download Assets

Building update packages requires external assets located on external repositories releases pages, in specific versions for specified products. The tool automates downloading such assets.

## How to use [`download_asset.py`](../tools/download_asset.py)

The tool can be used to:

- list releases from the repository from the Mudita organization
- download selected assets from the repositories from the Mudita organization via GitHub API
- download selected asset release from the repositories to get asset files via GitHub API and tar library

The tool uses `argparse` to provide CLI and the best user experience.
Please see `download_asset.py --help` for up to date parameters use and documentation

## GitHub API token

To use GitHub API your GitHub login and special token (API password) are required.
This token can by generated on "User" -> [Settings](https://github.com/settings/profile) page in section [Developer settings](https://github.com/settings/apps) -> [Personal acces tokens](https://github.com/settings/tokens) section.
It has to have at least read access to repositories.

For more info please refer to the Github help page about adding tokens:
[github documentation: Creating a personal access token](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token)

### Scopes

When you generate a token you can set "Scopes" for which the token will work.
For downloading assets, we need a ":repo" scope with all sub-scopes.

> [!NOTE]
> Tokens are displayed only during their creation, so this is the only moment you can copy them.

If you forget to do this, you will have to generate a new token.

> [!NOTE]
> With token added [please double check](#testing-for-proper-asset-download-configuration) if it's working before issuing not working toolkit as most of the problems lies with no, or improper configuration.

## Storing settings

`download_assets.py` loads authorization data via git configuration.
The process requires that this data is stored in your current repository or global git configuration.

To do so:

1. Add your github login to the git config:

    ```bash
    git config --add user.githublogin Your_Github_Login_Here
    ```

2. Add token to your global git config on PC

    ```bash
    git config --add --global user.apitoken Your_Generated_Token_Value_Here
    ```

To see the values run:

```bash
git config user.githublogin
git config user.apitoken
```

## Testing for proper asset download configuration

1. check if you have token configured

    ```bash
    git config user.apitoken
    ```

    **if not**  please add the token ( see doc: [documentation](download_assets.md#github-api-token))

2. check if you have access to the PureUpdater repository in read mode

    ```bash
    curl -o /dev/null -H "Authorization: token $(git config user.apitoken)" "https://api.github.com/repos/mudita/PureUpdater"
    ```

    **if not** Then please either fix your token access or request access to the PureUpdater

3. Check if you can list releases on repository:

    ```bash
    python3 ./tools/download_asset.py github --repository PureUpdater list
    ```

    **if not** Then fix your token, or request access to PureUpdater
