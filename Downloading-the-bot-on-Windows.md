This page will go through how to download the bot and other required tools on Windows.
If you just want to get it done check out the [Short version at the bottom.](#short-version)
# Downloading and installing the required programs

## Git

The way you download the bot is by using Git.
Git is a distributed version-control system for tracking changes in source code during software development (https://en.wikipedia.org/wiki/Git).

It is highly recommended to use git because it makes it **much easier** to install and stay up to date with the latest improvements.

Download Git from https://git-scm.com/

## NodeJS
NodeJS is required to run the bot. 

Download the LTS version from https://nodejs.org/.


# Downloading the bot
Now that you have all the required programs installed we can start with downloading the bot itself.

We will install the bot on the Desktop as an example.
To get started open a command prompt by typing `cmd` in your windows search bar.

Now you will type some commands into your command prompt.

`cd Desktop` to navigate to the Desktop.

`git clone https://github.com/TF2Autobot/tf2autobot.git --branch master` to clone the repository and choose the master branch. The master branch contains released code and is considered to be stable.

Once it has been cloned a new folder will be made called `tf2autobot`.

`cd tf2autobot`

# Installing TypeScript

The bot is made with TypeScript. This means that you need to compile the source code to be able to run it.

`npm install typescript@latest -g` will install TypeScript.

# Installing modules

When the bot has been downloaded you need to install the modules. Do this by navigating to the tf2autobot folder with the command prompt or a terminal and using the command `npm install`.

# Compiling source

If you already have installed TypeScript, then `npm run build` will compile the code. If you haven't then see [Installing TypeScript](https://github.com/TF2Autobot/tf2autobot/wiki/Downloading-the-bot-on-Windows#installing-typescript).

Compile the source using `npm run build`

The compiled code will now be inside a folder called dist.

# Short version
Download and install Git from https://git-scm.com/

Download and install NodeJS from https://nodejs.org/

Next up open a command prompt by typing `cmd` in your windows search bar.

Now type in the following commands:

`cd Desktop`

`git clone https://github.com/TF2Autobot/tf2autobot.git`

`cd tf2autobot`

`npm install typescript@latest -g`

`npm install`

`npm run build`

# All done?

Then the next step will be [to configure your bot.](https://github.com/TF2Autobot/tf2autobot/wiki/Introduction---Configuring-the-bot)
