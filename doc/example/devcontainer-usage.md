# Devcontainer usage

To use the image as a devcontainer, you can use the following `devcontainer.json`:


## TL:DR

```json
{
  "name": "Hugo",
  "image": "pixxelfragger/devcontainer-hugo:alpine",
  "extensions": [
    "gohugoio.hugo-0.107.0"
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
	// "image": "mcr.microsoft.com/vscode/devcontainers/base:debian-11",
	// "build": {
	// 	 "dockerfile": "./Dockerfile",
	//"image": 
	// 	 "args": {
	// 		// Update VARIANT to pick hugo variant.
	// 		// Example variants: hugo, hugo_extended
	// 		// Rebuild the container if it already exists to update.
	// 		"VARIANT": "hugo_extended",
	// 		// Update VERSION to pick a specific hugo version.
	// 		// Example versions: latest, 0.73.0, 0,71.1
	// 		// Rebuild the container if it already exists to update.
	// 		"VERSION": "latest",
	// 	 }
	// },
	// Set *default* container specific settings.json values on container create.
	"settings": {
		"terminal.integrated.defaultProfile.linux": "zsh"
	},
	// Add the IDs of extensions you want installed when the container is created.
	"extensions": [
		"bungcip.better-toml",
		"davidanson.vscode-markdownlint"
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