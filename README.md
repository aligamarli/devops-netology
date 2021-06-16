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
>?????? Задача не понятна
#### Task3.2.13
>echo 0 > /proc/sys/kernel/yama/ptrace_scope 
> по дефолту нужно активировать что-бы через reptyr потянуть процесс
>>Reptyr -T PID процесса 
#### Task3.2.14
>echo string | sudo tee /root/new_file  
> работает по той причине что, Эхо вывод делает а записать уже нужно права записи, tee получает stdout и правами root записывает. Сам shell запущен от обычного пользователя, и поэтому не может записать файл
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
