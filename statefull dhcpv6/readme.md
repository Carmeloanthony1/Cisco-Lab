# ipv6 dhcpv6 statefull configuration 
Project ini adalah simulasi jaringan multi-router yang menggunakan protokol ipv6 di Cisco Packet Tracer,
simulasi jaringan ini juga menerapkan statefull DHCPv6 untuk mengalokasikan IP pada end-device secara otomatis,
serta static routing untuk end-to-end routing sehingga dapat menghubungkan jaringan yang berbeda. 

Topologi :
Perangkat/interface/ipv6 address/
Router1/G0/0/1/2001:db8:acad:3::1/64/ - LAN
Router2/G0/0/0/2001:db8:acad:1::2/64/ - LAN, router utama 
Router1(1)/G0/0/0/2001:db8:acad:4::1/64/ - WLAN
Serta end device yang terhubung pada masing-masing router

#Konfigurasi 
1. Ipv6 unicast-routing
-----------------------
Setup DHCPv6 POOL
1. ipv6 dhcp pool POOL-ENV3/4
2. address prefix 2001:db8:acad:3::/64 atau :4::/64
3. dns-server 2001:4860:4860::8888
-----------------------
Menghubungkan ke interface 
1. ipv6 dhcp server POOL-ENV3/4
2. ipv6 nd managed-config-flag
3. end/write
------------------------
Static route 
1. Router kiri to :: (::/0 2001:db8:acad:1::1)
2. Router utama to :3:: (2001:db8:acad:3::/64 2001:db8:acad:1::2)
3. Router kanan to :: (::/0 2001:db8:acad:2::1)
4. ROuter utama to :4:: (2001:db8:acad:4::/64 2001:db8:acad:2::2)