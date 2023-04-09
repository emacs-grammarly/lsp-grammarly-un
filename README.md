[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![JCS-ELPA](https://raw.githubusercontent.com/jcs-emacs/badges/master/elpa/v/lsp-grammarly-un.svg)](https://jcs-emacs.github.io/jcs-elpa/#/lsp-grammarly-un)

# lsp-grammarly-un

[![CI](https://github.com/emacs-grammarly/lsp-grammarly-un/actions/workflows/test.yml/badge.svg)](https://github.com/emacs-grammarly/lsp-grammarly-un/actions/workflows/test.yml)
[![Activate](https://github.com/emacs-grammarly/lsp-grammarly-un/actions/workflows/activate.yml/badge.svg)](https://github.com/emacs-grammarly/lsp-grammarly-un/actions/workflows/activate.yml)

`lsp-mode` client leveraging [unofficial-grammarly-language-server](https://github.com/znck/grammarly).

<p align="center"><img src="./etc/screenshot.png"/></p>

<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [lsp-grammarly-un](#lsp-grammarly-un)
  - [:floppy_disk: Quickstart](#floppy_disk-quickstart)
  - [:card_index: Commands](#card_index-commands)
  - [:wrench: Configuration](#wrench-configuration)
  - [:pencil: Roadmap](#pencil-roadmap)
  - [:money_with_wings: Using a Paid Grammarly Account](#money_with_wings-using-a-paid-grammarly-account)
    - [:mag: Method 1: Login with VSCode (easier)](#mag-method-1-login-with-vscode-easier)
    - [:mag: Method 2: Login with Emacs (a bit complicated)](#mag-method-2-login-with-emacs-a-bit-complicated)
    - [Authentication from Grammarly website](#authentication-from-grammarly-website)
  - [Contribution](#contribution)

<!-- markdown-toc end -->

## 💾 Quickstart

```el
(use-package lsp-grammarly-un
  :ensure t
  :hook (text-mode . (lambda ()
                       (require 'lsp-grammarly-un)
                       (lsp))))  ; or lsp-deferred
```

## 📇 Commands

List of commands interact with `language server` and `Grammarly.com`.

| Commands                       | Description                                                                  |
|:-------------------------------|:-----------------------------------------------------------------------------|
| lsp-grammarly-un-login         | Login to Grammarly.com                                                       |
| lsp-grammarly-un-logout        | Logout from Grammarly.com                                                    |
| lsp-grammarly-un-check-grammar | Start grammarly check for currnet document (buffer)                          |
| lsp-grammarly-un-stop          | Stop grammarly checker from current document (buffer)                        |
| lsp-grammarly-un-stats         | Log out current document status, `score`, `readability`, `words count`, etc. |

## 🔧 Configuration

`lsp-grammarly-un` supports following configuration. Each configuration is described in
detail in [Grammarly Settings](https://github.com/znck/grammarly#extension-settings).

* `grammarly.autoActivate` via `lsp-grammarly-un-auto-activate`
* `grammarly.audience` via `lsp-grammarly-un-audience`
* `grammarly.dialect` via `lsp-grammarly-un-dialect`
* `grammarly.domain` via `lsp-grammarly-un-domain`
* `grammarly.emotions` via `lsp-grammarly-un-emotions`
* `grammarly.goals` via `lsp-grammarly-un-goals`
* `grammarly.userWords` via `lsp-grammarly-un-user-words`
* `grammarly.overrides` via `lsp-grammarly-un-override`

## 📝 Roadmap

List of todos, but I have not got time to implement these features.

- [ ] Create another package that displays information from [Grammarly.com](https://www.grammarly.com/)
(To display useful information, `score`, `readability`, `word counts`, etc).
- [ ] Implement command `Ignore Grammarly Issue`.
- [ ] Implement `diagnostics` and `severity` for configuration.

## 💸 Using a Paid Grammarly Account

> ***NOTE:** To login, make sure you have package [keytar](https://github.com/emacs-grammarly/keytar)
set up properly. See [keytar#installation](https://github.com/emacs-grammarly/keytar#installation)
for setup instruction.*

You can either login with [vscode-grammarly](https://marketplace.visualstudio.com/items?itemName=znck.grammarly)
using VSCode or hit `M-x lsp-grammarly-un-login`. They both share the same credentials
so you can login with either side.

### 🔍 Method 1: Login with VSCode (easier)

Install VSCode and install extension [vscode-grammarly](https://marketplace.visualstudio.com/items?itemName=znck.grammarly)
from the extension panel.

<p align="center"><img src="./etc/login/vscode-grammarly-extension.png"/></p>

Then call command palette (default to <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>p</kbd>)
and type to search `grammarly login` command.

<p align="center"><img src="./etc/login/vscode-grammarly-login.png"/></p>

You should see [Grammarly Website](#authentication-from-grammarly-website) and
login with your Grammarly account.

<p align="center"><img src="./etc/login/open-app-vscode.png"/></p>

🎉 Make sure you click on the button `Open Visual Studio Code`. Done! You
can now close VSCode and go back to Emacs!

### 🔍 Method 2: Login with Emacs (a bit complicated)

Hit `M-x lsp-grammarly-un-login` and you should see the Grammarly's website pop out
from your favorite browser. See below [screenshot](#authentication-from-grammarly-website),

After login, click the button `Open URL:vscode`, If you have VSCode installed, then
this button would be `Open Visual Studio Code` instead yet it doesn't matter.

<p align="center"><img src="./etc/login/open-url-vscode.png"/></p>

Then click <kbd>F12</kbd> to open the DevTool window. You should able to see
an URI like the following

<p align="center"><img src="./etc/login/external-handler.png"/></p>

Copy and paste the URI back to Emacs and hit return.

<p align="center"><img src="./etc/login/emacs-paste.png"/></p>


🎉 Done! Now you should be loggin!

### Authentication from Grammarly website

Login with your Grammarly account (This step does not require VSCode to be
installed)!

<p align="center"><img src="./etc/login/grammarly-website.png"/></p>

## Contribute

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![Elisp styleguide](https://img.shields.io/badge/elisp-style%20guide-purple)](https://github.com/bbatsov/emacs-lisp-style-guide)

If you would like to contribute to this project, you may either
clone and make pull requests to this repository. Or you can
clone the project and establish your own branch of this tool.
Any methods are welcome!
