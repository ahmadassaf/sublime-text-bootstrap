# SublimeText Bootsrap

I am a huge fan of automating stuff, and setting up my development environment is one of the things i aim at completely automating as i spent a great deal of time coding and switching between my text editor to my terminal.

[Sublime Text](https://www.sublimetext.com) is a very powerful and popular editor/"ecosystem" with various tools for every code you’ll face. However, entering this ecosystem is long walk; setting up and learning all the plugins, tricks and such will take time.

This repo is inspired and forked from [evanplaice](https://github.com/evanplaice/sublime-text-seed) SublimeText seed. I have fixed few things that were not working on OSX and adding the part of automating setting up projects and workspaces.

Sublime Text configuration exists at those locations depended on your operating system:

 - **OSX**: `/Library/Application Support/Sublime Text 3`
 - **Linux**: `~/.config/sublime-text-3`

Those configurations mainly consists of following:

 - `Packages/` folder where all your installed plugins and setting files lie (shortcut into this available through preferences menu)
 - `Packages/User/` folder where are the files specific to your configuration (other folders in Packages/ folder are pristine plugin files and should not be directly edited)
 - `Local/Session.sublime_session` stores all the information about projects, workspaces, etc.
 - `Packages/User/Preferences.sublime-settings` stores the preferences you have changed (main settings for Sublime Text)
 - `Packages/User/Package Control.sublime-settings` contains the list of installed addons

> If you have any custom packages, color schemes or themes then you can drop those in the `Packages/User/` folder

To batch install packages (plugins, themes, etc.), a `Package Control.sublime-settings` file needs to be placed into the `Packages/User/` folder. Inside of the settings file should be a JSON object with the key "installed_packages" that references a list of package names. When Package Control starts, if any of those packages are not present, the will be automatically downloaded and installed.

[Package Control](https://packagecontrol.io) is a package manager that makes it exceedingly simple to find, install and keep packages up-to-date. It is driven by the Command Palette. To open the palette, press ctrl+shift+p (Win, Linux) or cmd+shift+p (OS X). All Package Control commands begin with Package Control:, so start by typing Package.

# What is this ? tldr;

In short, this script aims at automatic installation + configuration of Sublime Text in OSX, Linux by:

 1. Installs `Sublime Text 3` with `apt-get` or `brew`
 2. Installs `Package Control`
 3. Installs your desired theme that you backup in the `./themes` folder
 4. Load your default configurations that you have in `./user-settings`
 5. Configure projects (either single or multiple projects at a time)

The setup script works transparently across all platforms by leveraging python as well as OS-specific package managers

> Note: I have not tested personally the installation script on Linux, but would love any input there

# Usage

Run the following to install and config `Sublime Text`

```bash
./setup.py
```

Restart the editor when prompted to do so. To view the package installation progress open the `Sublime Text` console.

> **Note**: This WILL overwrite the existing configuration if you have answered `y` when prompted to overwrite current configurations

# Configuration

A default configuration is included with this package. Feel free to fork the project and add your own custom configuration.

### General Settings

*User-Settings*
```json
{
	"highlight_modified_tabs": true,
	"tab_size": 2,
	"translate_tabs_to_spaces": true,
	"draw_white_space": "all",
	"indent_guide_options":
	[
		"draw_normal",
		"draw_active"
	],
}
....
```

### Key bindings

I have customized various shortcuts and overriden few detaults. These key bindings are saved in `Default (OSX).sublime-keymap` in `Packages/User/` folder. For me, i have changed the default Find and Replace to be `command+h`.

```json
[
	{ "keys": ["option+a"], "command": "alignment" },
	{ "keys": ["super+h"], "command": "show_panel", "args": {"panel": "find_in_files"} }
]
```

### Themes

I use [material-theme](https://packagecontrol.io/Package%20Control.sublime-package)

*User-Settings*
```json
{
	"theme": "Material-Theme-Darker.sublime-theme",
	"color_scheme": "Packages/User/cobalt/MaterialCobalt.tmTheme",
}
```
I also include various theme specific setting in `Preferences.sublime-settings` like:

```json
	"material_theme_accent_lime": true,
	"material_theme_accent_orange": true,
	"material_theme_accent_purple": true,
	"material_theme_accent_red": true,
	"material_theme_accent_yellow": true,
	"material_theme_arrow_folders": true,
	"material_theme_big_fileicons": true,
	"material_theme_bold_tab": true
	...
```

As for the color scheme, i have customized an existing color scheme and have that in `user-setting/cobalt` folder. In the configuration process. this fill will be copied to ``Packages/User/cobalt` and will be loaded by the line `"color_scheme": "Packages/User/cobalt/MaterialCobalt.tmTheme"`

### Packages

Sublime Text is powerful on its own but the following add-ons unlock the full potential. Th list of packaged i have by default are:

 - [A File Icon](https://packagecontrol.io/packages/A%20File%20Icon): Sublime file-specific icons for improved visual grepping
 - [AutoFilename](https://packagecontrol.io/packages/AutoFileName): Autocompletes filenames used in 'src' or 'href' attributes.
 - [AdvancedNewFile](https://packagecontrol.io/packages/AdvancedNewFile): This plugin allows for faster file creation within a project
 - [Alignment](https://packagecontrol.io/packages/Alignment): A simple key-binding for aligning multi-line and multiple selections
 - [AlignTab](https://packagecontrol.io/packages/AlignTab): The most flexible alignment plugin for Sublime Text 2/3. It align using regular expression, support custom spacing, padding and justification, smart detection for alignment if no lines are selected with multiple cursors support and have table mode and Live preview modes
 - [All Autocomplete](https://packagecontrol.io/packages/All%20Autocomplete): Extends the default autocomplete to find matches in all open files
 - [ApacheConf.tmLanguage](https://packagecontrol.io/packages/ApacheConf.tmLanguage): Syntax highlight for `.htaccess`, `.htgroups`, `.tpasswd` and `.conf` files
 - [API Blueprint](https://packagecontrol.io/packages/API%20Blueprint): Syntax highlighting for the API Blueprint format with the ability of compiling blueprint into its AST media-type and live linting of blueprints as you type using SublimeLinter3
 - [ApplySyntax](https://packagecontrol.io/packages/ApplySyntax): ApplySyntax is a plugin for Sublime Text 2 and 3 that allows you to detect and apply the syntax of files that might not otherwise be detected properly
 - [AutoFileName](https://packagecontrol.io/packages/AutoFileName): Sublime Text plugin that autocompletes filenames
 - [Better CoffeeScript](https://packagecontrol.io/packages/Better%20CoffeeScript): Syntax highlighting and checking, commands, shortcuts, snippets, watched compilation and more
 - [Better Completion](https://packagecontrol.io/packages/Better%20Completion): This package aim at provide a simpler way to build own auto-completions and avoid *.sublime-completions override word-completion wrongly in some circumstance. It also provides several APIs completions such as JavaScript, jQuery, Lodash, Underscore, HTML5, CSS3 and Bootstrap Classes, React.js, etc
 - [BracketHighlighter](https://packagecontrol.io/packages/BracketHighlighter): Displays matching brackets to the left of the line numbers. It is Useful for navigating complex code with multiple layers of nesting
 - [Case Conversion](https://packagecontrol.io/packages/Case%20Conversion): Case conversion plugin (pascal, camel, snake)
 - [CodeFormatter](https://packagecontrol.io/packages/CodeFormatter): CodeFormatter is a Sublime Text 2/3 plugin that supports format (beautify) source code
 - [ColorHighlighter](https://packagecontrol.io/packages/Color%20Highlighter): Underlays selected hexadecimal colorcodes (like "#FFFFFF", "rgb(255,255,255)", "white", etc.) with their real color. Also, plugin adds color picker to easily modify colors
 - [DashDoc](https://packagecontrol.io/packages/DashDoc): Open the selected text or text under cursor in [Dash](http://kapeli.com/dash) documentation browser
 - [DocBlockr](https://packagecontrol.io/packages/DocBlockr): Simplifies writing DocBlock comments in Javascript, PHP, CoffeeScript, Actionscript, C & C++
 - [EditorConfig](https://packagecontrol.io/packages/EditorConfig): Maintain consistent code formatting/style across multiple editors and developers. It is configured by including an `.editorconfig` file the project root. To determine which settings to use see the [Official Documentation](http://editorconfig.org/)
 - [FileDiffs](https://packagecontrol.io/packages/FileDiffs): Shows diffs between the current file, or selection(s) in the current file, and clipboard, another file, or unsaved changes
 - [Filter Lines](https://packagecontrol.io/packages/Filter%20Lines): Quickly find all lines matching a string or regular expression
 - [Fix Mac Path](https://packagecontrol.io/packages/Fix%20Mac%20Path): Fix Mac Path is a simple plugin for Sublime Text 2 and 3 which sets Sublime Text's PATH to that reported by your shell. Now, if you add homebrew's /usr/local/bin directory to your PATH in .bash_profile (or whatever other way you set your shell's PATH,) Sublime Text will inherit that PATH
 - [GenerateUUID](https://packagecontrol.io/packages/GenerateUUID): Helper script to generate a UUID v4. Can be executed via keyboard shortcut `Ctrl+Shift+U`
 - [Git](https://packagecontrol.io/packages/Git): Plugin for some git integration into sublime text
 - [Handlebars](https://packagecontrol.io/packages/Handlebars): Fullest Handlebars.js templating support for Atom and Sublime Text 2 / 3. Also drives syntax colouring on Github and in Visual Studio Code
 - [HTML-CSS-JS Prettify](https://packagecontrol.io/packages/HTML-CSS-JS%20Prettify): HTML, CSS, JavaScript and JSON code formatter for Sublime Text 2 and 3 via node.js
 - [HyperClick](https://packagecontrol.io/packages/HyperClick): Quickly and easily jump between your files. The missing part of Go to definition functionality in Sublime
 - [Icon Fonts](https://packagecontrol.io/packages/Icon%20Fonts): Completions for popular icon fonts such as Font Awesome, Glyphicons and many more
 - [Indent XML](https://packagecontrol.io/packages/Indent%20XML): Plugin for Sublime Text editor for reindenting XML and JSON files
 - [Jade](https://packagecontrol.io/packages/Jade): A comprehensive textmate / sublime text bundle for the Jade template language
 - [LaTeXTools](https://packagecontrol.io/packages/LaTeXTools): LaTeX plugin for Sublime Text 2 and 3
 - [LogView](https://packagecontrol.io/packages/LogView): Logfile viewer and highlighter for Sublime Text 3
 - [Markdown Preview](https://packagecontrol.io/packages/Markdown%20Preview): Launch a browser tab to preview Markdown from Sublime Text.
 - [Minify](https://packagecontrol.io/packages/Minify): Minify for Sublime Text allows you to quickly minify and/or beautify CSS, JavaScript, JSON, HTML and SVG files
 - [MultiEditUtils](https://packagecontrol.io/packages/MultiEditUtils): A Sublime Text Plugin which enhances editing of multiple selections
 - [SidebarEnhancements](https://packagecontrol.io/packages/SideBarEnhancements): Adds additional options to the sidebar
 - [SPARQL](https://packagecontrol.io/packages/SPARQL): SPARQL syntax highlighting for Sublime Text
 - [SublimeLinter](https://packagecontrol.io/packages/SublimeLinter): Base package required to enable linting in SublimeText3
 - [SublimeLinter-contrib-eslint](https://packagecontrol.io/packages/SublimeLinter-contrib-eslint): This linter plugin for SublimeLinter provides an interface to ESLint
 - [SyncedSideBar](https://packagecontrol.io/packages/SyncedSideBar): As you switch tabs Sublime highlights only files in folders that are already expanded. This plugin makes that work for all files. It accomplishes this through use of the “reveal in side bar” command from the default context menu
 - [Terminal](https://packagecontrol.io/packages/Terminal): Launch terminals from the current file or the root project folder
 - [Text Pastry](https://packagecontrol.io/packages/Text%20Pastry): Extend the power of multiple selections in Sublime Text 2/3. Modify selections, insert numeric sequences, incremental numbers, generate uuids, date ranges, insert continuously from a word list and more
 - [TrailingSpaces](https://packagecontrol.io/packages/TrailingSpaces): Highlight trailing spaces and delete them in a flash
 - [TypescriptCompletion](https://packagecontrol.io/packages/TypescriptCompletion): Typescript auto completion with your project method name, and inject method manually with a module/class/method dictionary build from your TypeScript project
 - [WakaTime](https://packagecontrol.io/packages/WakaTime): Sublime Text 2 & 3 plugin for automatic time tracking and metrics generated from your programming activity

# Project Setup

Projects in Sublime Text are made up of two files: the `.sublime-project` file, which contains the project definition, and the `.sublime-workspace` file, which contains user specific data, such as the open files and the modifications to each. To understand more about projects, you can refer to [this page](http://docs.sublimetext.info/en/latest/reference/projects.html).

> As a general rule, the `.sublime-project` file can be checked into version control, while the `.sublime-workspace` file would not

A daunting task for me is when i clone a bunch of repos that i would likk to work on (especially if you are dealing with Microservices where you can have tens of repos) and i need to set up a Sublime Text project for each of those folders. After a bit of investigation, i found out that i can actually automate this process by creating the files needed by Sublime Text.

Basically, the script creates `.sublime-project` at the root of each folder initalized with the following:

```json
{
	"folders":
	[
		{
			"path": "/PATH/TO/FOLDER"
		}
	]
}
```
The script also creates a `.sublime-workspace` folder intialized with an empty JSON object `{}` that Sublime will fill up with additional metadata after.

The last step is tell Sublime where these files so that they can come up in the projects drop down. To do that, we need to add the paths for the `.sublime-workspace` to `Local/Session.sublime_session` inside of the `workspaces.recent_workspaces` array

![sublime-automator](https://s22.postimg.cc/59mjfnn5t/sublime-automator.gif)
