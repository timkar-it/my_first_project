# my_first_project



sudo iptables -t nat -A PREROUTING -i eth0 -p tcp  --dport 80 -j DNAT --to-destination 10.0.0.3 # перенаправляем соединение eth0(10.0.0.1) по портам 80 в локальную сеть на 10.0.0.3

sudo iptables -t nat -A PREROUTING -i eth0 -p tcp  --dport 81 -j DNAT --to-destination 10.0.0.2:80# перенаправляем соединение eth0(10.0.0.1) по портам 81 в локальную сеть на 10.0.0.3

sudo iptables -A FORWARD -i eth0 -p tcp --dport 80,443 -J ACCEPT
 sudo iptables -A POSTROUTING -s 10.0.0.0/8 -o eth1 -j SNAT --to-source 1.1.1.1 # доступ хостам сети 10.0.0.0 на сетевую карту с внешним ип
 sudo iptables -t nat -A PREROUTING -i eth0 -p tcp  --dport 22 -j DNAT --to-destination 10.0.1.1 # проброс порта ssh
 sudo iptables -t nat -A PREROUTING -i eth0 -p tcp  --dport 22 -j DNAT --to-destination 10.0.1.2 # проброс порта 

Конфиг Nginx1
server {
        listen          80;
        server_name     nginx.example.net;
        
        return 301 https://nginx.example.net$request_uri;
    
}
Конфиг apache
<VirtualHost 80>
  ServerName apache.example.net
  ...
  SetEnvIf X-Forwarded-Proto https HTTPS=on
  ...
</VirtualHost>

 


