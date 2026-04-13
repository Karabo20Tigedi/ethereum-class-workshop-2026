# Installing NodeJS and Yarn

[NodeJS](https://nodejs.org/en/) is a JavaScript runtime built on Chrome’s V8 JavaScript engine. It is a server-side JavaScript runtime that is designed to build scalable network applications. When you install NodeJS, also install Node Package Manager (NPM), which is required to set up most of the tools and libraries required for blockchain development.

For these tutorials, you will need Node.js version [(>= v20.18.3)](https://nodejs.org/en/download/). There are many ways that you can install Node.js: for instance, you can use a package manager like snap or homebrew to install it; However, due to the complexity of running different Node.js versions on the same machine, we very strongly suggest using nvm, as explained below.

We recommend installing Node.js using [nvm, the node version manager](https://github.com/nvm-sh/nvm). When language runtimes are in active development (like Node.js is), sometimes you end up needing to have multiple versions of Node.js installed, and different projects that you work on might require different versions of Node.js. These annoyances are quite rare, but when it happens that you need to have mutliple versions of Node.js installed, it’s super handy to have your system set up already so that installing multiple versions and switching between it is easy. You can use our instructions to set up nvm even if you have previously installed Node.js.

## `NVM` Installation for Windows

Before starting the installation, make sure to kill your Visual Studio Code if you have it installed. To do that on Windows, open a command prompt(type `cmd` in the windows start bar, then select “Run as administrator”) and run the command `taskkill.exe /IM code.exe`.

1. Download `nvm-setup.zip` from the most recent release of [nvm-windows](https://github.com/coreybutler/nvm-windows/releases) (at time of writing this document, version was 1.2.2).

2. Extract the contents of `nvm-setup.zip` and run the executable `nvm-setup.exe`. This should open the nvm installation wizard.

3. Accept the license agreement and click next. Continue to accept the default choices for any remaining prompts, and click “install”. If you receive messages along the lines of “NodeJS version XYZ is already installed, would you like nvm to control this installation,” select “Yes”.

4. Upon completion, you will see the below window

5. Open a command prompt with administrative privileges (type `cmd` in the windows start bar, then select “Run as administrator”).

6. Verify the installation, run the command:

```bash
nvm --version
```

This should display the version of nvm installed.

7. Run the command `nvm list available` to display all available NodeJS versions.

```bash
nvm list
```

8. Install Node.js version 20 using the command `nvm install 20`.

```bash
nvm install 20
```

9. To use this version of NodeJS, run the command `nvm use 20`.

```bash
nvm use 20
```

Troubleshooting with VSCode: Did you follow these instructions successfully, but find a “Command not found” error when you try to run npm in VSCode? Try this: Close VSCode completely. Re-open it. In your command shell in VSCode, try again. We have noticed that if you have VSCode open while installing nvm, it is possible that VSCode will not see the new software installation until it’s closed and re-opened. You can also confirm that VSCode correctly sees the NodeJS installation by running `echo %PATH%` in your windows command shell in VSCode: it should include an entry similar to `C:\Program Files\nodejs`.

## `NVM` Installation for Linux / Mac

1. Run either `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash` or If wget is installed then run `wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash`.

2. Close and reopen the active terminal.

> Note: You can also restart your terminal by running source ~/.bashrc or source ~/.zshrc depending on your shell.

3. Verify nvm is working by entering the command `nvm -v`. If your terminal prints out nvm, it should be working. If you see nvm: command not found or no feedback, open a new terminal and trying again or restart from step 1.

```bash
nvm -v
```

4. Install the required version of Node.js by typing `nvm install 20`.

```bash
nvm install 20
```

> Note: We are using v 20 for these tutorials. So we should activate it if it is not activated already

5. While Node.js is now downloaded, you need to activate it to use it. Run the following command:

```bash
# use the latest version
nvm use node
# use a specific version
nvm use 20
```

## NVM Installation for Mac M1 Silicon

1. Check for .zshrc Profile: Open a new terminal window and run the following command to check if you already have a `.zshrc` profile:

```bash
ls -a ~
```

If you see `.zshrc` in the list, you can skip this step. However, if it’s not there, you need to create one:

```bash
touch .zshrc
```

2. Now that you have a .zshrc profile, it’s time to install NVM. Visit the official NVM GitHub repository [here](https://github.com/nvm-sh/nvm#install--update-script) to find the NVM cURL install command. The command should look something like this:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

Copy this command and paste it into your terminal. This will download and install NVM, making it available for use.

3. Refresh .zshrc: As this installation affects your .zshrc profile, you should run the following command to update it:

```bash
source .zshrc
```

4. Now run steps 4 and 5 from the `NVM` Installation for Linux / Mac section above.

## Yarn Installation

Both Yarn and npm are package managers used for Node.js projects, but Yarn is generally considered faster and more focused on security than npm, with the main difference being that Yarn installs packages in parallel for quicker installation times while npm installs them sequentially.

```bash
npm install -g yarn
```

**Note (this monorepo):** Lesson packages may require Node **>= 18.18** (see each lesson’s `package.json`). If `nvm use 20` conflicts with a lesson, use the version specified in that lesson’s README.
