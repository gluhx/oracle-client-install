# oracle-client-install-ubuntu
#Здесь описан процесс установки Oracle Client на Ubuntu 24.04.2. Данная иснтрукция работает на эту версию ОС и выше.

#1. Устанавливаем программу для преобразования форматов различных систем управления пакетами Linux:
sudo apt update
sudo apt install alien

#2. Скачиваем лежащие в репозитории файлы и преобразовываем их формат:
sudo alien <path-to>/oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm
sudo alien <path-to>/oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm
sudo alien <path-to>/oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm

#3. В конец файла ~/.bashrc добавляем строки:
export LD_LIBRARY_PATH=/usr/lib/oracle/12.1/client64/lib/${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}
export ORACLE_HOME=/usr/lib/oracle/12.1/client64
export PATH=$PATH:$ORACLE_HOME/bin
#после чего перезапускаем систему

the scr is /usr/lib/x86_64-linux-gnu
