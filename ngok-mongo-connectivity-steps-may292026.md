Architecture (what we want)
1. MongoDB runs on Windows (localhost:27017)
2. Start ngrok on Windows CMD
```ruby
ngrok tcp 127.0.0.1:27017
```
```
copy:
tcp://0.tcp.in.ngrok.io:22348 -> 127.0.0.1:27017
```
```ruby
ngrok                                                                                                                                                                                            (Ctrl+C to quit)
�  One gateway for every AI model. Available in early access *now*: https://ngrok.com/r/ai

Session Status                online
Account                       kyngitwrk@gmail.com (Plan: Free)
Version                       3.39.1-msix-stable
Region                        India (in)
Latency                       21ms
Web Interface                 http://127.0.0.1:4040
Forwarding                    tcp://0.tcp.in.ngrok.io:22348 -> localhost:27017

Connections                   ttl     opn     rt1     rt5     p50     p90
                              4       0       0.03    0.01    0.04    11.00
```
3. Test ngrok using Windows mongosh.exe From WSL:

Start powershell and launch WSL

```ruby
cd /mnt/c/Users/VENKATESHREDDY/AppData/Local/Programs/mongosh
```
```ruby
./mongosh.exe "mongodb://0.tcp.in.ngrok.io:22348/?directConnection=true"
```
```
vereddy@LAPTOP-CB73EHU6:/mnt/c/Users/VENKATESHREDDY/AppData/Local/Programs/mongosh$ ./mongosh.exe "mongodb://0.tcp.in.ngrok.io:22348/?directConnection=true"
Current Mongosh Log ID: 6a199a33f08f2b4ad2abc113
Connecting to:          mongodb://0.tcp.in.ngrok.io:22348/?directConnection=true&appName=mongosh+2.8.3
Using MongoDB:          8.3.2
Using Mongosh:          2.8.3

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/

------
   The server generated these startup warnings when booting
   2026-05-29T16:55:33.079+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

test>
```

4. For Atlas Live Migration source URI

Use:

mongodb://0.tcp.in.ngrok.io:22348/admin?directConnection=true

But your MongoDB warning says access control is not enabled. 
For migration testing that may connect without username/password, but for Atlas Live Migration you should enable auth and create a migration user.




