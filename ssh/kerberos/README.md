## Install kerberos 

```
Ubuntu:

sudo apt install krb5-user krb5-config
wget https://linux.web.cern.ch/docs/krb5.conf
sudo mv krb5.conf /etc/
kinit -f adlintul@CERN.CH
klist
```

To avoid To avoid problems when connecting to lxplus, open the file /etc/ssh/ssh_config and add:

```
$ sudo vim /etc/ssh/ssh_config
> vim
HOST lxplus*
    ForwardX11 yes
    ForwardX11Trusted no
    GSSAPITrustDNS yes
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials yes
```

## Setting up a cron job

Follow [this](https://www.rcg.sfu.ca/workstations/kerberos.html#q-22-the-answer-to-q-21-isn-t-good-enough-i-need-my-processes-to-run-unattended-for-weeks)

```
$ crontab -l
# m h  dom mon dow   command
MAILTO=adlintul@cern.ch
* */2 * * * /home/alintulu/anaconda3/bin/kinit adlintul@CERN.CH -kt /home/alintulu/Documents/ConfigStuff/kerberos/.keytab
```