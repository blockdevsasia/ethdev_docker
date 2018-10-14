# ethdev_docker
Development environment for Ethereum using Docker, Vue.JS and Truffle+GanacheCLI

How to get started:
- Install Docker / Docker-compose https://www.docker.com/get-started
- Clone this project
- Download and install Ganache [https://truffleframework.com/ganache]
- cd into the project 

```
cd ethdev_docker
```

- Start the container (docker-compose up -d)
- Run the start script (./scripts/start.sh)
- Get a shell in the container (./scripts/shell.sh)

Then create a Vue.js project
- vue create [projectname]
- (follow vue wizard)

Then create a Truffle project (which we actually will copy the files from into the vue project)
- (go to /apps)
- mkdir truffle && pushd truffle
- truffle init
- popd
- cp -R truffle/* [projectname]

Some cleanup
- rm -f truffle-config.js 

Set truffle.js to the following:
```    
module.exports = {
  // See <http://truffleframework.com/docs/advanced/configuration>
  // to customize your Truffle configuration!
  networks: {
    development: {
      host: "ganache-cli",
      port: 8545,
      network_id: "*",
      gas: 4600000
    }
  }
};
```

Then go into the Vue project and get started
- cd [projectname]
- serve_start
- truffle migrate

# Ethereum setup for Debian VM
Can also be found in:  https://bit.ly/2qryleP

#### NodeJS installation via package manager
- Check first if Node JS version installed is 8.x
```
node --version
```

- If installed Node JS version is not 8.x, remove NodeJS packages
```
sudo apt-get remove nodejs
```

- Run bash script from source (this script will add the repository link of the latest version supported by the distro)
```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
```

- Install NodeJS packages
```
sudo apt-get install -y nodejs
```

- Check if NodeJS is properly installed
```
node --version
```

#### NPM installation
- Normally, Node JS installation installs NPM
- Check if NPM version is 4.0.5
```
npm --version
```

- If version is not 4.0.5, reinstall NPM
```
sudo npm install npm@4.0.5    
```

- Check of NPM is properly installed
```
npm --version
```

#### Rebuild Python essential packages
```
sudo apt-get install build-essential python
```

#### Install Truffle
```
sudo npm install -g truffle
```

#### Install Ganache CLI and Web3 JS
```
sudo npm install ganache-cli web3@0.20.2
```

#### To check if Ganache is working properly
- Go to node_modules
```
cd <path where node_modules directory can be found>/node_modules
```

- Run Ganache local blockchain
```
.bin/ganache-cli
```

- If available accounts and corresponding keys displays, Ganache is working properly 

#### To check of Truffle works properly
- Go to project root directory
- Run Truffle local blockchain
- If available accounts and corresponding keys displays, Truffle is working properly 