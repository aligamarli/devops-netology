>1 - (1000 Mbps x 0.300 )/8 = TCP windows size = 37 500 000 bytes 

>2 - Если потеря 1%  =   1 / sqr(0.001) - вот во сколько раз 

>3 - 11,92 MB/S , размер фрейма не влияет на скорость. 

>4 - Учитывая что DNS кеш и ARP чистый. Обзор по некоторым strace участкам будем описывать процесс.
	openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libcurl.so.4", O_RDONLY|O_CLOEXEC) = 3  /// открывает библиотеки curl
	openat(AT_FDCWD, "/usr/lib/ssl/openssl.cnf", O_RDONLY) = 6 // открывает настройки ssl 
	openat(AT_FDCWD, "/etc/resolv.conf", O_RDONLY) = 6 // какой адрес придет и какой днс сервер ответит на запрос 
		ссылка на сам сервер если есть, или адресс DNS сервер(ов) на который будет идти рекурсивный запрос.
	connect(5, {sa_family=AF_INET, sin_port=htons(80), sin_addr=inet_addr("172.67.43.83")}, 16) = -1 EINPROGRESS (Operation now in progress) // установка соеденения 
	getsockopt(5, SOL_SOCKET, SO_ERROR, [0], [4]) = 0 // манурулятор флагамами TCP 
	getpeername(5, {sa_family=AF_INET, sin_port=htons(80), sin_addr=inet_addr("104.22.49.171")}, [128->16]) = 0  // Получает адресс с сокета с кем будет связватся
	getsockname(5, {sa_family=AF_INET, sin_port=htons(49440), sin_addr=inet_addr("192.168.111.128")}, [128->16]) = 0 // Получает адресс локального сокета который будет связыватся с внешным

>5 - DNS локальный, потом DNS провайдера, DNS .uk, DNS co.uk, 

>6 - /25 сетке - 126 хостов. 16384 подсетей с такой маской.

>7 - /23 - 510 адресов, /24 - 254 адреса

>8 - 131070 хостов соответсвует - /15 маске. количество подсетей можно сделать 2**9=512 с маской /15 если разделять 10.0.0.0/8 сеть
 
