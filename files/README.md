# Step 1 ssh
ssh -ND <local_ip>:<local_port> -p <server_ssh_port> <usr>@<server_ip>

# Step 2 Proxy
  ## browser
  install extension [SwitchyOmega](https://dujunda.github.io/files/SwitchyOmega.zip) or [SwitchySharp](https://dujunda.github.io/files/SwitchySharp.zip)  
  proxy protocol select **socks5**  
  input **<local_ip>** and **<local_port>**  
  ## system
  windows: open proxy setting, open proxy, address is **socks=<local_ip>** port is **<local_port>**, then click save
