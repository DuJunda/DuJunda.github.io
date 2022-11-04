# Step 1 ssh
ssh -ND <local_ip>:<local_port> -p <server_ssh_port> <usr>@<server_ip>

# Step 2 Proxy
  ## requests
  pip3 install requests[socks]  
  requests.get("http://www.google.com",proxies={'http':'socks5h://<local_ip>:<local_port>', 'https':'socks5h://<local_ip>:<local_port>'})  
  \# *socks5h represents that the domain name is resolved by the server, socks5 represents local* 
  ## ccxt
  pip3 install requests[socks]  
  binance.proxies = {'http': 'socks5h://<local_ip>:<local_port>','https': 'socks5h://<local_ip>:<local_port>'}  
  ## browser[recommended]
  install extension [SwitchyOmega](https://dujunda.github.io/files/SwitchyOmega.zip) or [SwitchySharp](https://dujunda.github.io/files/SwitchySharp.zip)  
  proxy protocol select **socks5**  
  input **<local_ip>** and **<local_port>**  
  *In SwitchyOmega, for pac setting, in switch rules, rule list rule select **proxy**; in rule list setting, rule list format select **AutoProxy**, rule list website is **https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt***  
  
  
  ## system
  ### windows
  open proxy setting, open proxy, address is **socks=<local_ip>** port is **<local_port>**, then click save
  ### linux
  $sudo nano /etc/environment  
  #export all_proxy="socks5h://127.0.0.1:1080"  
  export http_proxy="socks5h://127.0.0.1:1080"  
  export https_proxy="socks5h://127.0.0.1:1080"  
  export no_proxy="localhost, 127.0.0.1"  
  $sudo visudo #add line  
  Defaults        env_keep+="http_proxy https_proxy no_proxy"  
  $reboot  
