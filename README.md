# ubuntu20.04-vps
ubuntu-config one by one

add user

install clash-linux-amd64.gz and config--up config.yaml to ~/.config/clash/
config.yaml:

"""
port: 7890

socks-port: 7891

allow-lan: true

mode: Rule

log-level: info

external-controller: :9090

......
"""

#shadowsocks，v2ray 都是将代理转为本地 socks5 代理 (port:7891)，
#所以如果需要使用 http 代理(port:8118)，就需要借助 Privoxy

sudo apt install privoxy

vi /etc/privoxy/config

# 把本地 HTTP 流量转发到本地 7891 SOCKS5 代理
forward-socks5t / 127.0.0.1: 7891 .

# 可选，默认监听本地连接
listen-address 127.0.0.1:8118

install proxychains4 and change config in /etc/config/proxychain.conf

socks5 127.0.0.1 7891

(port same to clash  conffig.yaml socks-port:7891)

test by proxychains4 curl ip.gs -- vps ip

or

install speedtest-cli to test(compare speedtest-cli and proxychains4 speedtest-cli)

vim/neovim config  coc-nvim(github) use by vim-plug

# root用户配置user-rome同样的vim配置：
cp -r ~/.vim /root
cp -r ~/.vimrc /root


install conda by root and source --can ude by user : rome

aliyun mount data disk (20g) to /mnt/disk1

install postgresql 12 and change sql data path to /mnt/disk1/ppgsql_data

install pgadmin4 in unbuntu and login by web http://IP/pgadmin4 romepeng@outlook.com/t9


