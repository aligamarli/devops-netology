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
>> [Link text Here](https://link-url-here.org)