# Node image
FROM node:latest

# Create code directory
RUN mkdir /apps

# Set working directory
WORKDIR /apps

# Install Truffle
RUN npm install -g truffle && npm config set bin-links false

# Install Vue-CLI
RUN npm install -g @vue/cli && \
    cd /usr/local/bin && \
    ln -s /usr/local/lib/node_modules/@vue/cli/bin/vue.js vue && \
    npm install -g @vue/cli-service-global

# Install OpenZeppelin
RUN npm install openzeppelin-solidity

# Install some other tools
RUN apt-get update && apt-get install -y mc nano
 
# Custom Bash rc
ADD .bashrc /root/.bashrc