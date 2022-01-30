---
id: settingup
title: Setting Up for Local Development.
description: What you'll need to help develop the CIPP React frontend.
slug: /settingup
---

This page contains a mixture of required and recommended tools, programs and resources for developing the CIPP React frontend.

You'll want to have the following installed on the computer you're going to use for development:

* [Visual Studio Code](https://code.visualstudio.com) (VSCode) `winget install --exact vscode`
* These VSCode extensions:
  * [Azure Functions](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)
  * [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
  * [npm](https://marketplace.visualstudio.com/items?itemName=eg2.vscode-npm-script)
  * [npm Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense)
  * [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
  * [Stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
* [PowerShell 7](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-7.2) `winget install --exact PowerShell`
* [git](https://git-scm.com/download/win) `winget install --exact git`
* [node.js LTS](https://nodejs.org/en/download/) `winget install --exact "Node.js LTS"`
* [.NET SDK 5](https://dotnet.microsoft.com/en-us/download/dotnet/5.0)
* [.NET SDK 6](https://dotnet.microsoft.com/en-us/download/dotnet/6.0) `winget install --exact Microsoft.dotnet`

Using `npm` (node package manager) which is included with `nodejs` you're going to install the *Azure Static Web Apps CLI* and the *Azure Functions Core Tools* globally.

:::caution `npm install --global` Permissions

Depending on your system setup you may need to run the following commands elevated/as an administrator in order for npm to write the package files into a folder accessible to all users. Globally installed npm packages are available to all users.

:::

```bash title="Installing the Azure Static Web Apps CLI"
npm install --global @azure/static-web-apps-cli
```

```bash title="Installing the Azure Functions Core Tools"
npm install --global azure-functions-core-tools@4 --unsafe-perms true
```

Now we need to get the files downloaded for CIPP. In order to properly test as you develop the CIPP frontend we need a copy of your CIPP and CIPP-API repositories.

:::info Forking repositories

You're going to want to work on a [forked copy](https://docs.github.com/en/get-started/quickstart/fork-a-repo) of the [CIPP](https://github.com/KelvinTegelaar/CIPP) and [CIPP-API](https://github.com/KelvinTegelaar/CIPP-API) repositories.

For the rest of this guide we assume that your forks are at:

* **CIPP** - `https://github.com/goodatforking/CIPP`
* **CIPP-API** - `https://github.com/goodatforking/CIPP-API`

:::

:::tip What's a repository?

A Git repository is the `.git/` folder which you'll find inside many projects like CIPP. This repository tracks all changes made to files in the project, changes to these files are *commited* to the repository (repo) which then builds up a history of the project.

:::

The `CIPP` and `CIPP-API` repositories need to be located alongside each other (siblings) - so we're looking for a folder structure that looks like this:

```plain
- CIPP-Project
-- CIPP
-- CIPP-API
```

So if we assume that we want our `CIPP-Project` directory in `X:\Development` we're going to do the following:

```bash
cd "X:\Development"
mkdir "CIPP-Project"
cd "CIPP-Project"
git clone https://github.com/goodatforking/CIPP --origin goodatforking
git clone https://github.com/goodatforking/CIPP-API --origin goodatforking
```

:::tip Git remotes - An origin story

When you clone a git repository you automatically get a *remote* this is a pointer (usually a URL) to a remote copy of the git repository which you can push changes to. By default your first remote is called **origin**. But that doesn't really mean much to most people. In the commands above we're using `--origin goodatforking` to tell git that we want our first remote (origin) to be called `goodatforking`.

:::

At this point we could start working on the code - we have our pre-requisites and we have to code setup as we need it, but we're going to do one last thing to make life easier down the road.

We're going to add Kelvin's original repository as `upstream`.

```bash
cd "CIPP"
git remote add upstream https://github.com/KelvinTegelaar/CIPP
cd ..
cd "CIPP-API"
git remote add upstream https://github.com/KelvinTegelaar/CIPP-API
cd ..
```

:::tip git Branches

When working on open source projects it's often helpful to keep your stable / tested code separate from your under-development code. We can achieve this with git by using *branches*. The CIPP project uses the following branches:

* `main` - Our stable/tested code - this is where releases are created (tagged).
* `dev` - Our development code - this is the branch where active development takes place.
* `website` - The CIPP website code and documentation files.

:::

We're going to want to work from the `dev` branch since that's where the latest development code is, switching branches in git is achieved by doing a `checkout` on the branch.

```bash
cd "CIPP"
git checkout dev
cd ..
cd "CIPP-API"
git checkout dev
cd ..
```

That's it - we've got our repositories set locally and on the dev branch, our local environment is setup and ready to develop the CIPP UI. Read on through this section for further instructions.