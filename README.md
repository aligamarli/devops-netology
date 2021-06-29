# devops-netology
###First task 1
>Second modify

# Task 2.3 27.05.2021
>
# Task 3.1 28.05.2021
>#### Task3.1.5 
>Video Memory  4 
>Base Memory 1024 
>Processors 2
 
>#### Task3.1.5   
>customize the amount of memory on the VM:
>vbu.memory = "1024"
> >Либо в GUI

>#### Task3.1.8
> HISTSIZE - длина журнала
> > line 2403
>
>histcontrol=ignoreboth находится в файле .bashrc игорирует дубликаты и пробелы перед командами.
> 

>#### Task3.1.9
> {} для массивов и в расширенных списках
> > 258 line

>#### Task3.1.10
> touch {1..100000} - true
>
> touch {1..300000} - False "Argument too long"

>#### Task3.1.11
>[[ -d /tmp]] - проверает есть ли папка по данному пути. да или нет

>#### Task3.1.12 
> bash is /usr/bin/bash
> 
> bash is /bin/bash
> 
> bash is /tmp/new_path_derectory/bash/bash 
> 
> >Столько не пытался сделать последовательность не смог поменять
>#### Task3.1.13
> at команда выполняется в определенный момент
> batch команда выполняется в момент низкой нагрузке 1.5

# Task 3.2 16.06.2021
#### Task3.2.1
>cd команда является встроенной т.е она не как утилита а как часть баша
#### Task3.2.2
>grep -c some_string some_file 
#### Task3.2.3
>PID 1 PPID 0 - загрузчик который вызывает PID 1 
#### Task3.2.4
>ls 2>1 или 2>&1 и ошибку и просто вывод перенаправить как например логи
#### Task3.2.5
>input.sh #!bin/bash
> 
>echo"Hello World"
> 
 >>bash < input.sh > out.txt   ответ будет в файле out.txt запись Hello World
#### Task3.2.6
> bash < /dev/tty4  приблизительно так можно вывести чужие команды на свой bash
#### Task3.2.7
>bash 5>&1 ничего не показала, echo netology > /proc/$$/fd/5  выдает дескриптору 5 значение netology
#### Task3.2.8 
>????
#### Task3.2.9
>printenv
#### Task3.2.10
>cmdline файл для чтения который хранит полный путь команды пока не станет зомби.
>exe после 2,2 ядра Linux симлик который хранить выполненной команды, который может
#### Task3.2.11
>see see2 
#### Task3.2.12
> type -a bash гдн расположен файл
> >bash is /usr/bin/bash
> >bash is /bin/bash
> export PATH="/tmp/blabla:$PATH" добавляю папаку /tmp/blabla в переменную среды
> 
#### Task3.2.13
>echo 0 > /proc/sys/kernel/yama/ptrace_scope 
> по дефолту нужно активировать что-бы через reptyr потянуть процесс
>>Reptyr -T PID процесса 
#### Task3.2.14
>echo string | sudo tee /root/new_file  
> работает по той причине что, Эхо вывод делает а записать уже нужно права записи, tee получает stdout и правами root записывает. Сам shell запущен от обычного пользователя, и поэтому не может записать файл
####3.3.1
> system() chdir system call вызывает
> 
> chdir(/tmp")
> 
>
####3.3.2 
> strace file /dev/sda 2>&1 | grep "magic"
> 
> bopenat(AT_FDCWD, "/etc/magic", O_RDONLY) = 3
> 
> openat(AT_FDCWD, "/usr/share/misc/magic.mgc", O_RDONLY) = 3
> 

####3.3.3
> 2>&1 не аппендом, а перенаправлением один раз вывод в файл

####3.3.4
> Зомби не занимают никаких ресурсов, только в таблице процессовов. Ждет когда родитель прочитает его статус и удалит из списка.

####3.3.5
> sudo opensnoop-bpfcc

> 784    vminfo              4   0 /var/run/utmp 
> 
> 581    dbus-daemon        -1   2 /usr/local/share/dbus-1/system-services 
> 
> 581    dbus-daemon        18   0 /usr/share/dbus-1/system-services
> 
> 581    dbus-daemon        -1   2 /lib/dbus-1/system-services
> 
> 581    dbus-daemon        18   0 /var/lib/snapd/dbus-1/system-services/
> 
#####3.3.6
> openat(AT_FDCWD, "/proc/cpuinfo", O_RDONLY) = 3  -- для CPU
> 
> openat(AT_FDCWD, "/proc/version", O_RDONLY) = 3  -- uname -r это для ядра
> 
#####3.3.7
> test -d /tmp/some_dir; echo Hi правая часть это последовательная операция и ни как не звязанная с левой часть
> 
> test -d /tmp/some_dir && echo Hi Правая част сработает если первое условие будет TRUE
> 
> set -e test -d /tmp/some_dir &&  echo Hi  Тогда заработает
> 
#####3.3.8
> set -euxo pipefail
> 
> set -e моментально выходит если получает не нулевое значение
> 
> set -x Дебагинг вывод в шелл всех выполненных команд
> 
> set -u Считает переменные если эта переменная не была задекларирована, без этой не будет выскахвать про ошибку. Это опция выдает контретную ошибку файл. unbound variable"
> 
> set -o pipefail выдает то значение которое отличное от нуля, т.е если скрипт выполнился с ошибкой то в пайплайне тоже выйдет с ошибкой.
> 
#####3.3.9
> ps -o stat
> 
> STAT
> 
> Ss
> 
> R+
> 

> ps -aux если посмотреть можно увидеть процесы 
> s PID равнно SID это унаследованный

# Gitignore values




_Файлы игнора_

.config Файлы конфига системы

.key Файлы SSH сервера

.crash.log логи краша

.tmp временные файлы

.temp временные файлы

New line at Main Local

#New lines from IDE
code from IDE pycharm

#Third
3rd
