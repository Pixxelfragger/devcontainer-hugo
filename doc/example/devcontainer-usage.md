# Devcontainer usage

To use the image as a devcontainer, you can use the following `devcontainer.json`:


## TL:DR

```json
{
  "name": "Hugo",
  "image": "pixxelfragger/devcontainer-hugo:alpine",
  "extensions": [
        "budparr.language-hugo-vscode"
  ],
  "settings": {
    "terminal.integrated.shell.linux": "zsh"
  }
}
```

## Devcontainer config example

```json
{
    "name": "Hugo Dev",
    "image": "pixxelfragger/devcontainer-hugo:ext-debian",
    "settings": {
        "terminal.integrated.defaultProfile.linux": "zsh"
    },
    // Add the IDs of extensions you want installed when the container is created.
    "extensions": [
        "budparr.language-hugo-vscode"
    ],
    // Use 'forwardPorts' to make a list of ports inside the container available locally.
    "forwardPorts": [
        1313
    ],
    // Uncomment to connect as a non-root user. See https://aka.ms/vscode-remote/containers/non-root.
    // checkout link to see how to set up different users
    "remoteUser": "vscode",
    "containerUser": "vscode",
    "updateRemoteUserUID": true
}
```
