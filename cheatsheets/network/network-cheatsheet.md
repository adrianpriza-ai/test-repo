# Network & Web Cheatsheet

Panduan lengkap untuk **network commands**, **cURL**, dan **web development**.

---

## 🌐 Network Commands

### Basic Connectivity

```bash
ping <host>                  # Test koneksi ke host
ping -c 4 <host>             # Ping 4 kali
traceroute <host>            # Trace route ke host
tracepath <host>             # Alternative traceroute
mtr <host>                   # Combined ping + traceroute
```

### DNS Lookup

```bash
nslookup <domain>            # DNS lookup (basic)
dig <domain>                 # DNS lookup (detailed)
dig +short <domain>          # DNS lookup (short)
host <domain>                # DNS lookup (simple)
dig MX <domain>              # Get mail servers
dig NS <domain>              # Get name servers
dig TXT <domain>             # Get TXT records
```

### Network Interfaces

```bash
ip addr                      # Show IP addresses
ip link                      # Show network interfaces
ip route                     # Show routing table
ip neigh                     # Show ARP cache
ifconfig                     # Legacy interface info (deprecated)
route -n                     # Legacy routing table
arp -a                       # Show ARP table
```

### Port & Connection Info

```bash
netstat -tulpn               # Lihat port yang terbuka
ss -tulpn                    # Alternatif netstat (lebih cepat)
lsof -i                      # List network connections
lsof -i :8080                # Check port 8080
nc -zv <host> <port>         # Test port connectivity
telnet <host> <port>         # Test port (legacy)
```

### Download & Transfer

```bash
curl <url>                   # HTTP request
wget <url>                   # Download file
scp file user@host:/path     # Copy file via SSH
rsync -avz src/ dst/         # Sync files
sftp user@host               # FTP over SSH
```

---

## 🔷 cURL Examples

### Basic Requests

```bash
curl -X GET <url>            # GET request
curl -X POST <url>           # POST request
curl -X PUT <url>            # PUT request
curl -X DELETE <url>         # DELETE request
curl -I <url>                # HEAD request (headers only)
```

### With Data

```bash
curl -X POST -d "key=value" <url>           # POST form data
curl -X POST -d '{"key":"value"}' <url>     # POST JSON
curl -X POST -F "file=@image.png" <url>     # Upload file
```

### With Headers

```bash
curl -H "Authorization: Bearer token" <url> # Auth header
curl -H "Content-Type: application/json" <url> # JSON content
curl -H "User-Agent: CustomAgent" <url>    # Custom user agent
```

### Advanced Usage

```bash
curl -o file.zip <url>       # Download file
curl -L <url>                # Follow redirects
curl -k <url>                # Ignore SSL errors
curl --retry 3 <url>         # Retry on failure
curl -w "%{http_code}" <url> # Show HTTP status code
curl -v <url>                # Verbose output
curl -x proxy:port <url>     # Use proxy
```

### API Testing

```bash
# GET with query params
curl "https://api.example.com/users?page=1&limit=10"

# POST with JSON
curl -X POST https://api.example.com/users \
  -H "Content-Type: application/json" \
  -d '{"name":"John","email":"john@example.com"}'

# PUT update
curl -X PUT https://api.example.com/users/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"Jane"}'

# DELETE
curl -X DELETE https://api.example.com/users/1 \
  -H "Authorization: Bearer token"
```

---

## 📊 HTTP Status Codes

### Success (2xx)

```
200 OK                       # Success
201 Created                  # Resource created
202 Accepted                 # Request accepted
204 No Content               # Success, no content
```

### Redirection (3xx)

```
301 Moved Permanently        # Redirect permanent
302 Found                    # Redirect temporary
304 Not Modified             # Cached version valid
307 Temporary Redirect       # Temporary redirect
```

### Client Errors (4xx)

```
400 Bad Request              # Invalid request
401 Unauthorized             # Authentication required
403 Forbidden                # Access denied
404 Not Found                # Resource not found
405 Method Not Allowed       # HTTP method not allowed
408 Request Timeout          # Request timed out
429 Too Many Requests        # Rate limited
```

### Server Errors (5xx)

```
500 Internal Server Error    # Generic server error
502 Bad Gateway              # Invalid upstream response
503 Service Unavailable      # Server overloaded
504 Gateway Timeout          # Upstream timeout
```

---

## 🛠️ Web Development Tools

### Local Development Servers

```bash
# Python
python -m http.server 8000

# PHP
php -S localhost:8000

# Node.js (with http-server)
npx http-server -p 8000

# Ruby
ruby -run -e httpd . -p 8000
```

### SSL/TLS

```bash
openssl s_client -connect example.com:443  # Test SSL
openssl x509 -in cert.pem -text            # View certificate
openssl genrsa -out key.pem 2048           # Generate private key
openssl req -new -key key.pem -out csr.pem # Generate CSR
```

### WebSocket Testing

```bash
# Using websocat
websocat ws://localhost:8080

# Using wscat (npm)
wscat -c ws://localhost:8080
```

---

## 🎯 Quick Reference

| Command | Description |
|---------|-------------|
| `ping google.com` | Test internet connection |
| `curl -I url` | GET headers only |
| `curl -X POST -d data url` | POST request |
| `dig domain.com` | DNS lookup |
| `ss -tulpn` | Show open ports |
| `lsof -i :8080` | Check who uses port 8080 |
| `scp file user@host:path` | Copy file via SSH |
| `rsync -av src/ dst/` | Sync directories |

---

## 🔧 Useful One-Liners

```bash
# Get public IP
curl ifconfig.me

# Check website response time
curl -w "@curl-format.txt" -o /dev/null -s <url>

# Download entire website
wget -r -np -k <url>

# Test all HTTP methods
for method in GET POST PUT DELETE; do curl -X $method <url>; done

# Monitor HTTP responses
watch -n 1 'curl -o /dev/null -s -w "%{http_code}\n" <url>'
```

---

> Last Updated: $(date +%Y-%m-%d)
