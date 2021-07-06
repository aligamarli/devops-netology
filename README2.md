>#### 3.4.1
Файл юнита как службы и авто загрузки node_exporterd
> > cat node_exporter.service
> 
>Node Exporter service file — /etc/systemd/system/node_exporter.service
> 
>[Unit]
>Description=Node Exporter
> 
>Wants=network-online.target
> 
>After=network-online.target
> 

>[Service]
> 
>User=node_exporter
> 
>Group=node_exporter
>
>Type=simple
>
>ExecStart=/usr/local/bin/node_exporter

>[Install]
> 
>WantedBy=multi-user.target
> 

>>Для удобства 2 машини под node_exporter и прометеус
>> [prometheus.yml](https://github.com/aligamarli/devops-netology/blob/07602e067313fa0304bb670eb1afd909540329d5/p

##systemctl status node_exporter.service
● node_exporter.service - Node Exporter
   Loaded: loaded (/etc/systemd/system/node_exporter.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2021-07-06 06:36:47 UTC; 25min ago
 Main PID: 685 (node_exporter)
   CGroup: /system.slice/node_exporter.service
           └─685 /usr/local/bin/node_exporter

Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:113 collector=thermal_zone
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:113 collector=time
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:113 collector=timex
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:113 collector=udp_queues
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:113 collector=uname
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:113 collector=vmstat
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:113 collector=xfs
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:113 collector=zfs
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.961Z caller=node_exporter.go:195 msg="Listening on" address=:9100
Jul 06 06:36:47 localhost.localdomain node_exporter[685]: level=info ts=2021-07-06T06:36:47.969Z caller=tls_config.go:191 msg="TLS is disabled." http2=false
#3.4.2
>rate(node_cpu_seconds_total{job="node-exporter"}[5m]) >
> 
> node_memory_MemAvailable_bytes
> 
> node_disk_io_now

####3.4.3
[screnshoot_of_netdata](https://github.com/aligamarli/devops-netology/blob/190a7bf1cbc1e2f1d3631a8231c156d0d823470e/Screenshot%202021-07-06%20160859.png)

####3.4.4
>sudo dmesg | grep "Hypervisor detected"
> 
> [    0.000000] Hypervisor detected: VMware
