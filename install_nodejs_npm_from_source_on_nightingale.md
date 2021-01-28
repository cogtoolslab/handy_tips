## So you want to install Node.js and npm on nightingale ...

### Here is a step-by-step guide, based on light modifications to the stackoverflow answer [here](https://askubuntu.com/questions/981799/how-to-install-node-js-without-sudo-access-but-with-npm-1-3-10-installed):
1. ssh into nightingale

2. Update your PATH variable and make some directories in your home dir where you can install stuff
```
echo 'export PATH=$HOME/local/bin:$PATH' >> ~/.bashrc
. ~/.bashrc
mkdir ~/local
mkdir ~/node-latest-install
```
3. Go into your newly created `node-latest-install` folder and install Nodejs from source (this might take a little while).
```
cd ~/node-latest-install
curl -L -O http://nodejs.org/dist/node-latest.tar.gz
tar xf node-latest.tar.gz
./configure --prefix=~/local
make install 
```
4. Now install npm from source
```
curl -L -O https://www.npmjs.org/install.sh
bash install.sh
```


### Potentially helpful resources
* [Install npm packages without sudo](https://github.com/sindresorhus/guides/blob/main/npm-global-without-sudo.md)
* [npm-g_nosudo](https://github.com/glenpike/npm-g_nosudo)
