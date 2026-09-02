# nslookup & dig — DNS Lookups

## What it does
Resolves domain names to IP addresses and queries DNS records.
Useful when a site loads by IP but not by name.

## Syntax
```bash
nslookup google.com         # quick name to IP lookup
dig google.com              # detailed DNS query
dig google.com A            # just the A record (IPv4)
dig google.com MX           # mail records
dig @8.8.8.8 google.com     # query a specific DNS server
```

## My Terminal Output
```bash
rushi@rushi:~$ nslookup google.com
Server:         127.0.0.53
Address:        127.0.0.53#53

Non-authoritative answer:
Name:    google.com
Address: 142.250.67.14

rushi@rushi:~$ dig google.com A +short
142.250.67.14
```

## Key Points
- DNS maps human-readable names to IP addresses
- `nslookup` is quick for a simple name to IP check
- `dig` gives much more detail — TTL, record type, query time
- `dig +short` gives just the IP — cleaner output
- `dig @8.8.8.8` queries Google's DNS directly — bypasses your local resolver
- If a site loads by IP but not by name, DNS is the problem

## Common DNS record types
| Record | What it is |
|--------|-----------|
| `A` | IPv4 address |
| `AAAA` | IPv6 address |
| `MX` | Mail server |
| `CNAME` | Alias to another name |
| `TXT` | Text records (used for verification) |

## When I use this
Debugging why a domain is not resolving, checking what IP a domain
points to, verifying DNS changes after updating records.
