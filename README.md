# Obsidian Desmos

Render [Desmos](https://www.desmos.com/calculator) graphs right inside your notes.

# Installation

## Using Git

If your vault is hosted using git then congratulations, you can use the easy method. Run  
`git subtree add --prefix .obsidian/plugins/obsidian-desmos https://github.com/Nigecat/obsidian-desmos master --squash`  
to add the plugin to the vault in the current working directory of your terminal.  
You can then run  
`git subtree pull --prefix .obsidian/plugins/obsidian-desmos https://github.com/Nigecat/obsidian-desmos master --squash`  
to update the plugin to the latest version (from the same working directory).

## Using anything else

Alternatively, if you do not use git or are not comfortable using the terminal, you can manually install the plugin. Download [manifest.json](manifest.json), [versions.json](versions.json), and [main.js](main.js) and place them in `<vault>/.obsidian/plugins/obsidian-desmos` (you may have to create any missing folders).  
This process must be repeated to update the application.

# Usage

The most basic usage of this plugin involves creating a codeblock with the tag `desmos-graph` and placing the equations you wish to graph in the body:

````
    ```desmos-graph
    y=x
    ```
````

Equations use the [LaTeX math](https://en.wikibooks.org/wiki/LaTeX/Mathematics) format and you can graph multiple equations by placing each one on a seperate line:

````
    ```desmos-graph
    y=\sin(x)
    y=\frac{1}{x}
    ```
````

You can restrict the bounds of the graph and apply other settings by placing a `---` seperator before your equations. The content before it must be a set of `key=value` pairs seperated by either **newlines or semicolons** (or both):

````
    ```desmos-graph
    boundary_left=0; boundary_right=100;
    boundary_top=10; boundary_bottom=-10;
    ---
    y=\sin(x)
    ```
````

You can set the dimensions of the rendered image by using the `height` and `width` fields.

#### Restrictions

Note that graph restrictions follow the same format as desmos itself:

````
    ```desmos-graph
        y=\sin(x){y > 0}
    ```
````

## Important

Note that to be able to render these graphs into a PDF the following conditions must be fulfilled

1) Memory caching **must** be enabled
2) Obsidian **must** have been restarted since you initially created the graph
3) You **must** have viewed the rendered graph in the preview since the restart

After these are complete, a standard PDF export should work fine. 
In the future these steps will be removed and you will be able to directly export them.
