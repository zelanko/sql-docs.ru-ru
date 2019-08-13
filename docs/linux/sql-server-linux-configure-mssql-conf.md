---
title: Настройка параметров SQL Server на Linux
description: В этой статье описывается настройка параметров SQL Server на Linux с помощью средства mssql-conf.
author: VanMSFT
ms.author: vanto
ms.date: 07/30/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.openlocfilehash: aaddcbfb9520f2619df82ddbf3695604c2cbee40
ms.sourcegitcommit: 97e94b76f9f48d161798afcf89a8c2ac0f09c584
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661375"
---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Настройка SQL Server на Linux с помощью средства mssql-conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

**mssql-conf** — это скрипт настройки, который устанавливается вместе с SQL Server 2017 для Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu. С помощью этой служебной программы можно настраивать перечисленные ниже параметры.

|||
|---|---|
| [Агент](#agent) | Включение агента SQL Server. |
| [Параметры сортировки](#collation) | Задание новых параметров сортировки для SQL Server на Linux. |
| [Отзывы пользователей](#customerfeedback) | Включение или отключение отправки отзывов в корпорацию Майкрософт из SQL Server. |
| [Профиль компонента Database Mail](#dbmail) | Настройка профиля Database Mail по умолчанию для SQL Server на Linux. |
| [Каталог данных по умолчанию](#datadir) | Изменение каталога по умолчанию для новых файлов данных (MDF) SQL Server. |
| [Каталог журналов по умолчанию](#datadir) | Изменение каталога по умолчанию для новых файлов журналов (LDF) базы данных SQL Server. |
| [Каталог базы данных master по умолчанию](#masterdatabasedir) | Изменение каталога по умолчанию для файлов журналов и базы данных master.|
| [Имя файла базы данных master по умолчанию](#masterdatabasename) | Изменяет имя для файлов базы данных master. |
| [Каталог дампа по умолчанию](#dumpdir) | Изменение каталога по умолчанию для новых дампов памяти и других файлов, предназначенных для устранения неполадок. |
| [Каталог журналов ошибок по умолчанию](#errorlogdir) | Изменение каталога по умолчанию для новых файлов журнала ошибок SQL Server, трассировки профилировщика по умолчанию, сеанса XE работоспособности системы и сеанса XE Hekaton. |
| [Каталог резервного копирования по умолчанию](#backupdir) | Изменение каталога по умолчанию для новых файлов резервных копий. |
| [Тип дампа](#coredump) | Выбор типа файла с дампом памяти для сбора. |
| [Высокий уровень доступности](#hadr) | Включение групп доступности. |
| [Каталог локального аудита](#localaudit) | Указание каталога для добавления файлов локального аудита. |
| [Локаль](#lcid) | Указание языкового стандарта для SQL Server. |
| [Предельный объем памяти](#memorylimit) | Указание предельного объема памяти для SQL Server. |
| [TCP-порт](#tcpport) | Изменение порта, через который SQL Server ожидает передачи данных. |
| [TLS](#tls) | Настройка протокола TLS. |
| [Флаги трассировки](#traceflags) | Установка флагов трассировки, которые будет использовать служба. |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

**mssql-conf** — это скрипт настройки, который устанавливается вместе с [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] для Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu. С помощью этой служебной программы можно настраивать перечисленные ниже параметры.

|||
|---|---|
| [Агент](#agent) | Включение агента SQL Server. |
| [Параметры сортировки](#collation) | Задание новых параметров сортировки для SQL Server на Linux. |
| [Отзывы пользователей](#customerfeedback) | Включение или отключение отправки отзывов в корпорацию Майкрософт из SQL Server. |
| [Профиль компонента Database Mail](#dbmail) | Настройка профиля Database Mail по умолчанию для SQL Server на Linux. |
| [Каталог данных по умолчанию](#datadir) | Изменение каталога по умолчанию для новых файлов данных (MDF) SQL Server. |
| [Каталог журналов по умолчанию](#datadir) | Изменение каталога по умолчанию для новых файлов журналов (LDF) базы данных SQL Server. |
| [Каталог файлов базы данных master по умолчанию](#masterdatabasedir) | Изменение каталога по умолчанию для файлов базы данных master в существующей установке SQL.|
| [Имя файла базы данных master по умолчанию](#masterdatabasename) | Изменяет имя для файлов базы данных master. |
| [Каталог дампа по умолчанию](#dumpdir) | Изменение каталога по умолчанию для новых дампов памяти и других файлов, предназначенных для устранения неполадок. |
| [Каталог журналов ошибок по умолчанию](#errorlogdir) | Изменение каталога по умолчанию для новых файлов журнала ошибок SQL Server, трассировки профилировщика по умолчанию, сеанса XE работоспособности системы и сеанса XE Hekaton. |
| [Каталог резервного копирования по умолчанию](#backupdir) | Изменение каталога по умолчанию для новых файлов резервных копий. |
| [Тип дампа](#coredump) | Выбор типа файла с дампом памяти для сбора. |
| [Высокий уровень доступности](#hadr) | Включение групп доступности. |
| [Каталог локального аудита](#localaudit) | Указание каталога для добавления файлов локального аудита. |
| [Локаль](#lcid) | Указание языкового стандарта для SQL Server. |
| [Предельный объем памяти](#memorylimit) | Указание предельного объема памяти для SQL Server. |
| [Координатор распределенных транзакций Майкрософт](#msdtc) | Настройка координатора распределенных транзакций Майкрософт на платформе Linux. |
| [Лицензионные соглашения MLServices](#mlservices-eula) | Принятие лицензионных соглашений R и Python для пакетов mlservices. Применимо только к SQL Server 2019.|
| [outboundnetworkaccess](#mlservices-outbound-access) |Включение исходящего сетевого доступа для расширений R, Python и Java служб [mlservices](sql-server-linux-setup-machine-learning.md).|
| [TCP-порт](#tcpport) | Изменение порта, через который SQL Server ожидает передачи данных. |
| [TLS](#tls) | Настройка протокола TLS. |
| [Флаги трассировки](#traceflags) | Установка флагов трассировки, которые будет использовать служба. |

::: moniker-end

> [!TIP]
> Некоторые их этих параметров можно также настроить с помощью переменных среды. Дополнительные сведения см. в статье [Настройка параметров SQL Server с помощью переменных среды в Linux](sql-server-linux-configure-environment-variables.md).

## <a name="usage-tips"></a>Советы по использованию

* В случае с группами доступности Always On и кластерами общих дисков во всех узлах необходимо вносить одинаковые изменения в конфигурацию.

* В случае с кластером общих дисков не пытайтесь перезапустить службу **mssql-server**, чтобы применить изменения. SQL Server работает как приложение. Вместо этого переведите ресурс в режим "вне сети", а затем снова в режим "в сети".

* В этих примерах средство mssql-conf запускается с указанием полного пути: **/opt/mssql/bin/mssql-conf**. Если вы уже перешли по этому пути, запускайте mssql-conf в контексте текущего каталога: **./mssql-conf**.

## <a id="agent"></a> Включение агента SQL Server

Параметр **sqlagent.enabled** включает [агент SQL Server](sql-server-linux-run-sql-server-agent-job.md). По умолчанию агент SQL Server отключен. Если параметр **sqlagent.enabled** отсутствует в файле параметров mssql.conf, предполагается, что агент SQL Server отключен.

Чтобы изменить этот параметр, выполните указанные ниже действия.

1. Включите агент SQL Server:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
   ```

2. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="collation"></a> Изменение параметров сортировки SQL Server

Параметр **set-collation** позволяет выбрать любые из поддерживаемых параметров сортировки.

1. Сначала [выполните резервное копирование всех пользовательских баз данных](sql-server-linux-backup-and-restore-database.md) на сервере.

1. Затем используйте хранимую процедуру [sp_detach_db](../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) для отключения пользовательских баз данных.

1. Запустите программу с параметром **set-collation** и следуйте указаниям:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. Программа mssql-conf попытается изменить параметры сортировки на указанные и перезапустить службу. Если возникнут ошибки, будет произведен откат к прежним параметрам сортировки.

1. Восстановите пользовательские базы данных из резервных копий.

Чтобы получить список поддерживаемых параметров сортировки, выполните функцию [sys.fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md): `SELECT Name from sys.fn_helpcollations()`.

## <a id="customerfeedback"></a> Настройка отзывов пользователей

Параметр **telemetry.customerfeedback** определяет, отправляются ли отзывы из SQL Server в корпорацию Майкрософт. По умолчанию он имеет значение **true** для всех выпусков. Чтобы изменить значение, выполните следующие команды:

> [!IMPORTANT]
> Отключить отправку отзывов для бесплатных выпусков SQL Server, Express и Developer невозможно.

1. Запустите скрипт mssql-conf от имени привилегированного пользователя с помощью команды **set** для **telemetry.customerfeedback**. В приведенном ниже примере отправка отзывов отключается путем указания значения **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

Дополнительные сведения см. в статье [Отзывы пользователей об SQL Server на Linux](sql-server-linux-customer-feedback.md) и в [Заявлении о конфиденциальности SQL Server](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a id="datadir"></a> Изменение каталога по умолчанию для данных или журналов

Параметры **filelocation.defaultdatadir** и **filelocation.defaultlogdir** позволяют изменить расположение, в котором создаются файлы баз данных и журналов. Расположение по умолчанию — /var/opt/mssql/data. Чтобы изменить эти параметры, выполните указанные ниже действия.

1. Создайте целевой каталог для новых файлов данных и журналов базы данных. В следующем примере создается каталог **/tmp/data**:

   ```bash
   sudo mkdir /tmp/data
   ```

1. Задайте пользователя **mssql** в качестве владельца и группы каталога:

   ```bash
   sudo chown mssql /tmp/data
   sudo chgrp mssql /tmp/data
   ```

1. Используйте программу mssql-conf для изменения каталога данных по умолчанию с помощью команды **set**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdatadir /tmp/data
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Теперь все файлы баз данных для создаваемых баз данных будут сохраняться в этом новом расположении. Чтобы изменить расположение файлов журналов (LDF) для новых баз данных, можно выполнить следующую команду set:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultlogdir /tmp/log
   ```

1. Эта команда также предполагает, что существует каталог /tmp/log и что он принадлежит пользователю и группе **mssql**.


## <a id="masterdatabasedir"></a> Изменение каталога по умолчанию для файлов базы данных master

Параметры **filelocation.masterdatafile** и **filelocation.masterlogfile** позволяют изменить расположение, в котором ядро СУБД SQL Server ищет файлы базы данных master. Расположение по умолчанию — /var/opt/mssql/data.

Чтобы изменить эти параметры, выполните указанные ниже действия.

1. Создайте целевой каталог для новых файлов с журналами ошибок. В следующем примере создается каталог **/tmp/masterdatabasedir**:

   ```bash
   sudo mkdir /tmp/masterdatabasedir
   ```

1. Задайте пользователя **mssql** в качестве владельца и группы каталога:

   ```bash
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
   ```

1. Используйте программу mssql-conf, чтобы изменить каталог для файлов основных данных и журналов базы данных master с помощью команды **set**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
   ```

   > [!NOTE]
   > Помимо перемещения файлов основных данных и журналов, при этом также изменяется расположение для всех остальных системных баз данных.

1. Остановите службу SQL Server:

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Переместите файлы master.mdf и masterlog.ldf:

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf 
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
   ```

1. Запустите службу SQL Server:

   ```bash
   sudo systemctl start mssql-server
   ```

   > [!NOTE]
   > Если серверу SQL Server не удается найти файлы master.mdf и mastlog.ldf в указанном каталоге, в нем автоматически создается шаблонная копия системных баз данных и SQL Server успешно запускается. Однако метаданные, такие как пользовательские базы данных, имена входа на сервер, сертификаты сервера, ключи шифрования, задания агента SQL или старый пароль для имени входа SA, не обновляются в новой базе данных master. Чтобы продолжить использовать существующие метаданные, потребуется остановить SQL Server, переместить старые файлы master.mdf и mastlog.ldf в новое расположение, а затем снова запустить SQL Server.
 
## <a id="masterdatabasename"></a> Изменение имени для файлов базы данных master

Параметры **filelocation.masterdatafile** и **filelocation.masterlogfile** позволяют изменить расположение, в котором ядро СУБД SQL Server ищет файлы базы данных master. С их помощью можно также изменить имена файлов базы данных master и ее журналов. 

Чтобы изменить эти параметры, выполните указанные ниже действия.

1. Остановите службу SQL Server:

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Используйте программу mssql-conf, чтобы изменить требуемые имена файлов основных данных и журналов для базы данных master с помощью команды **set**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /var/opt/mssql/data/masternew.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.mastlogfile /var/opt/mssql/data/mastlognew.ldf
   ```

   > [!IMPORTANT]
   > Имена файлов базы данных master и ее журналов можно изменить только после успешного запуска SQL Server. При первом запуске SQL Server эти файлы должны называться master.mdf и mastlog.ldf.

1. Изменение имен файлов данных и журналов для базы данных master 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /var/opt/mssql/data/masternew.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /var/opt/mssql/data/mastlognew.ldf
   ```

1. Запустите службу SQL Server:

   ```bash
   sudo systemctl start mssql-server
   ```

## <a id="dumpdir"></a> Изменение каталога дампа по умолчанию

Параметр **filelocation.defaultdumpdir** позволяет изменить расположение по умолчанию, в котором создаются дампы памяти и SQL в случае аварийного завершения работы. По умолчанию эти файлы создаются в каталоге /var/opt/mssql/log.

Чтобы задать новое расположение, используйте приведенные ниже команды.

1. Создайте целевой каталог для новых файлов дампа. В следующем примере создается каталог **/tmp/dump**:

   ```bash
   sudo mkdir /tmp/dump
   ```

1. Задайте пользователя **mssql** в качестве владельца и группы каталога:

   ```bash
   sudo chown mssql /tmp/dump
   sudo chgrp mssql /tmp/dump
   ```

1. Используйте программу mssql-conf для изменения каталога данных по умолчанию с помощью команды **set**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdumpdir /tmp/dump
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="errorlogdir"></a> Изменение каталога по умолчанию для файла журнала ошибок

Параметр **filelocation.errorlogfile** позволяет изменить расположение, в котором создаются файлы журнала ошибок, трассировки профилировщика по умолчанию, сеанса XE работоспособности системы и сеанса XE Hekaton. Расположение по умолчанию — /var/opt/mssql/log. Каталог, в котором создается файл журнала ошибок SQL, становится каталогом по умолчанию и для остальных журналов.

Чтобы изменить этот параметр, выполните указанные ниже действия.

1. Создайте целевой каталог для новых файлов с журналами ошибок. В следующем примере создается каталог **/tmp/logs**:

   ```bash
   sudo mkdir /tmp/logs
   ```

1. Задайте пользователя **mssql** в качестве владельца и группы каталога:

   ```bash
   sudo chown mssql /tmp/logs
   sudo chgrp mssql /tmp/logs
   ```

1. Используйте программу mssql-conf, чтобы изменить имя файла журнала ошибок по умолчанию с помощью команды **set**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.errorlogfile /tmp/logs/errorlog
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```


## <a id="backupdir"></a> Изменение каталога резервного копирования по умолчанию

Параметр **filelocation.defaultdumpdir** позволяет изменить расположение по умолчанию, в котором создаются файлы резервных копий. По умолчанию эти файлы создаются в каталоге /var/opt/mssql/data.

Чтобы задать новое расположение, используйте приведенные ниже команды.

1. Создайте целевой каталог для новых файлов резервных копий. В следующем примере создается каталог **/tmp/backup**:

   ```bash
   sudo mkdir /tmp/backup
   ```

1. Задайте пользователя **mssql** в качестве владельца и группы каталога:

   ```bash
   sudo chown mssql /tmp/backup
   sudo chgrp mssql /tmp/backup
   ```

1. Используйте программу mssql-conf для изменения каталога резервного копирования по умолчанию с помощью команды set:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultbackupdir /tmp/backup
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="coredump"></a> Указание параметров дампа ядра

Если в одном из процессов SQL Server возникает исключение, SQL Server создает дамп памяти.

Есть два параметра для управления типом дампов памяти, собираемых сервером SQL Server: **coredump.coredumptype** и **coredump.captureminiandfull**. Каждый из них связан с одним из двух этапов записи дампа ядра. 

Первый этап записи управляется параметром **coredump.coredumptype**, который определяет тип файла дампа, создаваемого в случае исключения. Второй этап активируется параметром **coredump.captureminiandfull**. Если параметр **coredump.captureminiandfull** имеет значение true, создается файл дампа, определяемый параметром **coredump.coredumptype**, а также еще один файл — файл мини-дампа. Если присвоить параметру **coredump.captureminiandfull** значение false, второй этап регистрации выполняться не будет.

1. Укажите, следует ли записывать как полный дамп, так и мини-дамп, с помощью параметра **coredump.captureminiandfull**.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    Значение по умолчанию: **false**

1. Укажите тип файла дампа с помощью параметра **coredump.coredumptype**.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    Значение по умолчанию: **miniplus**

    В таблице ниже перечислены возможные значения параметра **coredump.coredumptype**.

    | Тип | Описание |
    |-----|-----|
    | **mini** | Mini — это тип файла дампа наименьшего размера. Он предполагает использование системных сведений Linux для определения потоков и модулей процесса. Дамп содержит только стеки и модули среды размещения. Косвенные ссылки на память и глобальные переменные в него не включаются. |
    | **miniplus** | Тип MiniPlus похож на mini, но в него включаются дополнительные области памяти. Он поддерживает внутренние процессы SQLPAL и среды размещения, благодаря чему в дамп добавляются следующие области памяти:</br></br> — различные глобальные переменные;</br> — вся память выше 64 ТБ;</br> — все именованные области, имеющиеся в **/proc/$pid/maps**;</br> — косвенная память из потоков и стеков;</br> — сведения о потоках;</br> — связанные структуры Teb и Peb;</br> — сведения о модулях;</br> — VMM и дерево VAD. |
    | **filtered** | Тип filtered основан на механизме исключения: в дамп включается вся память процесса, кроме явно исключенной. Он поддерживает внутренние процессы SQLPAL и среды размещения, причем из дампа исключаются определенные области.
    | **full** | Full — это полный дамп процесса, который содержит все области, имеющиеся в **/proc/$pid/maps**. Параметр **coredump.captureminiandfull** в этом случае не действует. |

## <a id="dbmail"></a> Настройка профиля Database Mail по умолчанию для SQL Server на Linux

Параметр **sqlpagent.databasemailprofile** позволяет задать профиль DB Mail по умолчанию для оповещений по электронной почте.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.databasemailprofile <profile_name>
```
## <a id="hadr"></a> Высокий уровень доступности

Параметр **hadr.hadrenabled** включает группы доступности в экземпляре SQL Server. Приведенная ниже команда включает группы доступности путем присвоения параметру **hadr.hadrenabled** значения 1. Чтобы этот параметр вступил в силу, необходимо перезапустить SQL Server.

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

Сведения об использовании этого параметра с группами доступности см. в следующих двух статьях:

- [Настройка группы доступности Always On для SQL Server на Linux](sql-server-linux-availability-group-configure-ha.md)
- [Настройка группы доступности для чтения и масштабирования в SQL Server на Linux](sql-server-linux-availability-group-configure-rs.md)


## <a id="localaudit"></a> Задание каталога локального аудита

Параметр **telemetry.userrequestedlocalauditdirectory** позволяет включить локальный аудит и указать каталог, в котором создаются журналы локального аудита.

1. Создайте целевой каталог для новых журналов локального аудита. В следующем примере создается каталог **/tmp/audit**:

   ```bash
   sudo mkdir /tmp/audit
   ```

1. Задайте пользователя **mssql** в качестве владельца и группы каталога:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Запустите скрипт mssql-conf от имени привилегированного пользователя с командой **set** для **telemetry.userrequestedlocalauditdirectory**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

Дополнительные сведения см. в статье [Отзывы пользователей об SQL Server на Linux](sql-server-linux-customer-feedback.md).

## <a id="lcid"></a> Изменение языкового стандарта SQL Server

Параметр **language.lcid** позволяет изменить языковой стандарт SQL Server, выбрав любой поддерживаемый код языка. 

1. В следующем примере языковой стандарт изменяется на французский (1036):

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. Перезапустите службу SQL Server, чтобы применить изменения:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a> Задание предела памяти

Параметр **memory.memorylimitmb** позволяет определять объем физической памяти (в МБ), доступный серверу SQL Server. Значение по умолчанию — 80 % физической памяти.

1. Запустите скрипт mssql-conf от имени привилегированного пользователя с командой **set** для **memory.memorylimitmb**. В приведенном ниже примере объем памяти, доступный серверу SQL Server, изменяется на 3,25 ГБ (3328 МБ).

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. Перезапустите службу SQL Server, чтобы применить изменения:

   ```bash
   sudo systemctl restart mssql-server
   ```

::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="msdtc"></a> Настройка координатора распределенных транзакций Майкрософт

Параметры **network.rpcport** и **distributedtransaction.servertcpport** позволяют настраивать координатор распределенных транзакций Майкрософт. Чтобы изменить эти параметры, выполните приведенные ниже команды.

1. Запустите скрипт mssql-conf от имени привилегированного пользователя с командой **set** для network.rpcport.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport <rcp_port>
   ```

2. Затем задайте параметр distributedtransaction.servertcpport:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport <servertcpport_port>
   ```

Помимо задания этих значений, необходимо также настроить маршрутизацию и обновить настройки брандмауэра для порта 135. Дополнительные сведения о том, как это сделать, см. в статье [Настройка MSDTC на платформе Linux](sql-server-linux-configure-msdtc.md).

Есть еще ряд параметров mssql-conf, с помощью которых можно отслеживать работу координатора распределенных транзакций Майкрософт и устранять его неполадки. Они вкратце описываются в приведенной ниже таблице. Дополнительные сведения об их использовании см. в статье службы поддержки Windows [Включение диагностической трассировки для координатора распределенных транзакций Майкрософт](https://support.microsoft.com/help/926099/how-to-enable-diagnostic-tracing-for-ms-dtc-on-a-windows-based-compute).

| Параметр mssql-conf | Описание |
|---|---|
| distributedtransaction.allowonlysecurerpccalls | Настройка только безопасных удаленных вызовов процедур (RPC) для распределенных транзакций |
| distributedtransaction.fallbacktounsecurerpcifnecessary | Настройка только безопасных удаленных вызовов процедур (RPC) для распределенных |транзакции
| distributedtransaction.maxlogsize | Размер файла журнала транзакций для координатора распределенных транзакций в МБ. Значение по умолчанию — 64 МБ. |
| distributedtransaction.memorybuffersize | Размер циклического буфера, в котором хранятся трассировки. Размер указывается в МБ. Значение по умолчанию — 10 МБ. |
| distributedtransaction.servertcpport | Порт RPC-сервера координатора распределенных транзакций Майкрософт |
| distributedtransaction.trace_cm | Трассировки в диспетчере подключений |
| distributedtransaction.trace_contact | Трассировка пула контактов и контактов |
| distributedtransaction.trace_gateway | Трассировка службы шлюза |
| distributedtransaction.trace_log | Трассировка журнала |
| distributedtransaction.trace_misc | Трассировки, не относящиеся к другим категориям |
| distributedtransaction.trace_proxy | Трассировки, создаваемые на прокси-сервере координатора распределенных транзакций Майкрософт |
| distributedtransaction.trace_svc | Трассировка запуска служб и файлов EXE |
| distributedtransaction.trace_trace | Инфраструктура трассировки |
| distributedtransaction.trace_util | Трассировка служебных подпрограмм, вызываемых из разных мест |
| distributedtransaction.trace_xa | Источник трассировки диспетчера транзакций XA (XATM) |
| distributedtransaction.tracefilepath | Папка, в которой должны храниться файлы трассировки |
| distributedtransaction.turnoffrpcsecurity | Включение или отключение безопасности RPC для распределенных транзакций |

::: moniker-end
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="mlservices-eula"></a> Принятие лицензионных соглашений MLServices

Для добавления [пакетов машинного обучения R или Python](sql-server-linux-setup-machine-learning.md) в ядро СУБД необходимо принять условия лицензии на дистрибутивы R и Python с открытым кодом. В приведенной ниже таблице перечислены все доступные команды и параметры, связанные с лицензионными соглашениями служб машинного обучения. Для R и Python используются одни и те же параметры.

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

Принятие лицензионных соглашений можно также настроить непосредственно в [файле mssql.conf](#mssql-conf-format).

```ini
[EULA]
accepteula = Y
accepteulaml = Y
```
:::moniker-end
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="mlservices-outbound-access"></a> Включение исходящего сетевого доступа

Исходящий сетевой доступ для расширений R, Python и Java в [Службах машинного обучения SQL Server](sql-server-linux-setup-machine-learning.md) по умолчанию отключен. Чтобы включить исходящие запросы, задайте логическое свойство outboundnetworkaccess с помощью программы mssql-conf.

Задав это свойство, перезапустите службу панели запуска SQL Server, чтобы считать обновленные значения из файла INI. При изменении любого свойства, связанного с расширяемостью, появляется сообщение с напоминанием о необходимости перезапуска.

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

Свойство outboundnetworkaccess можно также добавить напрямую в [файл mssql.conf](#mssql-conf-format).

```ini
[extensibility]
outboundnetworkaccess = 1
```
:::moniker-end

## <a id="tcpport"></a> Изменение TCP-порта

Параметр **network.tcpport** позволяет изменить TCP-порт, через который SQL Server ожидает передачи данных. По умолчанию используется порт 1433. Чтобы изменить порт, выполните приведенные ниже команды.

1. Запустите скрипт mssql-conf от имени привилегированного пользователя с командой set для network.tcpport.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
   ```

2. Перезапустите службу SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

3. Теперь при подключении к SQL Server нужно указывать пользовательский порт с запятой (,) после имени узла или IP-адреса. Например, для подключения sqlcmd будет использоваться следующая команда:

   ```bash
   sqlcmd -S localhost,<new_tcp_port> -U test -P test
   ```

## <a id="tls"></a> Указание параметров TLS

Ниже приведены параметры, которые служат для настройки протокола TLS для экземпляра SQL Server, работающего на платформе Linux.

|Параметр |Описание |
|--- |--- |
|**network.forceencryption** |Если задано значение 1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] требует, чтобы все подключения были зашифрованными. По умолчанию этот параметр имеет значение 0. |
|**network.tlscert** |Абсолютный путь к файлу сертификата, используемому [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для TLS. Пример   `/etc/ssl/certs/mssql.pem` Файл сертификата должен быть доступен учетной записи mssql. Корпорация Майкрософт рекомендует ограничивать доступ к этому файлу с помощью `chown mssql:mssql <file>; chmod 400 <file>`. |
|**network.tlskey** |Абсолютный путь к файлу закрытого ключа, используемому [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для TLS. Пример  `/etc/ssl/private/mssql.key` Файл сертификата должен быть доступен учетной записи mssql. Корпорация Майкрософт рекомендует ограничивать доступ к этому файлу с помощью `chown mssql:mssql <file>; chmod 400 <file>`. |
|**network.tlsprotocols** |Разделенный запятыми список протоколов TLS, которые SQL Server разрешает использовать. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] всегда пытается использовать самый надежный из допустимых протоколов. Если клиент не поддерживает ни один из допустимых протоколов, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] отклоняет попытку подключения.  В целях совместимости по умолчанию разрешены все поддерживаемые протоколы (1.2, 1.1, 1.0).  Если клиенты поддерживают протокол TLS 1.2, корпорация Майкрософт рекомендует разрешать использовать только эту версию. |
|**network.tlsciphers** |Определяет шифры, разрешенные к использованию для TLS в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Строка должна соответствовать [формату списка шифров OpenSSL](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). Как правило, изменять этот параметр не требуется. <br /> По умолчанию разрешены следующие шифры: <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **network.kerberoskeytabfile** |Путь к KEYTAB-файлу Kerberos |

Пример использования параметров TLS см. в статье [Шифрование подключений к SQL Server на Linux](sql-server-linux-encrypted-connections.md).

## <a id="traceflags"></a> Включение и отключение флагов трассировки

Параметр **traceflag** позволяет включить или отключить флаги трассировки при запуске службы SQL Server. Чтобы включить или отключить флаг трассировки, выполните приведенные ниже команды.

1. Для включения флага трассировки используйте приведенную ниже команду. Например, для флага трассировки 1234:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 on
   ```

1. Вы можете включить несколько флагов трассировки, указав их через пробел:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 2345 3456 on
   ```

1. Точно так же можно отключить один или несколько включенных флагов трассировки, указав их и добавив параметр **off**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 2345 3456 off
   ```

1. Перезапустите службу SQL Server, чтобы применить изменения:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="remove-a-setting"></a>Удаление параметра

Чтобы удалить любой параметр, заданный с помощью `mssql-conf set`, вызовите программу **mssql-conf** с параметром `unset` и именем удаляемого параметра. В результате будет восстановлено значение параметра по умолчанию.

1. В следующем примере удаляется параметр **network.tcpport**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf unset network.tcpport
   ```

1. Перезапустите службу SQL Server.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="view-current-settings"></a>Просмотр текущих параметров

Чтобы просмотреть все настроенные параметры, выполните следующую команду, которая выводит содержимое файла **mssql.conf**:

```bash
sudo cat /var/opt/mssql/mssql.conf
```

Обратите внимание на то, что параметры, отсутствующие в этом файле, имеют значения по умолчанию. В следующем разделе приводится пример файла **mssql.conf**.


## <a id="mssql-conf-format"></a> Формат файла mssql.conf

В приведенном ниже файле **/var/opt/mssql/mssql.conf** представлен пример каждого параметра. Вы можете использовать этот формат, чтобы вносить изменения в файл **mssql.conf** вручную по мере необходимости. Чтобы внесенные вручную изменения вступили в силу, необходимо перезапустить SQL Server. Для использования файла **mssql.conf** с Docker необходимо настроить в Docker [сохранение данных](sql-server-linux-configure-docker.md). Сначала добавьте полный файл **mssql.conf** в каталог узла, а затем запустите контейнер. Пример см. в статье [Отзывы пользователей](sql-server-linux-customer-feedback.md).

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

Сведения о том, как вносить некоторые из описанных изменений в конфигурацию с помощью переменных среды, см. в статье [Настройка параметров SQL Server с помощью переменных среды ](sql-server-linux-configure-environment-variables.md).

Описание других средств управления и сценариев см. в статье, посвященной [управлению SQL Server на Linux](sql-server-linux-management-overview.md).
