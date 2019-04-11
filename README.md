# Camel LSP in Eclipse Che

The code itself is hosted in Che repositories.

## Che 6

Only Camel XML DSL is supported.

To activate the Camel language Server:

- Go to your workspace
- Click on the yellow top left arrow
- Click on “Workspaces”
- Click on the “configuration icon corresponding to your workspace
- Click on “Installers” menu and turn on “Apache Camel language server"
- Apply and open the workspace
- Reopen the xml file
- Enjoy!

## Che 7

Development is in progress, see [Epic in Che repo](https://github.com/eclipse/che/issues/12584).

It will rely on [Camel VS Code extension](https://marketplace.visualstudio.com/itemdetails?itemName=camel-tooling.vscode-apache-camel) and [Eclipse Theia Camel client](https://github.com/camel-tooling/camel-lsp-client-theia).
