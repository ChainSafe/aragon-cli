![aragonCLI logo](/docs/assets/brand/aragoncli.png)

The aragonCLI (Command Line Interface) is used to create, develop, configure and manage Aragon DAOs and Applications.

## Installation

### Installation pre-requisites

The following must be installed prior to installation:

- Node + npm
  - Version of Node we recommend to be [the latest LTS version, available to download here](https://nodejs.org/en/).
  - After downloading and unpacking, you must add the /bin folder to you $PATH. 
  
For Linux:
- git
  - Install this using the command `sudo apt install git`
- python
  - Install this using the command `sudo apt install python`
  
For Mac:
- git
  - Install this using the [official installer](http://sourceforge.net/projects/git-osx-installer/). We recommend using the package manager [Homebrew](https://brew.sh), in this case use the command `brew install git`.

Note: Python comes pre-installed on Mac.

### Install aragonCLI

The aragonCLI can be installed from NPM:

```sh
npm install -g @aragon/cli
```

It can also be built and installed from source:

```sh
git clone https://github.com/aragon/aragon-cli.git
cd packages/aragon-cli
npm install
npm link
```

After installing, the main `aragon` executable will be available for use. It will also install the `dao` alias which is a shortcut for `aragon dao` commands.

## Global options

Options that change the behaviour of the command:

- `--silent`: Silence output to terminal.
- `--debug`: Show more output to terminal.
- `--cwd`: Project working directory.
- `--use-frame`: Use frame as a signing provider and web3 provider.
- `--environment`: The [environment](/docs/cli-global-confg.html#the-arappjson-file) in your arapp.json that you want to use.
- `--apm.ens-registry`: Address of the ENS registry. This will be overwritten if the selected environment from your arapp.json includes a `registry` property.
- `--apm.ipfs.gateway`: An URI to the IPFS Gateway to read files from. Defaults to `http://localhost:8080/ipfs`.
- `--apm.ipfs.rpc`: An URI to the IPFS node used to publish files. Defaults to `http://localhost:5001#default`.

### Example

```sh
aragon <command> --environment aragon:mainnet --use-frame --apm.ipfs.rpc https://ipfs.eth.aragon.network/ipfs --debug
```

## create-aragon-app

This command will set up an Aragon app project so you can start building your app from a functional boilerplate.

```sh
npx create-aragon-app <app-name> [boilerplate]
```

- `app-name`: The name or ENS domain name for your app in an aragonPM Registry (e.g. `myapp` or `myapp.aragonpm.eth`). If only the name is provided it will create your app on the default `aragonpm.eth` registry.

- `boilerplate`: (optional) the Github repo name or alias for a boilerplate to set up your app. The currently available boilerplates are:

	- `react`: this boilerplate contains a very basic Counter app and a webapp for interacting with it. It showcases the end-to-end interaction with an Aragon app, from the contracts to the webapp. Also comes with a DAO Template which will allow for using your app to interact with other Aragon apps like the Voting app. You can read more about DAO Template [here](templates-intro.md).
	- `bare`: this boilerplate will just set up your app directory structure but contains no functional code.

> **Note**<br>
> This is an independent package, it's not necessary to have `@aragon/cli` installed to use it.
> [npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) comes with npm 5.2+. If you use npm 5.1 or earlier, you can't use `npx`. Instead, install `create-aragon-app` globally.

> **Note**<br>
> The `react-kit` boilerplate has been deprecated and merged with `react` boilerplate. Also `kits` has been deprecated and `templates` should be used instead.
