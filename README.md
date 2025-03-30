# oracle-client-install-ubuntu
#Здесь описан процесс установки Oracle Client на Ubuntu 24.04.2. Данная иснтрукция работает на эту версию ОС и выше.

#1. Устанавливаем программу для преобразования форматов различных систем управления пакетами Linux:
sudo apt update
sudo apt install alien

#2. Скачиваем лежащие в репозитории файлы и преобразовываем их формат:
sudo alien -i <path-to>/oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm
sudo alien -i <path-to>/oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm
sudo alien -i <path-to>/oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm

#3. В конец файла ~/.bashrc добавляем строки:
export LD_LIBRARY_PATH=/usr/lib/oracle/12.1/client64/lib/${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}
export ORACLE_HOME=/usr/lib/oracle/12.1/client64
export PATH=$PATH:$ORACLE_HOME/bin
export NLS_LANG=AMERICAN_CIS.UTF8
#после чего перезапускаем систему

#4. Устанавливаем необходимую библиотеку и переносим файл в нужную папку:
sudo apt update
sudo apt install libaio1t64
sudo cp /usr/lib/x86_64-linux-gnu/libaio.so.1t64 $ORACLE_HOME/lib
sudo mv $ORACLE_HOME/lib/libaio.so.1t64 $ORACLE_HOME/lib/libaio.so.1

#5. Далее проверяем подключение к БД(она должна быть запущена):
sqlplus <username>/<password>@//<dbhost>:1521/<SID>
