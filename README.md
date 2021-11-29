# home
My home infrastructure

<img src="img/raspi.jpg" width=300>

## Proxy server configurations

### Enable remote forwarding
1. Add `GatewayPorts yes` to `/etc/ssh/sshd_config`
1. Restart ssh service by `sudo systemctl restart sshd`

### Redirect well-known ports for non-root binding

```shell
$ sudo iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 8080
$ sudo iptables -t nat -I PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 8443
```
