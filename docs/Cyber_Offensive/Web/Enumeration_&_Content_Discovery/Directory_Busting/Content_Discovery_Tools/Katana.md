[Katana](https://github.com/projectdiscovery/katana)

A next-generation crawling and spidering framework


#### install

Install using go [katana requires Go 1.18 to install successfully]
```shell
go install github.com/projectdiscovery/katana/cmd/katana@latest
```

If you can't use go, you can Install on Ubuntu using the below steps
```shell
sudo apt update
sudo snap refresh
sudo apt install zip curl wget git
sudo snap install golang --classic
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt update 
sudo apt install google-chrome-stable
```



