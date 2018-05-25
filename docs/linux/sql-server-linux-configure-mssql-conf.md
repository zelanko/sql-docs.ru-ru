---
title: Настройка параметров SQL Server в Linux | Документы Microsoft
description: В этой статье описывается использование средства mssql conf для настройки параметров 2017 г. SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.openlocfilehash: 6369c3144a9ce641765358621027729ce235f69d
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Настройка SQL Server в Linux с помощью средства mssql conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

**MSSQL conf** — это сценарий конфигурации, который устанавливается вместе с SQL Server 2017 г. для Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu. Эту программу можно использовать для настройки следующих параметров:

|||
|---|---|
| [Агент](#agent) | Включить агент SQL Server |
| [Параметры сортировки](#collation) | Задайте новые параметры сортировки для SQL Server в Linux. |
| [Отзывы пользователей](#customerfeedback) | Выберите ли SQL Server отправляет отзыв в корпорацию Майкрософт. |
| [Профиль компонента Database Mail](#dbmail) | Настроить почтовый профиль по умолчанию базы данных для SQL Server в Linux |
| [Каталог данных по умолчанию](#datadir) | Перейдите в каталог по умолчанию для новых файлов данных базы данных SQL Server (.mdf). |
| [Каталог журнала по умолчанию](#datadir) | Изменение каталога по умолчанию для новых файлов журналов (LDF) базы данных SQL Server. |
| [По умолчанию каталог файлов базы данных master](#masterdatabasedir) | Изменение каталога по умолчанию для файлов базы данных master на существующую установку SQL.|
| [Имя файла по умолчанию базы данных master](#masterdatabasename) | Изменяет имя файлов базы данных master. |
| [Каталог дампа по умолчанию](#dumpdir) | Перейдите в каталог по умолчанию для новых дампы памяти и другие файлы устранения неполадок. |
| [Каталог журнала ошибок по умолчанию](#errorlogdir) | Изменяет каталог по умолчанию для новых файлов в журнале ошибок SQL Server, трассировка по умолчанию профилировщик, XE сеанс работоспособности системы и XE сеанса Hekaton. |
| [Каталог резервного копирования по умолчанию](#backupdir) | Перейдите в каталог по умолчанию для новых файлов резервных копий. |
| [Тип дампа](#coredump) | Выберите тип файла дампа памяти дампа для сбора. |
| [Высокий уровень доступности](#hadr) | Включите группы доступности. |
| [Локальный каталог аудита](#localaudit) | Значение каталога, чтобы добавить файлы локального аудита. |
| [Локаль](#lcid) | Назначение локали для SQL Server для использования. |
| [Ограничение памяти](#memorylimit) | Задайте ограничение памяти для SQL Server. |
| [TCP-порт](#tcpport) | Измените номер порта, где SQL Server прослушивает соединения. |
| [ПРОТОКОЛ TLS](#tls) | Настройка безопасности на транспортном уровне. |
| [Флаги трассировки](#traceflags) | Задайте флаги трассировки, которую планируется использовать службу. |

> [!TIP]
> Некоторые из этих параметров можно настроить с переменными среды. Дополнительные сведения см. в разделе [SQL Server можно настроить параметры с переменными среды,](sql-server-linux-configure-environment-variables.md).

## <a name="usage-tips"></a>Советы по использованию

* Для группы доступности AlwaysOn и кластеры общих дисков всегда внесения изменений конфигурации на каждом узле.

* В сценарии общий диск кластера, не пытайтесь перезапустить **mssql server** службу, чтобы применить изменения. SQL Server работает как приложение. Вместо этого переведите ресурс вне сети и затем снова подключены к сети.

* Эти примеры, выполните mssql-conf, укажите полный путь: **/opt/mssql/bin/mssql-conf**. Если выбрать для перехода к этому пути, вместо выполнения mssql conf в контексте текущего каталога: **. / mssql conf**.

## <a id="agent"></a> Включить агент SQL Server

**Sqlagent.enabled** установка включает [агента SQL Server](sql-server-linux-run-sql-server-agent-job.md). Агент SQL Server отключен по умолчанию. Если **sqlagent.enabled** отсутствует в файле параметров mssql.conf SQL Server внутренне предполагается, что агент SQL Server включен.

Чтобы изменить эти параметры, выполните следующие действия:

1. Включите агент SQL Server:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="collation"></a> Изменение параметров сортировки SQL Server

**Набор параметров сортировки** параметр изменяет значения параметров сортировки в любом из поддерживаемых параметров сортировки.

1. Первый [резервное копирование всех баз данных пользователя](sql-server-linux-backup-and-restore-database.md) на сервере.

1. Затем с помощью [sp_detach_db](../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) хранимой процедуры для отсоединения базы данных пользователя.

1. Запустите **набор параметров сортировки** параметр и следуйте указаниям:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. Mssql conf программа попытается изменить значение указанных параметров сортировки и перезапустите службу. Если имеются ошибки, откат параметров сортировки к предыдущему значению.

1. Восстановить резервные копии базы данных пользователя.

Список поддерживаемых параметров сортировки, запустите [sys.fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) функция: `SELECT Name from sys.fn_helpcollations()`.

## <a id="customerfeedback"></a> Настройка отзывов клиентов

**Telemetry.customerfeedback** изменения параметров ли SQL Server отправляет отзыв в корпорацию Майкрософт, или нет. По умолчанию это значение равно **true**. Чтобы изменить значение, выполните следующие команды:

1. Запустите сценарий mssql conf как корень с **задать** для **telemetry.customerfeedback**. Следующий пример отключает отзывы пользователей, указав **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

Дополнительные сведения см. в разделе [отзывы для SQL Server в Linux](sql-server-linux-customer-feedback.md).

## <a id="datadir"></a> Изменить расположение каталога данных или журнала по умолчанию

**Filelocation.defaultdatadir** и **filelocation.defaultlogdir** параметры изменить расположение, в котором создаются новые файлы базы данных и журнала. По умолчанию это расположение, /var/opt/mssql/data. Чтобы изменить эти параметры, выполните следующие действия:

1. Создайте каталог для новой базы данных файлы данных и журналов. В следующем примере создается новый **/tmp/данных** каталога:

   ```bash
   sudo mkdir /tmp/data
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/data
   sudo chgrp mssql /tmp/data
   ```

1. Используйте mssql conf, чтобы изменить каталог данных по умолчанию с **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdatadir /tmp/data
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Теперь все файлы базы данных для вновь создаваемых баз данных будут храниться в данном расположении. Если вы хотите изменить расположение файлов журналов (LDF) для новых баз данных, можно использовать команду следующий «набор»:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultlogdir /tmp/log
   ```

1. Эта команда также предполагается, что каталог журнала/tmp/существует и является в группе пользователей и групп **mssql**.


## <a id="masterdatabasedir"></a> Изменить расположение каталога файла базы данных master по умолчанию

**Filelocation.masterdatafile** и **filelocation.masterlogfile** изменения параметров расположения, где ядра SQL Server ищет файлы базы данных master. По умолчанию это расположение, /var/opt/mssql/data. 

Чтобы изменить эти параметры, выполните следующие действия:

1. Создайте каталог для новых файлов журнала ошибок. В следующем примере создается новый **/tmp/masterdatabasedir** каталога:

   ```bash
   sudo mkdir /tmp/masterdatabasedir
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
   ```

1. Используйте для изменения базы данных master каталог по умолчанию для главного файлов данных и журналов с mssql conf **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
   ```

1. Остановите службу SQL Server:

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Переместите master.mdf и masterlog.ldf: 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf 
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
   ```

1. Запустите службу SQL Server:

   ```bash
   sudo systemctl start mssql-server
   ```
   
> [!NOTE]
> Если SQL Server не удается найти файлы master.mdf и mastlog.ldf в указанном каталоге, будет автоматически создается копия шаблонный системных баз данных в указанном каталоге и SQL Server будет успешно запущен. Однако метаданные, такие как пользовательские базы данных, имен входа на сервер, сертификаты сервера, ключи шифрования, задания агента SQL Server или старый пароль имени входа SA, не обновляются в новую базу данных master. Необходимо будет остановить SQL Server и переместить старые master.mdf и mastlog.ldf на новое место указанного и запустить SQL Server, чтобы продолжить использование существующих метаданных. 


## <a id="masterdatabasename"></a> Измените имя файлов базы данных master.

**Filelocation.masterdatafile** и **filelocation.masterlogfile** изменения параметров расположения, где ядра SQL Server ищет файлы базы данных master. По умолчанию это расположение, /var/opt/mssql/data. Чтобы изменить эти параметры, выполните следующие действия:

1. Остановите службу SQL Server:

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Используйте mssql conf изменять имена ожидаемый главной базы данных master файлов данных и журналов с **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /var/opt/mssql/data/masternew.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.mastlogfile /var/opt/mssql/data /mastlognew.ldf
   ```

1. Изменение имени файлов данных и журнала базы данных master 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /var/opt/mssql/data/masternew.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /var/opt/mssql/data/mastlognew.ldf
   ```

1. Запустите службу SQL Server:

   ```bash
   sudo systemctl start mssql-server
   ```



## <a id="dumpdir"></a> Изменить расположение каталога дампа по умолчанию

**Filelocation.defaultdumpdir** изменения параметров по умолчанию, когда памяти и файлы дампа SQL создаются при каждом запуске сбоя. По умолчанию эти файлы создаются в /var/opt/mssql/log.

Чтобы настроить новое расположение, используйте следующие команды:

1. Создайте каталог для новых файлов дампа. В следующем примере создается новый **/tmp/dump** каталога:

   ```bash
   sudo mkdir /tmp/dump
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/dump
   sudo chgrp mssql /tmp/dump
   ```

1. Используйте mssql conf, чтобы изменить каталог данных по умолчанию с **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdumpdir /tmp/dump
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="errorlogdir"></a> Изменить расположение каталога файла журнала ошибок по умолчанию

**Filelocation.errorlogfile** изменения параметров расположения, где создан новый журнал ошибок, трассировка по умолчанию профилировщик, сеанс работоспособности системы XE и файлы сеанса XE Hekaton. По умолчанию это расположение, /var/opt/mssql/log. Каталог, в котором задается файл журнала ошибок SQL становится каталог журналов по умолчанию для других журналов.

Чтобы изменить эти параметры:

1. Создайте каталог для новых файлов журнала ошибок. В следующем примере создается новый **/tmp/журналы** каталога:

   ```bash
   sudo mkdir /tmp/logs
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/logs
   sudo chgrp mssql /tmp/logs
   ```

1. Позволяет изменить имя файла журнала ошибок по умолчанию с mssql conf **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.errorlogfile /tmp/logs/errorlog
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```


## <a id="backupdir"></a> Изменить расположение каталога резервного копирования по умолчанию

**Filelocation.defaultbackupdir** изменения параметров по умолчанию, где создаются файлы резервной копии. По умолчанию эти файлы создаются в /var/opt/mssql/data.

Чтобы настроить новое расположение, используйте следующие команды:

1. Создайте каталог для новых файлов резервных копий. В следующем примере создается новый **резервногокопирования/tmp/** каталога:

   ```bash
   sudo mkdir /tmp/backup
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/backup
   sudo chgrp mssql /tmp/backup
   ```

1. Измените каталог резервного копирования по умолчанию с помощью команды «set» с помощью mssql conf.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultbackupdir /tmp/backup
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="coredump"></a> Укажите параметры дампа памяти

При возникновении исключения в один из процессов SQL Server, SQL Server создает дамп памяти.

Существует два параметра для управления типом памяти дампов, что SQL Server собирает: **coredump.coredumptype** и **coredump.captureminiandfull**. Они относятся к две фазы захвата дампа памяти. 

Первый этап записи управляется **coredump.coredumptype** параметр, который определяет тип файла дампа, созданного во время исключения. Второй этап включается при **coredump.captureminiandfull** параметр. Если **coredump.captureminiandfull** задано значение true, дамп файла, указанного параметром **coredump.coredumptype** создается и также создается второй мини-дампа. Установка **coredump.captureminiandfull** false отключает попытка второй отслеживания.

1. Решите, следует ли записывать как полный, так и мини-дампов с **coredump.captureminiandfull** параметр.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    По умолчанию: **false**

1. Укажите тип файла дампа с **coredump.coredumptype** параметр.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    По умолчанию: **miniplus**

    В следующей таблице перечислены возможные **coredump.coredumptype** значения.

    | Тип | Описание |
    |-----|-----|
    | **Mini** | Мини — это наименьший тип файла дампа. Он использует сведения о системе Linux для определения потоков и модулей в процессе. Дамп содержит только стеки потоков среды узла и модулей. Он не содержит ссылки на память, косвенные или глобальных переменных. |
    | **miniplus** | MiniPlus аналогична mini, но он включает дополнительную память. Он поддерживает внутренних SQLPAL и хост-среды, добавление следующих областей памяти дампа:</br></br> -Различные globals</br> -Всю память сверх 64 ТБ</br> -Все имена регионов **/proc/$ pid и сопоставлений**</br> -Память косвенных из потоков и стеками</br> -Сведения о потоке</br> -Связанные Teb элемента и его Peb</br> -Сведения о модуле</br> -VMM и VAD дерева |
    | **Фильтрация** | Отфильтрованные использует основе вычитания разработки, где всю память в процессе будет включен, если не исключены явным образом. Структура понимает внутренних SQLPAL и среде узла, за исключением некоторых регионах из дампа.
    | **Полный** | Полный дамп процесса завершения, включающий все области находится в **/proc/$ pid и сопоставлений**. Это не управляется **coredump.captureminiandfull** параметр. |

## <a id="dbmail"></a> Настроить почтовый профиль по умолчанию базы данных для SQL Server в Linux

**Sqlpagent.databasemailprofile** позволяет установить профиль электронной почты базы данных по умолчанию для оповещений по электронной почте.

```bash
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile <profile_name>
```
## <a id="hadr"></a> Высокий уровень доступности

**Hadr.hadrenabled** параметр активирует группы доступности на экземпляре SQL Server. Следующая команда включает группы доступности, задав **hadr.hadrenabled** значение 1. Необходимо перезапустить SQL Server для параметра вступили в силу.

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

Сведения, как он используется с группами доступности см. в следующих двух разделов.

- [Настройка группы доступности для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md)
- [Настройка группы доступности чтения шкалы для SQL Server в Linux](sql-server-linux-availability-group-configure-rs.md)

## <a id="localaudit"></a> Каталог локального аудита набора

**Telemetry.userrequestedlocalauditdirectory** параметр включает локальные аудита и позволяет задать каталог, где локальных журналов аудита на создаются.

1. Создайте целевой каталог для локальных журналов. В следующем примере создается новый **/tmp/аудита** каталога:

   ```bash
   sudo mkdir /tmp/audit
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Запустите сценарий mssql conf как корень с **задать** для **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

Дополнительные сведения см. в разделе [отзывы для SQL Server в Linux](sql-server-linux-customer-feedback.md).

## <a id="lcid"></a> Изменение языка SQL Server

**Language.lcid** изменения параметров языка SQL Server любой поддерживаемым идентификатором языка (LCID). 

1. Следующий пример изменяет языковой стандарт на французский (1036):

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. Перезапустите службу SQL Server для применения изменений:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a> Задать ограничение памяти

**Memory.memorylimitmb** настройки элементов управления объем доступной физической памяти (в МБ) для SQL Server. Значение по умолчанию — 80% физической памяти.

1. Запустите сценарий mssql conf как корень с **задать** для **memory.memorylimitmb**. В следующем примере изменяется доступной памяти для SQL Server 3,25 ГБ (3328 МБ).

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. Перезапустите службу SQL Server для применения изменений:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="tcpport"></a> Изменение порта TCP

**Network.tcpport** изменения параметров TCP-порт, где SQL Server прослушивает соединения. Этот порт по умолчанию равно 1433. Чтобы изменить порт, выполните следующие команды:

1. Запустите сценарий mssql conf корневым каталогом с помощью команды «набор» для «network.tcpport»:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

1. При подключении к SQL Server, необходимо указать другой номер порта с помощью запятой (,) после имени узла или IP-адрес. Например для подключения с помощью SQLCMD, используется следующая команда:

   ```bash
   sqlcmd -S localhost,<new_tcp_port> -U test -P test
   ```

## <a id="tls"></a> Укажите параметры TLS

Следующие параметры настройки TLS для экземпляра SQL Server на ОС Linux.

|Параметр |Описание |
|--- |--- |
|**Network.ForceEncryption** |Если значение равно 1, затем [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] заставляет все соединения, должны быть зашифрованы. По умолчанию этого параметра равно 0. |
|**Network.tlscert** |Абсолютный путь к сертификату файла, который [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует для TLS. Пример: `/etc/ssl/certs/mssql.pem` файл сертификата должен быть доступен для учетной записи mssql. Корпорация Майкрософт рекомендует ограничения доступа к файлу с помощью `chown mssql:mssql <file>; chmod 400 <file>`. |
|**Network.tlskey** |Абсолютный путь к закрытому ключу файла, который [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует для TLS. Пример: `/etc/ssl/private/mssql.key` файл сертификата должен быть доступен для учетной записи mssql. Корпорация Майкрософт рекомендует ограничения доступа к файлу с помощью `chown mssql:mssql <file>; chmod 400 <file>`. |
|**Network.tlsprotocols** |Список разделенных запятыми из какой TLS протоколы допускаемым сервером SQL Server. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] всегда пытается согласовать надежный протокол разрешенных. Если клиент не поддерживает любой допустимый протокол [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] отклоняет попытки подключения.  Для обеспечения совместимости по умолчанию (1.2, 1.1, 1.0) разрешены все поддерживаемые протоколы.  Если клиенты поддерживает TLS 1.2, корпорация Майкрософт рекомендует, позволяя только TLS 1.2. |
|**Network.tlsciphers** |Указывает, какие шифры допускаемых [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для TLS. Эта строка должен быть отформатирован в [OpenSSL в формате списка шифра](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). Как правило нет необходимости менять этот параметр. <br /> По умолчанию допускаются следующие шифров: <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **Network.kerberoskeytabfile** |Путь к файлу keytab Kerberos |

Пример использования параметров TLS см. в разделе [шифрование соединений с SQL Server в Linux](sql-server-linux-encrypted-connections.md).

## <a id="traceflags"></a> Включение или отключение флага трассировки

Это **traceflag** параметр включает или отключает флаги трассировки для запуска службы SQL Server. Для включения или отключения traceflag используйте следующие команды:

1. Включите traceflag, используя следующую команду. Например, Traceflag 1234:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 on
   ```

1. Можно включить несколько флаги трассировки, указав их отдельно.

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 2345 3456 on
   ```

1. Аналогичным образом, можно отключить один или несколько включены флаги трассировки, указав их и добавив **off** параметр:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 2345 3456 off
   ```

1. Перезапустите службу SQL Server для применения изменений:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="remove-a-setting"></a>Удалите параметр

Чтобы отменить любое задание осуществляется с `mssql-conf set`, вызовите **mssql conf** с `unset` и имя параметра. Это приведет к очистке параметра, фактически возвращением к значению по умолчанию.

1. В следующем примере удаляется **network.tcpport** параметр.

   ```bash
   sudo /opt/mssql/bin/mssql-conf unset network.tcpport
   ```

1. Перезапустите службу SQL Server.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="view-current-settings"></a>Просмотр текущих параметров

Для просмотра любого настроены параметры, выполните следующую команду, чтобы вывести содержимое **mssql.conf** файла:

```bash
sudo cat /var/opt/mssql/mssql.conf
```

Обратите внимание, что все параметры, не отображаются в этом файле используют значения по умолчанию. В следующем разделе приводится образец **mssql.conf** файла.

## <a name="mssqlconf-format"></a>Формат MSSQL.conf

Следующие **/var/opt/mssql/mssql.conf** файл содержит пример для каждого параметра. Этот формат можно использовать для внесения изменений вручную **mssql.conf** файла при необходимости. Если вручную изменить файл, необходимо перезапустить SQL Server перед применением изменений. Для использования **mssql.conf** файла с помощью Docker, необходимо иметь Docker [сохранить данные](sql-server-linux-configure-docker.md). Сначала необходимо добавить полный **mssql.conf** файл в каталог на сервере, а затем запустите контейнер. Приводится пример приведен в [отзывы](sql-server-linux-customer-feedback.md).

```ini
[EULA]
accepteula = Y

[coredump]
captureminiandfull = true
coredumptype = full

[filelocation]
defaultbackupdir = /var/opt/mssql/data/
defaultdatadir = /var/opt/mssql/data/
defaultdumpdir = /var/opt/mssql/data/
defaultlogdir = /var/opt/mssql/data/

[hadr]
hadrenabled = 0

[language]
lcid = 1033

[memory]
memorylimitmb = 4096

[network]
forceencryption = 0
ipaddress = 10.192.0.0
kerberoskeytabfile = /var/opt/mssql/secrets/mssql.keytab
tcpport = 1401
tlscert = /etc/ssl/certs/mssql.pem
tlsciphers = ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA
tlskey = /etc/ssl/private/mssql.key
tlsprotocols = 1.2,1.1,1.0

[sqlagent]
databasemailprofile = default
errorlogfile = /var/opt/mssql/log/sqlagentlog.log
errorlogginglevel = 7

[telemetry]
customerfeedback = true
userrequestedlocalauditdirectory = /tmp/audit

[traceflag]
traceflag0 = 1204
traceflag1 = 2345
traceflag = 3456
```

## <a name="next-steps"></a>Следующие шаги

Вместо этого использовать переменные среды, чтобы сделать некоторые из этих изменений конфигурации, в разделе [SQL Server можно настроить параметры с переменными среды,](sql-server-linux-configure-environment-variables.md).

Другие средства управления и сценарии см. в разделе [управления SQL Server в Linux](sql-server-linux-management-overview.md).
