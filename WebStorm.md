# Webstorm
WebStorm is an Integrated Development Environment by JetBrains focused on JavaScript development.

## First Project
- It comes with different web project templates out of the box
- It allows us to preview the current file in the browser. The list of available browsers is at the top right corner.

## Panels
- Project Panel
- Editor Panel
- Navigation Bar
- Status: It allows to change encoding, read only, got line, git branch
- Tool Buttons:
    - Project (Alt+1)
    - Favorites (Alt+2): Shows the saved breakpoints or bookmarked code
    - Find (Alt+3)
    - Run (Alt+4): Shows the running processes (gulp, grunt, debug)
    - Debug (Alt+5)
    - TODO (Alt+6): Shows the lines marked with a TODO comment.
    - Structure (Alt+7)
    - Version Control (Alt+9)
    - Event Log
    - Grunt (Alt+F11)
    - Gulp(Alt+F11)
    - Terminal (Alt+F12)

## Organizing IDE
- Window mode: it is separated to a new Window, useful for multiple monitors
- Floating mode: looks like a new window but in fact is still inside the main editor Window
- Docked: It sticks the panel to a position. It hides the panel once it loses focus if it's not pinned.
- Pinned: It pins the panel and prevents to hide it. It should be docked first.

The panels can be splitted to show more than one panel in the space.

## Terminal
- It shows the default terminal of the OS. It can be customized, go to: Settings/Tool/Terminal
- It supports tabs

## Coding Style, Fonts and Appearance
- WebStorm allows to define the code style by language. Things like indentation, tab size, etc.
- Go to: Settings/Editor/Code Style
- It also allows to change the font scheme. Go to and save a custom scheme: Settings/Editor/Colors & Fonts
- To change the appearance go to: Settings/Editor/Appearance & Behavior

## Coding in HTML
- WebStorm supports emmet which is a language for rapid html scaffolding
    - http://docs.emmet.io/
- `ctrl + alt + t` to surround an element with a tag

## Live Templates
Input the short name and hit `tab`
- Go to Settings/Editor/Live Templates to check the available templates
### Custom Live Templates
- Use `$variable_name$` to create placeholders for variables in your Live Template
- `$END$` to stablish the cursor after finishing the inputs
- `$SELECTION$` wrap some piece of selected code with the template
- Click on edit variables to define expressions or default values for the variables

## Scopes
- It allows what files to include in the project list.
- It allows to use conditions like expressions
- Go to Settings/Appearance & Behavior/Scopes to define the scope and add files to your list
- Mark directories as test, root, etc

## Live Editing
Allows to have a debug session in a browser (Chrome) to edit the code and see the changes in real time
- First install the Chrome Extension: https://chrome.google.com/webstore/detail/jetbrains-ide-support/hmhgeddbohgjknpmjagkdomcpobmllji
- Configure the debugger: Go to Run/Edit Configuration... and add a debugger

## JavaScript
- Surround with `ctrl + shift + t`
- Refactor: select the snippet and hit `ctrl + shift + alt + t`
- `ctrl + b` to go to a function declaration
- `alt + F7` to do the reverse and find usages of a function

### JSDoc
http://usejsdoc.org/
- Type `/**` above a function to document it
    - Hold `ctrl` while hovering over a function
- Then you can hit `ctrl + q` to show the documentation

## Preprocessors and MetaLanguages
WebStorm allows to work with preprocessors like Stylus and Sass and MetaLanguages like TypeScript
- Using preprocessors:
    - Install the preprocessor globally with npm `npm install stylus -g`
    - Add a watcher: Settings/Tools/File Watchers


## Language injection
- `alt + enter` select edit fragment to edit the injected code
- It will also allow to check regular expressions. First insert regex and then `alt + enter` again and select check regex. A small popup will appear to help us to check it.

## Debugging
- Set the server port: go to Settings/Build, Execution, Deployment/Debugger
- Go to Run/Edit Configurations to add a javascript debugging session
- Hit `shift + F9` to start the debugging
- Set a breakpoint on the left of the line
    - Right click on it to set a condition
- Debugging TypeScript works the same as normal JavaScript
### The debugging panel
- Debugger
    - Frames: A list of the functions that got us to this point
    - Variables: A tree view of the variables in the scope. We can even change the values here in real time.
    - Watches: to interrogate variables. It also allows to evaluate expressions.
        - hover over a variable and click on "+"
        - right click on the variable and "Add to the watches"
        - simply click on the "+" button on the Watches tab
    - It has several steppers for easy debugging
- Console
- Structure

## External Libraries
- When there is no local store of a library we can download it. `ctrl + enter` on the src to get it.
- To add Node to an existing project just add a debug configuration to the project.
- To add **code completion** right click anywhere on the editor and click "Use JavaScript Library". Select the library.
- To add intellisense go to Settings/Languages & Frameworks/Node and NPM, click "Configure..."
    - The packages section can be used to replace NPM

## Tools
### Test RESTful Services
WebStorm allow to test REST services directly : Go to Tools/Test RESTful service

### Deployment
Webstorm can deploy projects directly: Go to Tools/Deployment

### Local History
- It is like a local repo of the project
- It allows to put a tag in order to revert to a previous state

### Gulp
Gulps integrates deeply with gulp. It even allows debugging gulp tasks.

### Git
- If no git repo is initialized, you can go to VCS/Import Version Control/Create Git Repo
- Git has a git manager integrated. It allows to view the branching history directly. (`alt+9`)
- `ctrl + t` to update the project
- `ctrl + k` to commit and push changes

### GitHub
Webstorm allows to create gists directly. Select your snippet, right click on it and select "Create Gist"

## Pluggins
- gitignore
- material ui
- markdown

## KeyMaps
You can define your own shortcuts. Go to Settings/KeyMap.

- `ctrl + shift + a` to find an action or a shortcut
- `ctrl + alt + s` to open the settings
- `ctrl + alt + L` to reformat the code
- `ctrl + space` to pop up instellisense and look for the files in the current root.
- Paths: `ctrl + space` If we do it twice it looks for the files in the entire project.
- Multi Selection: place the cursor somewhere, hold `alt` and drag the cursor
    - or hold `alt` and click on multiple places
    - or `ctrl + j` to select the next occurrence
- `F6` to refactor/rename an element
- `ctrl + shift + n` to open a file
- `alt + enter` to create a file that doesn't exist
- `shift ~ shift` to show recent files