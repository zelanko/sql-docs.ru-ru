---
title: "Устранение неполадок SQL Server для Linux | Документы Microsoft"
description: "Содержит советы по устранению неполадок для использования 2017 г. SQL Server в Linux."
author: annashres
ms.author: anshrest
manager: craigg
ms.date: 01/18/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.workload: On Demand
ms.openlocfilehash: f56806313075865c53cbd3fc1f80c0d132804c04
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="troubleshoot-sql-server-on-linux"></a>Устранение неполадок SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом документе описывается устранение неполадок Microsoft SQL Server, работающим на платформе Linux или в контейнер Docker. При устранении неполадок SQL Server в Linux, не забудьте просмотреть поддерживаемые функции и известные ограничения в [SQL Server в заметках о выпуске Linux](sql-server-linux-release-notes.md).

## <a id="connection"></a> Устранение ошибок соединения
Если возникли затруднения при подключении к экземпляру SQL Server в Linux, существует несколько необходимо проверить следующее. 

- Убедитесь в том, что имя сервера или IP-адрес доступен с клиентского компьютера.

   > [!TIP]
   > Чтобы найти IP-адрес вашего компьютера Ubuntu, можно выполнить команду ifconfig, как показано в следующем примере:
   >
   >   ```bash
   >   sudo ifconfig eth0 | grep 'inet addr'
   >   ```
   > Для Red Hat можно использовать IP-адрес, как показано в следующем примере:
   >
   >   ```bash
   >   sudo ip addr show eth0 | grep "inet"
   >   ```
   > Единственным исключением из этого метода относится к виртуальным машинам Azure. Для виртуальных машин Azure [найти общедоступный IP-адрес для виртуальной Машины на портале Azure](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#connect).

- Если это применимо, проверьте, что был открыт в брандмауэре порт SQL Server (по умолчанию 1433).

- Для виртуальных машин Azure, убедитесь, что [правило группы безопасности сети для порта SQL Server по умолчанию](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#remote).

- Убедитесь, что имя пользователя и пароль не должен содержать опечаток, лишних пробелов и неправильный регистр символов.

- Попробуйте явно задать протокол и номер порта на имя сервера имеет следующий вид: **tcp:servername 1433**.

- Также могут вызвать проблемы с сетевым соединением, значения времени ожидания и ошибок подключения. После проверки того, сведения о соединении и подключение к сети, повторите попытку подключения.

## <a name="manage-the-sql-server-service"></a>Управление службой SQL Server

Ниже показано, как запустить, остановить, перезапустить и проверьте состояние службы SQL Server. 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Управление службой mssql server в Red Hat Enterprise Linux (RHEL) и Ubuntu 

Проверьте состояние службы SQL Server, с помощью этой команды.

   ```bash
   sudo systemctl status mssql-server
   ```

Можно остановить, запустить или перезапустить службу SQL Server, при необходимости с помощью следующих команд:

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl start mssql-server
   sudo systemctl restart mssql-server
   ```

### <a name="manage-the-execution-of-the-mssql-docker-container"></a>Управление выполнение в контейнер Docker mssql

Состояние и контейнер идентификатор последней созданной контейнера SQL Server Docker можно получить, выполнив следующую команду (идентификатор находится в **идентификатор КОНТЕЙНЕРА** столбца):

   ```bash
   sudo docker ps -l
   ```
   
Можно остановить или перезапустить службу SQL Server, при необходимости с помощью следующих команд:
   
   ```bash
   sudo docker stop <container ID>
   sudo docker restart <container ID>
   ```

> [!TIP]
> Дополнительные советы по устранению неполадок для Docker см. в разделе [контейнеры Устранение неполадок SQL Server Docker](sql-server-linux-configure-docker.md#troubleshooting).

## <a name="access-the-log-files"></a>Доступ к файлам журнала
   
Журнал ядра SQL Server в файл /var/opt/mssql/log/errorlog в установках Linux и Docker. Вы должны быть в режиме «суперпользователь» для просмотра этого каталога.

Программа установки регистрирует здесь: / var/opt/mssql/установки-< метка времени, представляющий время установки > можно просматривать файлы журнала ошибок с любой совместимый средства UTF-16, как «vim» или «cat» следующим образом: 

   ```bash
   sudo cat errorlog
   ```

При желании файлы можно преобразовать в UTF-8, чтобы ознакомиться с ними с помощью «больше» или «меньше» с помощью следующей команды:
   
   ```bash
   sudo iconv –f UTF-16LE –t UTF-8 <errorlog> -o <output errorlog file>
   ```
## <a name="extended-events"></a>Расширенные события

Расширенные события можно запрашивать с помощью команды SQL.  Дополнительные сведения о расширенных событиях можно найти [здесь](https://technet.microsoft.com/en-us/library/bb630282.aspx):

## <a name="crash-dumps"></a>Аварийные дампы 

Найдите файлы дампа в каталоге журналов в Linux. Проверьте в каталоге /var/opt/mssql/log на наличие дампов ядра Linux (. расширение tar.gz2) или минидампы SQL (с расширением расширением mdmp)

Для дампов 
   ```bash
   sudo ls /var/opt/mssql/log | grep .tar.gz2 
   ```

Для файлов дампа SQL 
   ```bash
   sudo ls /var/opt/mssql/log | grep .mdmp 
   ```
   
## <a name="start-sql-server-in-minimal-configuration-or-in-single-user-mode"></a>Запуск SQL Server в минимальной конфигурации или в однопользовательском режиме

### <a name="start-sql-server-in-minimal-configuration-mode"></a>Запуск SQL Server в режиме минимальной конфигурации
Эта функция полезна в случае, если установленные значения конфигурации (например, слишком большой объем выделяемой памяти) не позволяют выполнить запуск сервера.
  
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -f
   ```

### <a name="start-sql-server-in-single-user-mode"></a>Запуск SQL Server в однопользовательском режиме
В некоторых случаях может потребоваться запустить экземпляр SQL Server в однопользовательском режиме, используя параметр запуска -m. Например, может понадобиться изменить параметры конфигурации сервера, восстановить поврежденную базу данных master или другую системную базу данных. Например может потребоваться изменить параметры конфигурации сервера или восстановить поврежденную базу данных master или другую системную базу данных   

Запуск SQL Server в однопользовательском режиме
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m
   ```

Запуск SQL Server в однопользовательском режиме с помощью SQLCMD
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
   ```
  
> [!WARNING]  
>  Чтобы избежать проблем с запуском в дальнейшем, SQL Server в Linux следует запускать с указанием пользователя "mssql". Пример: "sudo -u mssql /opt/mssql/bin/sqlservr [параметры запуска]" 

Случайно с другим пользователем после запуска SQL Server, необходимо изменить владельца файлов базы данных SQL Server для пользователя «mssql» перед запуском SQL Server с systemd. Например для изменения владельца всех файлов базы данных в группе /var/opt/mssql для пользователя «mssql», выполните следующую команду

   ```bash
   chown -R mssql:mssql /var/opt/mssql/
   ```

## <a name="common-issues"></a>Распространенные проблемы

1. Не удается подключиться к удаленному экземпляру SQL Server.

   В разделе об устранении неполадок статьи, [подключение к SQL Server в Linux](#connection).

2. Ошибка: Имя узла должно быть 15 символов или меньше.

   Это известное проблему, которая происходит всякий раз, когда имя компьютера, при попытке установить пакет Debian SQL Server более 15 символов. В настоящее время не существует обходных путей Кроме изменение имени компьютера. Один из способов достижения этого является, изменив файл имя узла и перезагрузить компьютер. Следующие [руководство по веб-сайт](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) это раздел содержит подробное описание.

3. Сбросить пароль системного администрирования (SA).

   Если вы забыли пароль системного администратора (SA) или его потребуется сбросить по другой причине, выполните следующие действия.

   > [!NOTE]
   > Следующие шаги временно остановите службу SQL Server.

   Войдите на узел терминалов, выполните следующие команды и следуйте инструкциям на экране, чтобы сбросить пароль учетной записи SA:

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. Использование специальных символов в пароле.

   При использовании некоторых символов в пароле имя входа SQL Server может потребоваться экранировать их при их использовании в терминале Linux. $ Необходимо экранировать в любое время с помощью обратной косой черты используется в терминалов команда или сценарий:

   Не работает:

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   Works:

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   Ресурсы: [специальные символы](http://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](http://tldp.org/LDP/abs/html/escapingsection.html)

## <a name="support"></a>Поддержка

Поддержка доступна в сообществе и наблюдать инженеров. Дополнительную информацию используйте следующие ресурсы:

- [Администратор базы данных Exchange стека](https://dba.stackexchange.com/questions/tagged/sql-server): задать вопросы администрирования базы данных
- [Переполнение стека](http://stackoverflow.com/questions/tagged/sql-server): вопросы разработки
- [Форумы MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): задавайте технические вопросы
- [Отправить отзыв о](https://feedback.azure.com/forums/908035-sql-server): ошибки и запрос функции отчетов
- [Reddit](https://www.reddit.com/r/SQLServer/): обсудить SQL Server
