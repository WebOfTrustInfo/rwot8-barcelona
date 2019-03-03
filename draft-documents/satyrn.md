# Satyrn
A Markdown-based JavaScript Sandbox 

https://github.com/WebOfTrustInfo/satyrn  

Joe Andrieu joe@legreq.com 

Eric Welton eric@korsimoro.com

Will Abramson will.abramson@napier.ac.uk

Ganesh Annan gannan@digitalbazaar.com 

## Requirements
* File format is markdown
* In the app, the markdown is unmodifiable, but rendered
* If viewed outside the app, files will be sensibly renderable (it is compatible markdown)
* Custom code section(s) render as an “interactive” editor
* Code in editor sections is executable, with console output
* Focus on teaching/testing node.js modules
* JavaScript execution context
* Standalone executable app
* Vanilla JavaScript
* Creators and users may install additional node modules which will be installed in the file’s directory, under node_modules (as typical with node.js apps). Installation is outside the app, however, such modules may be require()'d within a file.
Node modules that conflict with modules  already in use by Satyrn, must be avoided. 

## Nice to have features
* Teacher mode
* REPL
* Module info to help users avoid conflicts

## Out of scope
* Browser libraries (Vue, React, Angular, etc.)
* Native bindings
* Non-javascript languages
* External editor
* Minimal external dependencies

## Electron Resources
https://github.com/sindresorhus/awesome-electron


## Components
* Electron
* Electron template https://github.com/sindresorhus/awesome-electron#boilerplates
* Markdown renderer https://github.com/showdownjs/showdown
* Inline Editor Ace
* Console (output)
* Editor control buttons





