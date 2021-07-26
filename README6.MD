### 1 - Причина временного зависания InActConn какое-то время из-за того что флаг tcp еще ждет закрытия, ipvsadm берет состояние из флага так прописано в ядре.
 'if (!(cp->flags & IP_VS_CONN_F_TEMPLATE)) {
 kernel-3.10.0-957.el7(RHEL7.6) related code
 698                 /* It is a normal connection, so decrease the inactconns
 699                    or activeconns counter */
 700                 if (cp->flags & IP_VS_CONN_F_INACTIVE) {
 701                         atomic_dec(&dest->inactconns);
 702                 } else {
 703                         atomic_dec(&dest->activeconns);
 ' )
 
### 2 - Такой конфиг работает и в продакшн залил.



global_defs {
    enable_script_security
}
vrrp_script myhealth {
    script "/bin/nc -z -w 2 127.0.0.1 80"
    interval 1
    user nobody
}
vrrp_instance VI_1 {
    state MASTER
    interface ens160
    virtual_router_id 5
    priority 109
    advert_int 1
    notify /etc/keepalived/keepalived-notify.sh root
    authentication {
        auth_type PASS
        auth_pass P@ssw0rd
    }
    virtual_ipaddress {
        192.168.15.5
    }
track_script {
        myhealth
    }
}
### 3 
> - Схема такая: 4 lb с keepalive , 2 VIP, 