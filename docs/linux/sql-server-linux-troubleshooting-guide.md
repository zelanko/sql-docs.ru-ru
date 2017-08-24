---
title: "Устранение неполадок SQL Server для Linux | Документы Microsoft"
description: "Содержит советы по устранению неполадок для использования 2017 г. SQL Server в Linux."
author: annashres
ms.author: anshrest
manager: jhubbard
ms.date: 05/08/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 21b7d94bcf15e1ae2d99dd44f4b0030929b92111
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="troubleshoot-sql-server-on-linux"></a>Устранение неполадок SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

В этом документе описывается устранение неполадок Microsoft SQL Server, работающим на платформе Linux или в контейнер Docker. При устранении неполадок SQL Server в Linux, убедитесь в помните ограничения этой частной предварительной версии. Можно найти их в список [заметки о выпуске](sql-server-linux-release-notes.md).

## <a id="connection"></a>Устранение ошибок соединения
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
   > Единственным исключением из этого метода относится к виртуальным машинам Azure. Для виртуальных машин Azure [найти общедоступный IP-адрес для виртуальной Машины на портале Azure](sql-server-linux-azure-virtual-machine.md#connect).

- Если это применимо, проверьте, что был открыт в брандмауэре порт SQL Server (по умолчанию 1433).

- Для виртуальных машин Azure, убедитесь, что [правило группы безопасности сети для порта SQL Server по умолчанию](sql-server-linux-azure-virtual-machine.md#remote).

- Убедитесь, что имя пользователя и пароль не должен содержать опечаток, лишних пробелов и неправильный регистр символов.

- Попробуйте явно задать номер порта и протокола с указанием имени сервера следующим образом: **tcp:servername 1433**.

- Также могут вызвать проблемы с сетевым соединением, значения времени ожидания и ошибок подключения. После проверки того, сведения о соединении и подключение к сети, повторите попытку подключения.

## <a name="manage-the-sql-server-service"></a>Управление службой SQL Server

Ниже показано, как запустить, остановить, перезапустить и проверьте состояние службы SQL Server. 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Управление службой mssql server в Red Hat Enterprise Linux (RHEL) и Ubuntu 

Проверьте состояние состояние службы SQL Server, с помощью этой команды.

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

Состояние и контейнер идентификатор последней созданной контейнера SQL Server Docker можно получить, выполнив следующую команду (идентификатор будет в столбце «Идентификатор КОНТЕЙНЕРА»):

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

## <a name="common-issues"></a>Распространенные проблемы

1. Не удается подключиться к удаленному экземпляру SQL Server.

   В разделе об устранении неполадок см. в разделе [подключение к SQL Server в Linux](#connection).

2. Ошибка: Имя узла должно быть 15 символов или меньше.

   Это известное проблему, которая происходит всякий раз, когда имя компьютера, при попытке установить пакет Debian SQL Server более 15 символов. В настоящее время не существует обходных путей Кроме изменение имени компьютера. Один из способов достижения этого является, изменив файл имя узла и перезагрузить компьютер. Следующие [руководство по веб-сайт](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) это раздел содержит подробное описание.

3. Сбросить пароль системного администрирования (SA).

   Если вы забыли пароль системного администратора (SA) или его потребуется сбросить по другой причине, выполните следующие действия.

   > [!NOTE]
   > После выполнения этих действий останавливает службу SQL Server в временно.

   Войдите на узел терминалов, выполните следующие команды и следуйте инструкциям на экране, чтобы сбросить пароль учетной записи SA:

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. Использование специальных символов в пароле.

   При использовании некоторых символов в пароле имя входа SQL Server может потребоваться экранировать их при их использовании в терминале Linux. Необходимо экранировать $ в любое время с помощью обратной косой черты используется в терминалов команда или сценарий:

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
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): ошибки и запрос функции отчетов
- [Reddit](https://www.reddit.com/r/SQLServer/): обсудить SQL Server
