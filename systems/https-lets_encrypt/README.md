# HTTPS in Nginx with Let's Encrypt

```
AUTHOR: Samuel M.H.
DATE: 08-JAN-2022
LICENCE: all rights reserved.
```

## The problem
I have an NGINX server and I want to serve pages with TLS `https://`.

I will be following the guide in [1].

## Steps


### Set up
1. Install certbot [3]
```bash
sudo apt install certbot python3-certbot-nginx
```

2. Get a certificate
```bash
sudo certbot --nginx -d example.com -d www.example.com
```
* You only have to select wether you like to redirect all requests to https or not and make a backup of `/etc/letsencrypt`.
* At this point your server will be serving through https.


### Backup certificates

1. Create password protected securoty copy of the let's encrypt data [4].
```bash
GPG_TTY=$(tty); tar -czvf - /etc/letsencrypt/ | gpg --symmetric > RECOV_letsencrypt_`date  +%Y-%m-%d_%H-%M`.tar.gz.gpg
chown <ssh_user> <RECOV>
```

2. Store the backup in a safe place (copy from other computer).
```bash
scp <ssh_user>@<domain>:<RECOV> .
```

3. Recovery
```bash
gpg -d <RECOV> | tar -xvzf -
```

### Renew a certificate

* `certbot certonly`: to manually select the certificates.
* `certbot renew`: to non-interactively renew *all* the certificates.


## Conclusion
Certbot will take care of everything saving a lot of time.


## Resources
* [1] [Cómo proteger Nginx con Let´s Encrypt en Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04-es)
* [2] [Let's Encrypt](https://letsencrypt.org/es/)
* [3] [Certbot](https://certbot.eff.org/)
* [4] [How to create compressed encrypted archives with tar and gpg](https://linuxconfig.org/how-to-create-compressed-encrypted-archives-with-tar-and-gpg)
