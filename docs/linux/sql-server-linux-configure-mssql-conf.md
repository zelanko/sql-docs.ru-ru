---
title: Настройка параметров SQL Server в Linux
description: В этой статье описывается, как использовать средство mssql-conf для настройки параметров SQL Server на Linux.
author: VanMSFT
ms.author: vanto
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.openlocfilehash: ac1f88377b15bf8bd4a92a5dd705716db55deaaf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077602"
---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Настройка SQL Server в Linux с помощью средства mssql-conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

**MSSQL-conf** — это сценарий конфигурации, который устанавливается вместе с SQL Server 2017 для Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu. Эта программа позволяет задать следующие параметры:

|||
|---|---|
| [Агент](#agent) | Включите агент SQL Server. |
| [Параметры сортировки](#collation) | Задайте новые параметры сортировки для SQL Server в Linux. |
| [Отзывы клиентов](#customerfeedback) | Выберите ли SQL Server отправляет отзыв в корпорацию Майкрософт. |
| [Профиль компонента Database Mail](#dbmail) | Настройте почтовый профиль по умолчанию базы данных для SQL Server в Linux. |
| [Каталог данных по умолчанию](#datadir) | Перейдите в каталог по умолчанию для новых файлов данных базы данных SQL Server (.mdf). |
| [Каталог журналов по умолчанию](#datadir) | Изменяет каталог по умолчанию для новых файлов журналов (LDF) базы данных SQL Server. |
| [Каталог базы данных master по умолчанию](#masterdatabasedir) | Изменение каталога по умолчанию для главной базы данных и журнала файлов.|
| [Имя файла базы данных master по умолчанию](#masterdatabasename) | Изменяет имя файлов базы данных master. |
| [Каталог дампа по умолчанию](#dumpdir) | Перейдите в каталог по умолчанию для новых дампы памяти и другие файлы для устранения неполадок. |
| [Каталог журналов ошибок по умолчанию](#errorlogdir) | Изменяет каталог по умолчанию для новых файлов в журнале ошибок SQL Server, трассировка Profiler по умолчанию, XE сеанс работоспособности системы и Hekaton сеанса XE. |
| [Резервным каталогом по умолчанию](#backupdir) | Перейдите в каталог по умолчанию для новых файлов резервной копии. |
| [Тип дампа](#coredump) | Выберите тип файла дампа памяти дампа для сбора. |
| [Высокий уровень доступности](#hadr) | Включите группы доступности. |
| [Каталогу локального аудита](#localaudit) | Задает каталог для добавления файлов локального аудита. |
| [Локаль](#lcid) | Задание локали для SQL Server для использования. |
| [Предел памяти](#memorylimit) | Задайте ограничение памяти для SQL Server. |
| [TCP-порт](#tcpport) | Изменение порта, где SQL Server прослушивает соединения. |
| [TLS](#tls) | Настройте безопасность на транспортном уровне. |
| [Флаги трассировки](#traceflags) | Набор флагов трассировки, который планируется использовать службу. |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

**MSSQL-conf** — это сценарий конфигурации, который устанавливается вместе с [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] для Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu. Эта программа позволяет задать следующие параметры:

|||
|---|---|
| [Агент](#agent) | Включить агент SQL Server |
| [Параметры сортировки](#collation) | Задайте новые параметры сортировки для SQL Server в Linux. |
| [Отзывы клиентов](#customerfeedback) | Выберите ли SQL Server отправляет отзыв в корпорацию Майкрософт. |
| [Профиль компонента Database Mail](#dbmail) | Настройте почтовый профиль по умолчанию базы данных для SQL Server в Linux. |
| [Каталог данных по умолчанию](#datadir) | Перейдите в каталог по умолчанию для новых файлов данных базы данных SQL Server (.mdf). |
| [Каталог журналов по умолчанию](#datadir) | Изменяет каталог по умолчанию для новых файлов журналов (LDF) базы данных SQL Server. |
| [Каталог файлов базы данных master по умолчанию](#masterdatabasedir) | Изменение каталога по умолчанию для файлов базы данных master на существующую установку SQL.|
| [Имя файла базы данных master по умолчанию](#masterdatabasename) | Изменяет имя файлов базы данных master. |
| [Каталог дампа по умолчанию](#dumpdir) | Перейдите в каталог по умолчанию для новых дампы памяти и другие файлы для устранения неполадок. |
| [Каталог журналов ошибок по умолчанию](#errorlogdir) | Изменяет каталог по умолчанию для новых файлов в журнале ошибок SQL Server, трассировка Profiler по умолчанию, XE сеанс работоспособности системы и Hekaton сеанса XE. |
| [Резервным каталогом по умолчанию](#backupdir) | Перейдите в каталог по умолчанию для новых файлов резервной копии. |
| [Тип дампа](#coredump) | Выберите тип файла дампа памяти дампа для сбора. |
| [Высокий уровень доступности](#hadr) | Включите группы доступности. |
| [Каталогу локального аудита](#localaudit) | Задает каталог для добавления файлов локального аудита. |
| [Локаль](#lcid) | Задание локали для SQL Server для использования. |
| [Предел памяти](#memorylimit) | Задайте ограничение памяти для SQL Server. |
| [Служба координатора распределенных транзакций](#msdtc) | Настройка и устранение неполадок MSDTC на платформе Linux. |
| [MLServices лицензионные соглашения.](#mlservices-eula) | Примите лицензионные соглашения Python и R для mlservices пакетов. Применимо к SQL Server 2019 только.|
| [outboundnetworkaccess](#mlservices-outbound-access) |Разрешить исходящий сетевой доступ для [mlservices](sql-server-linux-setup-machine-learning.md) модули R, Python и Java.|
| [TCP-порт](#tcpport) | Изменение порта, где SQL Server прослушивает соединения. |
| [TLS](#tls) | Настройте безопасность на транспортном уровне. |
| [Флаги трассировки](#traceflags) | Набор флагов трассировки, который планируется использовать службу. |

::: moniker-end

> [!TIP]
> Некоторые из этих параметров можно также настроить с помощью переменных среды. Дополнительные сведения см. в разделе [SQL Server можно настроить параметры с переменными среды](sql-server-linux-configure-environment-variables.md).

## <a name="usage-tips"></a>Советы по использованию

* Для групп доступности AlwaysOn и общих томах кластера всегда внести аналогичные изменения конфигурации на каждом узле.

* Для сценария общий диск кластера, не пытайтесь перезапустить **mssql-server** службы, чтобы применить изменения. SQL Server выполняется как приложение. Вместо этого переведите ресурс вне сети и затем восстановлен.

* Эти примеры запуска mssql-conf, указав полный путь: **/opt/mssql/bin/mssql-conf**. Если вы решили перейти к этому пути, вместо этого, запустите mssql-conf в контексте текущего каталога: **. / mssql-conf**.

## <a id="agent"></a> Включить агент SQL Server

**Sqlagent.enabled** установка включает [агента SQL Server](sql-server-linux-run-sql-server-agent-job.md). Агент SQL Server функция отключена по умолчанию. Если **sqlagent.enabled** отсутствует в файле параметров mssql.conf, после чего SQL Server внутренне предполагается, что агент SQL Server отключена.

Чтобы изменить этот параметр, сделайте следующее:

1. Включите агент SQL Server:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
   ```

2. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="collation"></a> Изменение параметров сортировки SQL Server

**Набора параметров сортировки** параметр изменяется значение параметров сортировки на любой из поддерживаемых параметров сортировки.

1. Первый [резервное копирование всех баз данных пользователя](sql-server-linux-backup-and-restore-database.md) на сервере.

1. Затем с помощью [sp_detach_db](../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) хранимой процедуры для отсоединения базы данных пользователя.

1. Запустите **набора параметров сортировки** параметр и следуйте инструкциям на экране:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. Mssql-conf программа попытается изменить значение указанных параметров сортировки и перезапустите службу. При возникновении любой ошибки, откат параметров сортировки к предыдущему значению.

1. Восстановите резервные копии базы данных пользователя.

Для получения списка поддерживаемых параметров сортировки, запустите [sys.fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) функция: `SELECT Name from sys.fn_helpcollations()`.

## <a id="customerfeedback"></a> Настройка отзывов пользователей

**Telemetry.customerfeedback** параметр изменения SQL Server отправляет отзыв в корпорацию Майкрософт, или нет. По умолчанию это значение присваивается **true** для всех выпусков. Чтобы изменить значение, выполните следующие команды:

> [!IMPORTANT]
> Можно не отключить отзывов пользователей бесплатно выпусков SQL Server, Express и Developer.

1. Запустите сценарий mssql-conf в качестве привилегированного пользователя с **задать** команду для **telemetry.customerfeedback**. Следующий пример отключает отзывы клиентов, указав **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

Дополнительные сведения см. в разделе [отзывы по SQL Server в Linux](sql-server-linux-customer-feedback.md) и [заявление о конфиденциальности SQL Server](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a id="datadir"></a> Изменение расположения каталога данных или журнала по умолчанию

**Filelocation.defaultdatadir** и **filelocation.defaultlogdir** параметров изменить расположение, где создаются новые файлы базы данных и журнала. По умолчанию это расположение, /var/opt/mssql/data. Чтобы изменить эти параметры, используйте следующие действия:

1. Создайте целевой каталог для новой базы данных файлы данных и журналов. В следующем примере создается новый **/tmp/данных** каталог:

   ```bash
   sudo mkdir /tmp/data
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/data
   sudo chgrp mssql /tmp/data
   ```

1. Используйте mssql-conf, чтобы изменить каталог по умолчанию с **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdatadir /tmp/data
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Теперь все файлы базы данных для вновь создаваемых баз данных будут храниться в это расположение. Если вы хотите изменить расположение файлов журналов (LDF) новые базы данных, можно использовать команды ниже «set»:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultlogdir /tmp/log
   ```

1. Эта команда также предполагается, что каталог/tmp/журнала существует и что он находится в разделе пользователей и групп **mssql**.


## <a id="masterdatabasedir"></a> Изменить расположение каталога файла базы данных master по умолчанию

**Filelocation.masterdatafile** и **filelocation.masterlogfile** задание изменения расположения, где ядра SQL Server выполняет поиск файлов базы данных master. По умолчанию это расположение, /var/opt/mssql/data.

Чтобы изменить эти параметры, используйте следующие действия:

1. Создайте целевой каталог для новых файлов журнала ошибок. В следующем примере создается новый **/tmp/masterdatabasedir** каталог:

   ```bash
   sudo mkdir /tmp/masterdatabasedir
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
   ```

1. Используйте mssql-conf, чтобы изменить каталог базы данных master по умолчанию для главного файлов данных и журналов с **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
   ```

   > [!NOTE]
   > В дополнение к перемещению основных данных и файлов журнала, это также переводит расположение по умолчанию для всех других системных баз данных.

1. Остановка службы SQL Server:

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
   > Если SQL Server не удается найти файлы master.mdf и mastlog.ldf в указанном каталоге, шаблонного копии системных баз данных будет автоматически создан в указанный каталог и SQL Server будет успешно запущен. Тем не менее метаданные, такие как пользовательских баз данных, имен входа на сервер, сертификаты сервера, ключи шифрования, заданий агента SQL Server или старый пароль имени входа SA не будет обновляться в новой базе данных master. Необходимо остановить SQL Server и переместить старые master.mdf и mastlog.ldf на новое место указанного и запустить SQL Server, чтобы продолжить использование существующих метаданных.
 
## <a id="masterdatabasename"></a> Изменить имя файлов базы данных master

**Filelocation.masterdatafile** и **filelocation.masterlogfile** задание изменения расположения, где ядра SQL Server выполняет поиск файлов базы данных master. Это также можно использовать для изменения имени главной базы данных и журнала файлов. 

Чтобы изменить эти параметры, используйте следующие действия:

1. Остановка службы SQL Server:

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Используйте mssql-conf, чтобы изменить имена ожидаемый главной базы данных master файлов данных и журналов с **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /var/opt/mssql/data/masternew.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.mastlogfile /var/opt/mssql/data/mastlognew.ldf
   ```

   > [!IMPORTANT]
   > Можно изменить имя базы данных master и только после успешного запуска SQL Server, файлы журнала. Перед начального запуска SQL Server ожидает, что файлы называться master.mdf и mastlog.ldf.

1. Измените имя файлов данных и журналов базы данных master 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /var/opt/mssql/data/masternew.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /var/opt/mssql/data/mastlognew.ldf
   ```

1. Запустите службу SQL Server:

   ```bash
   sudo systemctl start mssql-server
   ```

## <a id="dumpdir"></a> Изменение расположения каталога дампа по умолчанию

**Filelocation.defaultdumpdir** изменения параметров по умолчанию, когда объем памяти и дампы SQL создаются каждый раз при обнаружении сбоя. По умолчанию эти файлы создаются в /var/opt/mssql/log.

Чтобы настроить это расположение, используйте следующие команды:

1. Создайте целевой каталог для новых файлов дампа. В следующем примере создается новый **/tmp/дампа** каталог:

   ```bash
   sudo mkdir /tmp/dump
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/dump
   sudo chgrp mssql /tmp/dump
   ```

1. Используйте mssql-conf, чтобы изменить каталог по умолчанию с **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdumpdir /tmp/dump
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="errorlogdir"></a> Изменить расположение каталога файла журнала ошибок по умолчанию

**Filelocation.errorlogfile** задание изменения расположения, где создан новый журнал ошибок, трассировка профилировщика по умолчанию, сеанс работоспособности системы XE и файлы сеанса XE Hekaton. По умолчанию это расположение, /var/opt/mssql/log. Каталог, в котором задается файл журнала ошибок SQL становится каталог журналов по умолчанию для других журналов.

Чтобы изменить эти параметры:

1. Создайте целевой каталог для новых файлов журнала ошибок. В следующем примере создается новый **/tmp/журналы** каталог:

   ```bash
   sudo mkdir /tmp/logs
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/logs
   sudo chgrp mssql /tmp/logs
   ```

1. Используйте mssql-conf, чтобы изменить имя файла журнала ошибок по умолчанию с **задать** команды:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.errorlogfile /tmp/logs/errorlog
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```


## <a id="backupdir"></a> Изменить расположение каталога резервного копирования по умолчанию

**Filelocation.defaultbackupdir** изменения параметров по умолчанию, где создаются файлы резервной копии. По умолчанию эти файлы создаются в /var/opt/mssql/data.

Чтобы настроить это расположение, используйте следующие команды:

1. Создайте целевой каталог для новых файлов резервной копии. В следующем примере создается новый **/tmp/backup** каталог:

   ```bash
   sudo mkdir /tmp/backup
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/backup
   sudo chgrp mssql /tmp/backup
   ```

1. Измените каталог резервного копирования по умолчанию с помощью команды «set» с помощью mssql-conf.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultbackupdir /tmp/backup
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="coredump"></a> Укажите параметры дампа памяти

При возникновении исключения в один из процессов SQL Server, SQL Server создает дамп памяти.

Существует два варианта для управления типом памяти дампов, что SQL Server собирает: **coredump.coredumptype** и **coredump.captureminiandfull**. Они относятся к два этапа захвата дампа памяти. 

Первый этап захвата управляется **coredump.coredumptype** параметр, определяющий тип файла дампа, созданные во время исключения. Второй этап включается, когда **coredump.captureminiandfull** параметр. Если **coredump.captureminiandfull** имеет значение true, дамп файл, указанный параметром **coredump.coredumptype** создается и также создается второй мини-дампа. Установка **coredump.captureminiandfull** false отключает попытки второй записи.

1. Решить, следует ли записывать полный и мини-дампов с помощью **coredump.captureminiandfull** параметр.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    Значение по умолчанию — **false**

1. Укажите тип файла дампа с **coredump.coredumptype** параметр.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    Значение по умолчанию — **miniplus**

    В следующей таблице перечислены возможные **coredump.coredumptype** значения.

    | Type | Описание |
    |-----|-----|
    | **Mini** | Mini — это наименьший тип файла дампа. Сведения о системе Linux используется для определения потоков и модулей в процессе. Дамп содержит только стеки потоков среды узла и модули. Он не содержит ссылки на память, косвенные или глобальных переменных. |
    | **miniplus** | MiniPlus аналогичен mini, но он включает в себя дополнительную память. Понимание внутренних механизмов SQLPAL и хост-среды, добавление следующих областей памяти дампа:</br></br> -Различные globals</br> -Всю память выше 64 ТБ</br> — Все с именем регионов **/proc/$ pid и сопоставлений**</br> -Косвенных памяти из потоков и стеки</br> -Сведения о потоке</br> -Связанные Teb элемента и его Peb</br> -Данные модуля</br> -VMM и VAD дерева |
    | **Фильтрация** | Структура отфильтрованных использует, основанная на вычитание, где всю память в процессе будет включен, если только специально не исключаются. Проектирование понимает внутренних SQLPAL и средой размещения, за исключением определенных регионах из дампа.
    | **Полный** | Полный дамп полного процесса, включающий все области находится в **/proc/$ pid и сопоставлений**. Это поведение не управляется **coredump.captureminiandfull** параметр. |

## <a id="dbmail"></a> Настроить почтовый профиль по умолчанию базы данных для SQL Server в Linux

**Sqlpagent.databasemailprofile** позволяет задать профиль по умолчанию компонента DB Mail для уведомлений по электронной почте.

```bash
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile <profile_name>
```
## <a id="hadr"></a> Высокий уровень доступности

**Hadr.hadrenabled** позволяет группы доступности в экземпляре SQL Server. Следующая команда включает группы доступности, задав **hadr.hadrenabled** 1. Необходимо перезапустить SQL Server для параметра вступили в силу.

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

Сведения о том, как они используются для групп доступности см. в разделе двух следующих разделах.

- [Настройка AlwaysOn группы доступности для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md)
- [Настройка группы доступности для чтения и масштабирования для SQL Server в Linux](sql-server-linux-availability-group-configure-rs.md)


## <a id="localaudit"></a> Каталог локального аудита набора

**Telemetry.userrequestedlocalauditdirectory** параметр позволяет включить локальный аудит и создаются позволяет задать каталог, где в локальном журнале аудита.

1. Создайте целевой каталог для новых журналов локального аудита. В следующем примере создается новый **/tmp/аудита** каталог:

   ```bash
   sudo mkdir /tmp/audit
   ```

1. Изменить владельца и группу каталога **mssql** пользователя:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Запустите сценарий mssql-conf в качестве привилегированного пользователя с **задать** команду для **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

Дополнительные сведения см. в разделе [отзывы по SQL Server в Linux](sql-server-linux-customer-feedback.md).

## <a id="lcid"></a> Изменение языка SQL Server

**Language.lcid** изменения параметров языкового стандарта сервера SQL любого идентификатора поддерживаемого языка (LCID). 

1. Следующий пример изменяет языковой стандарт на французский (1036):

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. Перезапустите службу SQL Server, чтобы применить изменения:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a> Задать ограничение памяти

**Memory.memorylimitmb** параметр объем доступной физической памяти (в МБ) для SQL Server. Значение по умолчанию составляет 80% физической памяти.

1. Запустите сценарий mssql-conf в качестве привилегированного пользователя с **задать** команду для **memory.memorylimitmb**. В следующем примере изменяется доступной памяти для SQL Server для 3,25 ГБ (3328 МБ).

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. Перезапустите службу SQL Server, чтобы применить изменения:

   ```bash
   sudo systemctl restart mssql-server
   ```

::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="msdtc"></a> Настройте службу MSDTC

**Network.rpcport** и **distributedtransaction.servertcpport** параметры используются для настройки координатора распределенных транзакций Microsoft (MSDTC). Чтобы изменить эти параметры, выполните следующие команды:

1. Запустите сценарий mssql-conf в качестве привилегированного пользователя с **задать** команду «network.rpcport»:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport <rcp_port>
   ```

2. Затем установите для параметра «distributedtransaction.servertcpport»:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport <servertcpport_port>
   ```

В дополнение к настройке этих значений, необходимо также настроить маршрутизацию и обновить брандмауэр для порта 135. Дополнительные сведения о том, как это сделать, см. в разделе [настройка MSDTC на Linux](sql-server-linux-configure-msdtc.md).

Существует несколько других параметров для mssql-conf, который можно использовать для наблюдения и диагностики MSDTC. В следующей таблице кратко описаны эти параметры. Дополнительные сведения по их использованию см. сведения в статье службы поддержки Windows, [как включить диагностическую трассировку для MS DTC](https://support.microsoft.com/help/926099/how-to-enable-diagnostic-tracing-for-ms-dtc-on-a-windows-based-compute).

| параметр MSSQL-conf | Описание |
|---|---|
| distributedtransaction.allowonlysecurerpccalls | Настройка безопасного вызовы RPC только для распределенных транзакций |
| distributedtransaction.fallbacktounsecurerpcifnecessary | Настройка безопасности только вызовы RPC для распределенных |транзакции
| distributedtransaction.maxlogsize | DTC размером файла журнала транзакций в МБ. Значение по умолчанию — 64 МБ |
| distributedtransaction.memorybuffersize | Размер циклического буфера, в которой хранятся трассировок. Этот размер является в МБ, и значение по умолчанию — 10 МБ |
| distributedtransaction.servertcpport | MSDTC rpc-порт сервера |
| distributedtransaction.trace_cm | Трассировки в диспетчере соединений |
| distributedtransaction.trace_contact | Отслеживает связи пула и контакты |
| distributedtransaction.trace_gateway | Источник трассировки шлюза |
| distributedtransaction.trace_log | Журнал трассировки |
| distributedtransaction.trace_misc | Трассировки, которые нельзя разделить на другие категории |
| distributedtransaction.trace_proxy | Трассировки, создаваемые в прокси-сервером MSDTC |
| distributedtransaction.trace_svc | Отслеживает службы и .exe файла запуска |
| distributedtransaction.trace_trace | Сама инфраструктура трассировки |
| distributedtransaction.trace_util | Подпрограммы CRC трассировок, которые вызываются из нескольких расположений |
| distributedtransaction.trace_xa | Источник трассировки диспетчера транзакций XATM XA (не) |
| distributedtransaction.tracefilepath | Папка, в трассировке должны сохраняться файлы |
| distributedtransaction.turnoffrpcsecurity | Включение или отключение безопасности RPC для распределенных транзакций |

::: moniker-end
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="mlservices-eula"></a> Примите лицензионные соглашения MLServices

Добавление [машинного обучения пакетов R или Python](sql-server-linux-setup-machine-learning.md) к базе данных ядра необходимо принять условия лицензионного соглашения для дистрибутивов с открытым исходным кодом R и Python. В следующей таблице перечислены все доступные команды или параметры, связанные с mlservices лицензионные соглашения. Один и тот же параметр лицензионное соглашение используется для R и Python, в зависимости от того, что вы установили.

```bash
# For all packages: database engine and mlservices
# Setup prompts for mlservices EULAs, which you need to accept
sudo /opt/mssql/bin/mssql-conf setup

# Add R or Python to an existing installation
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml

# Alternative valid syntax
# Adds the EULA section to the INI and sets acceptulam to yes
sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y

# Rescind EULA acceptance and removes the setting
sudo /opt/mssql/bin/mssql-conf unset EULA accepteulaml
```

Принятие лицензионного соглашения можно также добавить непосредственно в [mssql.conf файл](#mssql-conf-format):

```ini
[EULA]
accepteula = Y
accepteulaml = Y
```
:::moniker-end
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="mlservices-outbound-access"></a> Разрешить исходящий сетевой доступ

Исходящий сетевой доступ для расширений R, Python и Java в [службы машинного обучения SQL Server](sql-server-linux-setup-machine-learning.md) функция отключена по умолчанию. Чтобы включить исходящие запросы, задайте «outboundnetworkaccess» логическое свойство, с помощью mssql-conf.

После задания значения свойства, перезапустите службу панели запуска SQL Server для чтения обновленные значения из INI-файл. Сообщение перезапуска, напоминающее каждый раз, когда изменяется параметр относящиеся к расширяемости.

```bash
# Adds the extensibility section and property.
# Sets "outboundnetworkaccess" to true.
# This setting is required if you want to access data or operations off the server.
sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1

# Turns off network access but preserves the setting
/opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 0

# Removes the setting and rescinds network access
sudo /opt/mssql/bin/mssql-conf unset extensibility.outboundnetworkaccess
```

Можно также добавить «outboundnetworkaccess» непосредственно к [mssql.conf файл](#mssql-conf-format):

```ini
[extensibility]
outboundnetworkaccess = 1
```
:::moniker-end

## <a id="tcpport"></a> Изменение TCP-порт

**Network.tcpport** изменения параметров TCP-порт, где SQL Server прослушивает соединения. По умолчанию этот порт будет присвоено 1433. Чтобы изменить порт, выполните следующие команды:

1. Запустите сценарий mssql-conf в качестве привилегированного пользователя с помощью команды «set» для «network.tcpport»:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
   ```

2. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

3. При подключении к SQL Server, необходимо указать пользовательский порт запятой (,) после имени узла или IP-адрес. Например чтобы подключиться с помощью SQLCMD, вы выполните команду ниже:

   ```bash
   sqlcmd -S localhost,<new_tcp_port> -U test -P test
   ```

## <a id="tls"></a> Укажите параметры TLS

Следующие параметры настройки TLS для экземпляра SQL Server на Linux.

|Параметр |Описание |
|--- |--- |
|**Network.ForceEncryption** |Если значение равно 1, затем [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] заставляет все подключения должны быть зашифрованы. По умолчанию этот параметр является 0. |
|**Network.tlscert** |Абсолютный путь к сертификату файла, который [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует для TLS. Пример   `/etc/ssl/certs/mssql.pem`  Файл сертификата должны быть доступны с помощью учетной записи mssql. Корпорация Майкрософт рекомендует ограничения доступа к файлу с помощью `chown mssql:mssql <file>; chmod 400 <file>`. |
|**Network.tlskey** |Абсолютный путь к закрытому ключу файла, который [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует для TLS. Пример  `/etc/ssl/private/mssql.key`  Файл сертификата должны быть доступны с помощью учетной записи mssql. Корпорация Майкрософт рекомендует ограничения доступа к файлу с помощью `chown mssql:mssql <file>; chmod 400 <file>`. |
|**Network.tlsprotocols** |Разделенный запятыми список, из какой TLS протоколы разрешено использовать с SQL Server. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] всегда пытается согласовать надежный протокол разрешенных. Если клиент не поддерживает любой допустимый протокол [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] отклоняет попытки подключения.  Для обеспечения совместимости всех поддерживаемых протоколов разрешены по умолчанию (1.2, 1.1, 1.0).  Если ваши клиенты поддерживают TLS 1.2, корпорация Майкрософт рекомендует, позволяя только TLS 1.2. |
|**Network.tlsciphers** |Указывает, какие шифры допускаемых [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для TLS. Эта строка должны быть отформатированы в [формате списка шифров OpenSSL](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). Как правило нет необходимости для изменения этого параметра. <br /> По умолчанию допускаются следующие шифров: <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **Network.kerberoskeytabfile** |Путь к файлу keytab Kerberos |

Пример использования параметров TLS, см. в разделе [шифрование соединений с SQL Server в Linux](sql-server-linux-encrypted-connections.md).

## <a id="traceflags"></a> Включение или отключение флагов трассировки

Это **traceflag** включает или отключает флаги трассировки для запуска службы SQL Server. Чтобы включить или отключить флаг трассировки используйте следующие команды:

1. Включите флаг трассировки, используя следующую команду. Например, 1234 флаг трассировки:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 on
   ```

1. Вы можете включить несколько флагов трассировки, указав их отдельно:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 2345 3456 on
   ```

1. Аналогичным образом, можно отключить один или несколько флагов трассировки включен, указав их и добавив **off** параметр:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 2345 3456 off
   ```

1. Перезапустите службу SQL Server, чтобы применить изменения:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="remove-a-setting"></a>Удалите параметр

Чтобы отменить все задание осуществляется с `mssql-conf set`, вызовите **mssql-conf** с `unset` и имя параметра. Это Очищает параметр, эффективно возвращением к значению по умолчанию.

1. В следующем примере удаляется **network.tcpport** параметр.

   ```bash
   sudo /opt/mssql/bin/mssql-conf unset network.tcpport
   ```

1. Перезапустите службу SQL Server.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="view-current-settings"></a>Просмотр текущих параметров

Для просмотра любого настроек, выполните следующую команду, чтобы вывести содержимое **mssql.conf** файла:

```bash
sudo cat /var/opt/mssql/mssql.conf
```

Обратите внимание на то, что все параметры, не отображаются в этот файл при использовании значения по умолчанию. В следующем разделе приводится пример **mssql.conf** файла.


## <a id="mssql-conf-format"></a> Формат MSSQL.conf

Следующие **/var/opt/mssql/mssql.conf** файл содержит пример для каждого параметра. Этот формат можно использовать вручную внести изменения в **mssql.conf** файл при необходимости. Если вы вручную измените файл, необходимо перезапустить SQL Server перед применением изменений. Чтобы использовать **mssql.conf** файла с помощью Docker, необходимо иметь Docker [сохранить данные](sql-server-linux-configure-docker.md). Сначала добавьте полное **mssql.conf** файла в каталоге узла, а затем запустите контейнер. Пример этого [отзывы клиентов](sql-server-linux-customer-feedback.md).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

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

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```ini
[EULA]
accepteula = Y
accepteulaml = Y

[coredump]
captureminiandfull = true
coredumptype = full

[distributedtransaction]
servertcpport = 51999

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
rpcport = 13500
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

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Вместо этого использовать переменные среды, чтобы сделать некоторые из этих изменений конфигурации, см. в разделе [SQL Server можно настроить параметры с переменными среды](sql-server-linux-configure-environment-variables.md).

Другие средства управления и сценарии, см. в разделе [управления SQL Server в Linux](sql-server-linux-management-overview.md).
