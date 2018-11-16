---
title: Устранение неполадок в SQL Server в Linux | Документация Майкрософт
description: Содержит советы по устранению неполадок для использования SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/01/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.openlocfilehash: 4bd04ee62af21255f40363de602c6461aeb350a6
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677923"
---
# <a name="troubleshoot-sql-server-on-linux"></a>Устранение неполадок в SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом документе описывается устранение неполадок с Microsoft SQL Server, работающих на платформе Linux или в контейнере Docker. При устранении неполадок SQL Server в Linux, не забудьте просмотреть поддерживаемые функции и известные ограничения в [SQL Server на заметки о выпуске Linux](sql-server-linux-release-notes.md).

> [!TIP]
> Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](sql-server-linux-faq.md).

## <a id="connection"></a> Устранение неполадок при сбоях подключения
Если у вас возникают затруднения при подключении к серверу SQL Server в Linux, чтобы проверить несколько моментов. 

- Убедитесь, что имя сервера или IP-адрес доступен на клиентском компьютере.

   > [!TIP]
   > Чтобы найти IP-адрес машины Ubuntu, можно выполнить команду ifconfig, как показано в следующем примере:
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

- Если необходимо, проверьте, что был открыт порт SQL Server (по умолчанию 1433) в брандмауэре.

- Для виртуальных машин Azure, убедитесь, что [правило группы безопасности сети для порта SQL Server по умолчанию](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#remote).

- Убедитесь, что имя пользователя и пароль не содержит опечаток или лишние пробелы или неправильный регистр.

- Попробуйте явно задать протокол и номер порта с именем сервера, как в следующем примере: **tcp:servername, 1433**.

- Также может вызывать проблемы с сетевым подключением, ошибки подключения и использование времени ожидания. После проверки того, сведения о подключении и подключения к сети, повторите попытку подключения.

## <a name="manage-the-sql-server-service"></a>Управление службой SQL Server

Ниже показано, как запустить, остановить, перезапустить и проверьте состояние службы SQL Server. 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Управление службой mssql-server в Red Hat Enterprise Linux (RHEL) и Ubuntu 

Проверьте состояние службы SQL Server, с помощью следующей команды:

   ```bash
   sudo systemctl status mssql-server
   ```

Можно остановить, запустить или перезапустить службу SQL Server, при необходимости с помощью следующих команд:

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl start mssql-server
   sudo systemctl restart mssql-server
   ```

### <a name="manage-the-execution-of-the-mssql-docker-container"></a>Управление выполнением mssql контейнера Docker

Идентификатор состояния и контейнер последний созданный контейнер SQL Server Docker можно получить, выполнив следующую команду (идентификатор находится в **идентификатор КОНТЕЙНЕРА** столбца):

   ```bash
   sudo docker ps -l
   ```
   
Можно остановить или перезапустить службу SQL Server, при необходимости с помощью следующих команд:
   
   ```bash
   sudo docker stop <container ID>
   sudo docker restart <container ID>
   ```

> [!TIP]
> Дополнительные советы по устранению неполадок для Docker, см. в разделе [Устранение неполадок SQL Server контейнерах](sql-server-linux-configure-docker.md#troubleshooting).

## <a name="access-the-log-files"></a>Доступ к файлам журнала
   
Журнал ядра SQL Server в файл /var/opt/mssql/log/errorlog в установках Docker и Linux. Вы должны быть в режиме «суперпользователь», чтобы просмотреть этот каталог.

Установщик регистрирует здесь: / var/opt/mssql/установки-< метка времени, представляющее время установки > можно просмотреть файлы журнала ошибок с помощью любого совместимого инструмента UTF-16 как «vim» или «cat» следующим образом: 

   ```bash
   sudo cat errorlog
   ```

При желании можно также преобразовать файлы UTF-8, чтобы ознакомиться с ними с помощью «больше» или «меньше», выполнив следующую команду:
   
   ```bash
   sudo iconv –f UTF-16LE –t UTF-8 <errorlog> -o <output errorlog file>
   ```
## <a name="extended-events"></a>Расширенные события

Расширенные события можно запрашивать с помощью команды SQL.  Дополнительные сведения о расширенных событиях можно найти [здесь](https://technet.microsoft.com/library/bb630282.aspx):

## <a name="crash-dumps"></a>Аварийные дампы 

Найдите файлы дампа в каталоге журнала в Linux. Проверьте в каталоге /var/opt/mssql/log на наличие дампов ядра Linux (. расширение tar.gz2) или мини-дампов SQL (с расширением расширением mdmp)

Для дампов ядра 
   ```bash
   sudo ls /var/opt/mssql/log | grep .tar.gz2 
   ```

For SQL dumps 
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

Если случайно запущено SQL Server с другим пользователем, необходимо изменить владельца файлов базы данных SQL Server для пользователя «mssql» перед запуском SQL Server с помощью systemd. Например чтобы изменить владение всеми файлами базы данных в группе /var/opt/mssql на пользователя «mssql», выполните следующую команду

   ```bash
   chown -R mssql:mssql /var/opt/mssql/
   ```

## <a name="rebuild-system-databases"></a>Перестроение системных баз данных
В качестве последнего средства вы можете перестроение базы данных master и модели баз данных обратно в версии по умолчанию.

> [!WARNING]
> Эти шаги позволят **к удалению всех данных системы SQL Server** , вы настроили! Сюда входят сведения о пользовательских баз данных (но не за базы данных пользователя, сами). Она также удаляет другие данные, хранящиеся в системных базах данных, включая следующие: сведения главного ключа, все сертификаты, загруженных в master, пароль имени входа SA, связанных с заданием сведения из базы данных msdb, сведения компонента DB Mail с msdb и параметры хранимой процедуры sp_configure. Используйте, только если понимаете последствия!

1. Остановка SQL Server.

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Запустите **sqlservr** с **force-setup** параметра. 

   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr --force-setup
   ```
   
   > [!WARNING]
   > См. приведенное выше предупреждение! Кроме того, необходимо запустить его в виде **mssql** пользователя, как показано ниже.

1. После появления сообщения «Восстановления завершена», нажмите клавиши CTRL + C. Это завершит работу SQL Server

1. Измените пароль SA.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-sa-password
   ```
   
1. Запустите SQL Server и изменить конфигурацию сервера. Это включает в себя восстановление или присоединив к пользовательским базам данных.

   ```bash
   sudo systemctl start mssql-server
   ```

## <a name="improve-performance"></a>Повысить производительность

Существует много факторов, влияющих на производительность, включая структуры базы данных, оборудования и пиковой нагрузки. Если вам нужно повысить производительность, начните с изучения рекомендаций в этой статье, [рекомендации по производительности и рекомендации по конфигурации для SQL Server в Linux](sql-server-linux-performance-best-practices.md). Затем изучите некоторые из доступных средств для устранения неполадок производительности.

- [Хранилище запросов](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Системные динамические административные представления (DMV)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
- [Панель мониторинга производительности в SQL Server Management Studio](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)

## <a name="common-issues"></a>Распространенные проблемы

1. Не удается подключиться к удаленному экземпляру SQL Server.

   См. в разделе об устранении неполадок статьи [подключение к SQL Server в Linux](#connection).

2. Ошибка: Имя узла должно быть 15 символов или меньше.

   Это известные проблема, которая происходит всякий раз, когда имя компьютера, на котором выполняется попытка установки SQL Server пакет Debian длиннее 15 символов. В настоящее время не существует обходных путей Кроме изменение имени компьютера. Одним из способов добиться этого является редактирования файла имя узла и перезагрузить компьютер. Следующие [руководство по веб-сайт](https://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) это раздел содержит подробное описание.

3. Сбросить пароль системного администрирования (SA).

   Если вы забыли пароль системного администратора (SA) или его потребуется сбросить по другой причине, выполните следующие действия.

   > [!NOTE]
   > Следующие действия временно остановите службу SQL Server.

   Войдите на узел терминалов, выполните следующие команды и следуйте инструкциям на экране, чтобы сбросить пароль системного Администратора.

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. Использование специальных символов в пароле.

   При использовании некоторых символов в пароле имени входа SQL Server, может потребоваться поставить обратную косую черту при их использовании в команде Linux в окне терминала. Например необходимо экранировать знак доллара ($) каждый раз, когда его использовать в скрипте команду или оболочки терминала:

   Не работает:

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   Works:

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   Ресурсы: [специальные символы](https://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](https://tldp.org/LDP/abs/html/escapingsection.html)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
