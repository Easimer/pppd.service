## systemd unit file for pppd

To initiate a PPP connection on `/dev/ttyS0`, first set the link parameters under `/etc/default/pppd-ttyS0`:

```bash
SPEED=115200
LOCAL_IP=192.168.7.1
REMOTE_IP=192.168.7.2
```

Where `$SPEED` is the speed of the connection, `$LOCAL_IP` is our IP and `$REMOTE_IP` is the peer's address.

Start the service:
```bash
systemctl start pppd@ttyS0
```

Any character device can be used that is found under `/dev`. The config file of `/dev/ttyUSB0` is found at `/etc/default/pppd-USB0` and the service is started with `systemctl start pppd@ttyUSB0`.

The service automatically restarts on any failure and will try to establish the connection.
