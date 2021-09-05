# home
My home infrastructure

<img src="img/raspi.jpg" width=300>

## Public access through reverse SSH tunnel
To be automated

### On Raspberry Pi
```
ssh -o ExitOnForwardFailure=yes -f -R $REMOTE_PORT:localhost:443 -N $USER@$IP
```

### On remote proxy server
Add `GatewayPorts yes` to `/etc/ssh/sshd_config`. Restart ssh service by `sudo systemctl restart sshd`
