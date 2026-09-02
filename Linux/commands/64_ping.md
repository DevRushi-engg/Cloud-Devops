# ping — Test Network Reachability

## What it does
Sends packets to a host and measures if it responds and how long
it takes. First check when something seems unreachable.

## Syntax
```bash
ping google.com           # ping until Ctrl+C
ping -c 4 google.com      # send exactly 4 packets then stop
ping -c 4 192.168.1.1     # ping an IP address
```

## My Terminal Output
```bash
rushi@rushi:~$ ping -c 4 google.com
PING google.com (142.250.67.14): 56 data bytes
64 bytes from 142.250.67.14: icmp_seq=0 ttl=116 time=12.3 ms
64 bytes from 142.250.67.14: icmp_seq=1 ttl=116 time=11.8 ms
64 bytes from 142.250.67.14: icmp_seq=2 ttl=116 time=12.1 ms
64 bytes from 142.250.67.14: icmp_seq=3 ttl=116 time=12.5 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss
round-trip min/avg/max = 11.8/12.1/12.5 ms
```

## Key Points
- Always use `-c 4` — without it ping runs forever until Ctrl+C
- `0% packet loss` means the host is reachable
- Round trip time in milliseconds — higher means slower connection
- If ping fails, check: is the host up? Is your network up? Is DNS working?
- Ping `8.8.8.8` (Google DNS) by IP to test connectivity without DNS

## Troubleshooting with ping
```bash
ping -c 2 8.8.8.8       # test internet (by IP, no DNS)
ping -c 2 google.com    # test DNS resolution + internet
ping -c 2 192.168.1.1   # test local gateway
```

## When I use this
First thing I run when something seems unreachable — is it a
network issue, a DNS issue, or is the service itself down?

