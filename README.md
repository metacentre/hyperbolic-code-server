# hyperbolic-code-server

Instructions so far

```
sudo apt update
sudo apt install docker.io nodejs npm -y
sudo npm install pm2 -g
pm2 startup

git clone https://github.com/AnEntrypoint/hyperbolic-code-server.git
cd hyperbolic-code-server/
npm install
node init.js

#follow instructions

cd tunnel
pm2 start server.js
pm2 save

cd ~/
sudo docker run -it --name code-server --restart unless-stopped -p 127.0.0.1:8080:8080 \
  -v "$HOME/.config:/home/coder/.config" \
  -v "$PWD:/home/coder/project" \
  -u "$(id -u):$(id -g)" \
  -e "DOCKER_USER=$USER" \
  codercom/code-server:latest

sudo fallocate -l 4G /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo sh -c "echo '/swapfile swap swap defaults 0 0' >> /etc/fstab"
```
