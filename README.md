# ethdev_docker
Development environment for Ethereum using Docker, Vue.JS and Truffle+GanacheCLI

How to get started:
- Install Docker / Docker-compose
- Clone this project
- Download and install Ganache [https://truffleframework.com/ganache]
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

