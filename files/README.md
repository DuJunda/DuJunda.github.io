127.0.0.1=<local_ip>
1080=<local_port>
# Step 1 ssh
  $ssh -ND 127.0.0.1:1080 -p <server_ssh_port> <usr>@<server_ip>

# Step 2 Proxy
  ## requests
  $pip3 install requests[socks]  
  $python3  
  >requests.get("http://www.google.com",proxies={'http':'socks5h://127.0.0.1:1080', 'https':'socks5h://127.0.0.1:1080'})  
  \# *socks5h represents that the domain name is resolved by the server, socks5 represents local* 
  ## ccxt
  $pip3 install requests[socks]  
  $python3
  >import ccxt  
  >binance.proxies = {'http': 'socks5h://127.0.0.1:1080','https': 'socks5h://127.0.0.1:1080'}  
  >binance.fapiPublicGetTickerPrice()  
  ## browser[recommended]
  install extension [SwitchyOmega](https://dujunda.github.io/files/SwitchyOmega.zip) or [SwitchySharp](https://dujunda.github.io/files/SwitchySharp.zip)  
  proxy protocol select **socks5**  
  input **127.0.0.1** and **1080**  
  *In SwitchyOmega, for pac setting, in switch rules, rule list rule select **proxy**; in rule list setting, rule list format select **AutoProxy**, rule list website is **https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt***  
  
  
  ## system
  if you want browser can access, maybe require SwitchyOmega, and select "use system proxy" mode
  ### windows
  open proxy setting, open proxy, address is **socks=127.0.0.1** port is **1080**, then click save
  ### linux
  $sudo nano /etc/environment  
  >#export all_proxy="socks5h://127.0.0.1:1080"  
  >export http_proxy="socks5h://127.0.0.1:1080"  
  >export https_proxy="socks5h://127.0.0.1:1080"  
  >export no_proxy="localhost, 127.0.0.1"  
  
  $sudo visudo #add line  
  >Defaults        env_keep+="http_proxy https_proxy no_proxy"  
  
  $reboot  
  $python3 #test
  >import requests  
  >requests.get("http://www.google.com")  


  ### andriod
  install [juicessh](https://dujunda.github.io/files/JuiceSSH_2.1.4_Mod.apk) and [postern](https://dujunda.github.io/files/Postern_v3.1.3.apk), then config  
  
  
