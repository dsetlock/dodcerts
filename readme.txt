###############################
#Created by Daniel Setlock
#Email at dsetlock@microsoft.com
################################

Update your ca-bundle for Git to include the DoD Root Certificates (2, 3, 4).

Download the file (ca-bundle.crt), and move it to a central location such as C:\users\<username>

Launch Git CLI. 
#Set Git back to check revocation if it was changed.
Type: git config --global http.sslVerify true
#Set new location for ca-bundle
Type:git config --global http.sslCAInfo C:/users/<username>/ca-bundle.crt
#Note: Slashes are / not \.
#Verify configuration changes
Type: git config -l

Restart open clients and attempt to clone/push against a .mil address.

#If authentication still fails, it might be necessary to change credential.helper from 'manager' to 'wincred'. 
#Through testing, some times 'manager' works, others, 'wincred', and cannot reproduce the issue due to variations in the Git install.
To update, launch Git CLI.
Type: git config --global credential.helper wincred
