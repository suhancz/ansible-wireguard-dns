ansible-wireguard-dns
=====================

Name server exposing WireGuard clients

Role Variables
--------------

```
server:
  # server-specific config
  mtu: 1412 # optional - MTU for the WireGuard server
  cidr: 10.0.42.1/24 # mandatory - CIDR range the WireGuard server listens on
  publickey: oigftjkgjfnbkgjsdnsiungiusegiurbabjkan # mandatory, but advised to set in vars/secret.yml - the server's public key
  psk: v5utmw9utwumtp5ut5pttw598t # optional, advised to set in vars/secret.yml - the pre-shared key between the server and the client
  privatekey: v9w045jmt05u8ebp98up5m9yuabmsuyj # mandatory, but advised to set in vars/secret.yml - the server's private key
  address: this.is.my.server # mandatory, but advised to set in vars/secret.yml - the IP address or domain name the clients find the server at
  lport: 12345 # mandatory, but advised to set in vars/secret.yml - the port the WireGuard server listens on
dns_ip: 8.8.8.8 # mandatory, but advised to set in vars/secret.yml - the IP address of the DNS server the clients will use after connection
outputdir: ./outputdir # optional - the output directory to save the generated configs to
clients:
  # client-specific config
  client2: # name of the client for reference
    cidr: 10.0.42.254/32 # mandatory, but advised to set in vars/secret.yml - the IP address of the client on the VPN
    publickey: oigftjkgjfnbkgjsdnsiungiusegiurbabjkan # mandatory, but advised to set in vars/secret.yml - the client's public key
    psk: v5utmw9utwumtp5ut5pttw598t # optional, advised to set in vars/secret.yml - the pre-shared key between the server and the client
    privatekey: v9w045jmt05u8ebp98up5m9yuabmsuyj # mandatory, but advised to set in vars/secret.yml - the client's private key
    keepalive: 15 # optional - tunnel keepalive in seconds
    lport: 9876 # optional - the port the WireGuard client listens on
    mtu: 1412 # optional - MTU for the WireGuard client
```


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: server
      roles:
        - role: ansible-wireguard-dns
          tags:
            - server
            - client

License
-------

GPLv3
