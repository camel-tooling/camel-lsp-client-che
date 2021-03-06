# Camel LSP in Eclipse Che

The code itself is hosted in Che repositories.

## Use on che.openshift.io with Che 7

The plugin is available on che.openshift.io.

To activate the Camel language Server:

- Go to che.openshift.io
- Create a workspace based on the “Che 7” stack
- Go to your workspace
- Click on the yellow top left arrow
- Click on “Workspaces”
- Click on the “configuration” icon corresponding to your workspace
- Click on “Plugins”
- Enable “Camel” plugin in the second table
- Apply and open the workspace
- Reopen the xml or Java file
- Enjoy!

## Che 6

Only Camel XML DSL is supported.

To activate the Camel language Server:

- Go to your workspace
- Click on the yellow top left arrow
- Click on “Workspaces”
- Click on the “configuration” icon corresponding to your workspace
- Click on “Installers” menu and turn on “Apache Camel language server"
- Apply and open the workspace
- Reopen the xml file
- Enjoy!

## Che 7

The development is still in progress, see [Epic in Che repo](https://github.com/eclipse/che/issues/12584). It can already be used on che.openshift.io.

It will rely on [Camel VS Code extension](https://marketplace.visualstudio.com/itemdetails?itemName=camel-tooling.vscode-apache-camel) and [Eclipse Theia Camel client](https://github.com/camel-tooling/camel-lsp-client-theia).

### Test Camel VS Code Extension inside Che 7

- have access to a Che instance, choose your way:
  - use che.openshift.io
  - use [Che on OpenShift](https://www.eclipse.org/che/docs/che-6/openshift-single-user.html) (it is Che 6 doc but it is working with Che 7 currently)
  - use [Che on Kubernetes](https://www.eclipse.org/che/docs/che-6/kubernetes-single-user.html) (it is Che 6 doc but it is working with Che 7 currently)
  - DO NOT use Che on Docker, the plugins mechanism of Che 7 is not working
- Create a workspace on stack "Che 7"
- (DO NOT USE View --> Find Command , call "Deploy plugin by Id" and put _vscode:extension/camel-tooling.vscode-apache-camel_)
- Go to workspace configuration, config tab
- add

 ```yaml
    "attributes": {
       "editor": "org.eclipse.che.editor.theia:1.0.0",
       "plugins": "che-machine-exec-plugin:0.0.1,https://raw.githubusercontent.com/apupier/che-plugin-registry/109-AddApacheCamelVSCodeExtension/plugins/camel-tooling.vscode-apache-camel:0.0.14"
    }
 ```
 
 additional tips for debugging:
 
 - if on che.openshift.io, in Terminal, you can type echo ${CHE_OSO_CLUSTER//api/console} to have access to the OpenShift console url and investigate for all containers/pods deployed.
 - if you want to add several plugins in the "attributes", it is possible. you might need to also limit the memory size, it is another parameter following `"sidecar.org.eclipse.che.editor.<pluginId>.memory_limit": "512Mi"` pattern
