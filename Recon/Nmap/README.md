# NMAP Recon Cheatsheet


### Test for Heartbleed Vulnerability 

`nmap --script ssl-heartbleed --script-args vulns.showall -sV <subnet_goes_here>`
