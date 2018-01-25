---
title: "Локальный аудит для сбора отзывов об использовании SQL Server | Документы Майкрософт"
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-security
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Local Audit
ms.assetid: a0665916-7789-4f94-9086-879275802cf3
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e7f97c11f27f8eb1773c8535ace8e409290750d
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="local-audit-for-sql-server-usage-feedback-collection"></a>Локальный аудит для сбора отзывов об использовании SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
## <a name="introduction"></a>Введение

Microsoft SQL Server включает в себя функции, которые могут собирать и отправлять в Майкрософт сведения о компьютере или устройстве пользователя через Интернет (далее — "стандартные сведения о компьютере"). Компонент локального аудита для [сбора отзывов об использовании SQL Server](http://support.microsoft.com/kb/3153756) записывает собранные службой данные в указанную папку, где представлены данные (журналы), которые будет отправляться в корпорацию Майкрософт. Локальный аудит позволяет клиентам просмотреть все данные, которые корпорация Майкрософт собирает с помощью этой функции для обеспечения соответствия, выполнения нормативных требований или соблюдения конфиденциальности.  

Начиная с SQL Server 2016 с накопительным пакетом обновления 2, локальный аудит настраивается на уровне экземпляра для ядра СУБД SQL Server и служб Analysis Services (SSAS). В SQL Server 2016 с накопительным обновлением 4 (CU4) и SQL Server 2016 с пакетом обновления 1 (SP1) локальный аудит также включен для служб SQL Server Integration Services (SSIS). Другие компоненты SQL Server, устанавливаемые во время выполнения программы установки, и средства SQL Server, которые скачиваются или устанавливаются позднее, не имеют функций локального аудита для сбора отзывов об использовании. 

## <a name="prerequisites"></a>предварительные требования 

Ниже приведены предварительные требования для включения локального аудита на каждом экземпляре SQL Server. 

1. На экземпляре установлены исправления для SQL Server 2016 RTM с накопительным пакетом обновления 2 или более поздней версии. 

1. Пользователь должен быть системным администратором или использовать роль, позволяющую добавлять и изменять раздел реестра, создавать папки, управлять их безопасностью, а также останавливать и запускать службу Windows.  

## <a name="pre-configuration-steps-prior-to-turning-on-local-audit"></a>Шаги предварительной настройки перед включением локального аудита 

Перед включением аудита локального системному администратору требуется сделать следующее.

1. Узнать имя экземпляра SQL Server, а также учетную запись входа в службу телеметрии из программы улучшения качества (CEIP) SQL Server. 

1. Настроить новую папку для файлов локального аудита.

1. Предоставить разрешения для учетной записи входа в службу телеметрии из программы улучшения качества программного обеспечения SQL Server.

1. Создать раздел реестра для настройки конечного каталога локального аудита. 

    Для ядра СУБД и служб Integration Services требуется создать раздел в *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<INSTANCENAME\>\\CPE*. 
    
    Для служб Analysis Services требуется создать раздел в *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<INSTANCENAME\>\\CPE*.

### <a name="get-the-sql-server-ceip-service-logon-account"></a>Получение учетной записи входа в службу CEIP для SQL Server

Чтобы получить учетную запись входа в службу телеметрии из программы улучшения качества SQL Server, выполните следующие действия.
 
1. Запустите **Службы** — нажмите кнопку **Windows**  и введите *services.msc*. 

2. Перейдите к соответствующей службе. Например, для ядра СУБД найдите **Служба CEIP для SQL Server \<имя экземпляра\>**. Для служб Analysis Services найдите **CEIP для служб SQL Server Analysis Services \<имя экземпляра\>**. Для служб Integration Services найдите **службу CEIP 13 для служб Integration Services SQL Server**.

3. Щелкните правой кнопкой службу и выберите **Свойства**. 

4. Откройте вкладку **Вход в систему** . Учетная запись для входа приведена в поле **Указанная учетная запись**. 

### <a name="configure-a-new-folder-for-the-local-audit-files"></a>Настроить новую папку для файлов локального аудита.    

Создайте папку (каталог локального аудита), куда функция локального аудита будет записывать журналы. Например, полный путь к каталогу локального аудита для экземпляра ядра СУБД по умолчанию будет иметь вид: *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\*. 
 
> Примечание. Задайте путь к папке локального аудита за пределами пути установки SQL Server, чтобы избежать потенциальных проблем с SQL Server в результате включения функций аудита и применения соответствующих исправлений.

  ||Решение о разработки|Рекомендация|  
  |------|-----------------|----------|  
  |![Флажок](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Наличие свободного места |При умеренной рабочей нагрузке, когда используется около 10 баз данных, запланируете около 2 МБ места на диске в день на каждый экземпляр.|  
|![Флажок](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Отдельные каталоги | Создайте каталог для каждого экземпляра. Например, используйте *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\* для экземпляра SQL Server с именем `MSSQLSERVER`. Это упрощает управление файлами.
|![Флажок](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Отдельные папки |Используйте отдельную папку для каждой службы. Например, для определенного имени экземпляра используйте одну папку для ядра СУБД. Если экземпляр SSAS использует то же имя экземпляра, создайте для SSAS отдельную папку. Наличие экземпляров ядра СУБД и служб Analysis Services, настроенных для одной и той же папки, приведет к тому, что все данные локального аудита из обоих экземпляров будут записываться в один файл журнала.| 
|![Флажок](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Предоставление разрешения для учетной записи входа в службу телеметрии CIEP для SQL Server|Назначьте разрешения **Список содержимого папки**, **Чтение** и **Запись** для доступа к учетной записи входа в службу телеметрии CIEP для SQL Server.|


### <a name="grant-permissions-to-the-sql-server-ciep-telemetry-service-logon-account"></a>Предоставление разрешения для учетной записи входа в службу телеметрии CIEP для SQL Server
  
1. В **проводнике**, перейдите к расположению новой папки.  

1. Правой кнопкой мыши щелкните папку и выберите пункт **Свойства**. 

1. На вкладке **Безопасность**щелкните **Изменить** для управления разрешениями.

1. Щелкните **Добавить** и введите учетные данные службы телеметрии CEIP для SQL Server, например `NT Service\SQLTELEMETRY`.   

1. Щелкните **Проверить имена** , чтобы проверить указанное имя, и нажмите кнопку **ОК**. 

1. В диалоговом окне **Разрешение** выберите учетную запись входа в службу телеметрии CEIP для SQL Server и выберите **Список содержимого папки**, **Чтение** и **Запись**.  

1. Нажмите кнопку **ОК** , чтобы немедленно применить изменения разрешений. 
  
### <a name="create-a-registry-key-setting-to-configure-local-audit-target-directory"></a>Создать раздел реестра для настройки конечного каталога локального аудита.

1. Запустите программу regedit.  

1. Перейдите по соответствующему пути CPE. 

    Для ядра СУБД и служб Integration Services используйте *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<INSTANCENAME\>\\CPE*. 
    
    Для служб Analysis Services используйте *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<INSTANCENAME\>\\CPE*.

1. Щелкните путь CPE правой кнопкой мыши и выберите **Создать**. Щелкните **Строковое значение**.

1. Назовите новый раздел реестра " `UserRequestedLocalAuditDirectory`". 
 
## <a name="turning-local-audit-on-or-off"></a>Включение и отключение локального аудита

После завершения предварительной настройки вы можете включить локальный аудит. Для этого используйте учетную запись системного администратора или аналогичную роль, позволяющую изменять разделы реестра для включения и отключения локального аудита, выполнив следующие действия. 

1. Запустите программу **regedit**.  

1. Перейдите по соответствующему пути CPE. 

    Для ядра СУБД и служб Integration Services используйте *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<INSTANCENAME\>\\CPE*. 
    
    Для служб Analysis Services используйте *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<INSTANCENAME\>\\CPE*.

1. Щелкните правой кнопкой мыши **UserRequestedLocalAuditDirectory** и выберите *Изменить*. 

1. Чтобы включить локальный аудит, введите путь локального аудита, например *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\*.
 
    Чтобы отключить локальный аудит, задайте пустое значение **UserRequestedLocalAuditDirectory**.

1. Закройте программу **regedit**. 

Программа улучшения качества SQL Server должна сразу же распознать настройку локального аудита, если она уже запущена. Чтобы запустить службу программы улучшения качества SQL Server, системному администратору или пользователю, имеющего права для запуска или остановки служб Windows, требуется выполнить следующие действия. 

1. Запустите приложение служб, нажав кнопку Windows и введя "Службы". 

1. Перейдите к соответствующей службе. 

    Для ядра СУБД используйте **Служба CEIP для SQL Server (\<ИМЯ_ЭКЗЕМПЛЯРА\>)**. 
    
    Для служб Analysis Services используйте **CEIP для служб SQL Server Analysis Services (\<ИМЯ_ЭКЗЕМПЛЯРА\>)**. 

1. Щелкните правой кнопкой службу и выберите "Перезапуск". 

1. Убедитесь, что служба находится в состоянии **Выполняется**. 

Функция локального аудита создает один файл журнала в день. Файлы журнала имеют форму `<YYYY-MM-DD>.json`. Например, *2016-07-12.json*. Если в назначенном каталоге уже есть файл за этот день, функция локального аудита добавляет данные в него. В противном случае она создает новый файл за этот день. 

> Примечание. Первая запись журнала после включения локального аудита может занять до 5 минут. 

## <a name="maintenance"></a>Обслуживание 

1. Чтобы ограничить использование дискового пространства файлами, записываемыми функцией локального аудита, настройте политику или регулярное задание для очистки каталога локального аудита, чтобы удалить старые и ненужные файлы.  

2. Защитите путь к каталогу локального аудита, чтобы он был доступен только для соответствующих пользователей. Обратите внимание, что файлы журнала содержат сведения, описанные в разделе [How to configure SQL Server 2016 to send feedback to Microsoft](http://support.microsoft.com/kb/3153756)(Настройка SQL Server 2016 для отправки отзывов в корпорацию Майкрософт). Доступ для чтения этого файла должен быть запрещен большинству сотрудников вашей организации.  

## <a name="data-dictionary-of-local-audit-output-data-structure"></a>Словарь данных для структуры выходных данных локального аудита 

- Файлы журнала локального аудита имеют формат JSON и содержат набор объектов (строк), представляющих точки данных, которые отправляются обратно в корпорацию Майкрософт во время **emitTime**.  

- Каждая строка соответствует определенной схеме, определенной значением **schemaVersion**.   

- Каждая строка является выходным значением сеанса службы SQLCEIP, указанного в **sessionID**.  

- Строки выводятся в определенной последовательности, заданной значением **sequence**. 

- Каждая строка точки данных содержит выходные данные **queryIdentifier** , который может быть запросом T-SQL, сеансом XE или сообщением, связанным с типом трассировки, который обозначается значением **traceName**.   

- Группирование и контроль версий для**queryIdentifiers** осуществляются вместе с **querySetVersion**. 

- **data** содержит выходные данные соответствующего выполнения запроса, занявшего время **queryTimeInTicks**. 

- **queryIdentifiers** для запросов T-SQL имеют определение запроса T-SQL, хранящееся в запросе. 


| Логическая иерархия сведений о локальном аудите | Связанные столбцы |
| ------ | -------|
| Заголовок | emitTime, schemaVersion 
| Компьютер | hostname, domainHash, sqmID, operatingSystem 
| Экземпляр | instanceName, correlationID, clientVersion 
| Session | sessionID, traceName 
| Запрос | sequence, querySetVersion, queryIdentifier, query, queryTimeInTicks 
| data |  . 

### <a name="namevalue-pairs-definition-and-examples"></a>Определение пары "имя-значение" и примеры 

Указанные ниже столбцы представляют порядок выходных данных файлов для локального аудита. Односторонний хэш-алгоритм SHA 256 используется для обезличенных значений в указанных ниже столбцах.  

| Имя | Description | Примеры значений
|-------|--------| ----------|
|hostname | Обезличенное имя компьютера, где установлен SQL Server| de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11 
|domainHash| Обезличенный хэш домена для компьютера, где размещен экземпляр SQL Server | de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11 
|sqmId |Идентификатор, представляющий компьютер, где установлен SQL Server | 02AF58F5-753A-429C-96CD-3900E90DB990 
|INSTANCENAME| Обезличенное имя экземпляра SQL Server| e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 
|schemaVersion| Версия схемы SQLCEIP |  3 
|emitTime |Время вывода точки данных в формате UTC | 2016-09-08T17:20:22.1124269Z 
|sessionID | Идентификатор для обслуживания службы SQLCEIP | 89decf9a-ad11-485c-94a7-fefb3a02ed86 
| correlationId | Заполнитель для дополнительного идентификатора | 0 
|sequence | Порядковый номер точек данных, отправленных в рамках сеанса | 15 
| clientVersion | Версия экземпляра SQL Server | 13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223) 
| operatingSystem | Версия операционной системы, где установлен экземпляр SQL Server | Microsoft Windows Server 2012 R2 Datacenter 
| querySetVersion | Версия группы определений запросов | 1.0.0.0 
|traceName | Категории трассировки: (SQLServerXeQueries, SQLServerPeriodicQueries, SQLServerOneSettingsException) | SQLServerPeriodicQueries 
|queryIdentifier | Идентификатор запроса | SQLServerProperties.002 
|.   | Выходные сведения, собранные для queryIdentifier в виде вывода запроса T-SQL, сеанса XE или приложения |   [{"Collation": "SQL_Latin1_General_CP1_CI_AS","SqlFTinstalled": "0" "SqlIntSec": "1","IsSingleUser": "0","SqlFilestreamMode": "0","SqlPbInstalled": "0","SqlPbNodeRole": "","SqlVersionMajor": "13","SqlVersionMinor": "0","SqlVersionBuild": "2161","ProductBuildType": "","ProductLevel": "RTM","ProductUpdateLevel": "CU2","ProductUpdateReference": "KB3182270","ProductRevision": "3","SQLEditionId": "-1534726760","IsClustered": "0","IsHadrEnabled": "0","SqlAdvAInstalled": "0","PacketReceived": "1210","Version": "Microsoft SQL Server 2016 (RTM-CU2) (KB3182270) - 13.0.2161.3 (X64) \n\tSep  7 2016 14:24:16 \n\tCopyright (c) Microsoft Corporation\n\tStandard Edition (64-bit) on Windows Server 2012 R2 Datacenter 6.3 \u003cX64\u003e (Build 9600: ) (Hypervisor)\n"}],
|Запрос| Если это применимо, определение запроса T-SQL, связанное с queryIdentifier, который создает данные.        Этот компонент не отправляется службой CEIP SQL Server. Он включен в локальный аудит только для справки.| SELECT\n      SERVERPROPERTY(\u0027Collation\u0027) AS [Collation],\n      SERVERPROPERTY(\u0027IsFullTextInstalled\u0027) AS [SqlFTinstalled],\n      SERVERPROPERTY(\u0027IsIntegratedSecurityOnly\u0027) AS [SqlIntSec],\n      SERVERPROPERTY(\u0027IsSingleUser\u0027) AS [IsSingleUser],\n      SERVERPROPERTY (\u0027FileStreamEffectiveLevel\u0027) AS [SqlFilestreamMode],\n      SERVERPROPERTY(\u0027IsPolybaseInstalled\u0027) AS [SqlPbInstalled],\n      SERVERPROPERTY(\u0027PolybaseRole\u0027) AS [SqlPbNodeRole],\n      SERVERPROPERTY(\u0027ProductMajorVersion\u0027) AS [SqlVersionMajor],\n      SERVERPROPERTY(\u0027ProductMinorVersion\u0027) AS [SqlVersionMinor],\n      SERVERPROPERTY(\u0027ProductBuild\u0027) AS [SqlVersionBuild],\n      SERVERPROPERTY(\u0027ProductBuildType\u0027) AS ProductBuildType,\n      SERVERPROPERTY(\u0027ProductLevel\u0027) AS ProductLevel,\n      SERVERPROPERTY(\u0027ProductUpdateLevel\u0027) AS ProductUpdateLevel,\n      SERVERPROPERTY(\u0027ProductUpdateReference\u0027) AS ProductUpdateReference,\n      RIGHT(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)),CHARINDEX(\u0027.\u0027, REVERSE(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)))) - 1) AS ProductRevision,\n      SERVERPROPERTY(\u0027EditionID\u0027) AS SQLEditionId,\n      SERVERPROPERTY(\u0027IsClustered\u0027) AS IsClustered,\n      SERVERPROPERTY(\u0027IsHadrEnabled\u0027) AS IsHadrEnabled,\n      SERVERPROPERTY(\u0027IsAdvancedAnalyticsInstalled\u0027) AS [SqlAdvAInstalled],\n      @@PACK_RECEIVED AS PacketReceived,\n      @@VERSION AS Version
|queryTimeInTicks | Время, затрачиваемое на выполнение запроса в следующей категории трассировки: (SQLServerXeQueries, SQLServerPeriodicQueries) |  0 
 
### <a name="trace-categories"></a>Категории трассировки 
Сейчас мы собираем следующие категории трассировки. 

- **SQLServerXeQueries**: содержит точки данных, собранные в рамках сеанса расширенных событий. 

- **SQLServerPeriodicQueries**: содержит точки данных, собранные периодическими запросами, выполняемыми в экземпляре SQL Server. 

- **SQLServerPerDBPeriodicQueries**: содержит точки данных, собранные периодическими запросами, выполняемыми для баз данных (до 30) в экземпляре SQL Server. 

- **SQLServerOneSettingsException**: содержит сообщения об исключениях, связанные с обновлением схемы и/или набора запроса. 

- **DigitalProductID**: содержит точки данных для статистической обработки обезличенного (SHA-256) хэшированного идентификатора цифрового продукта для экземпляров SQL Server. 

### <a name="local-audit-file-examples"></a>Примеры файла локального аудита



Ниже приведен отрывок выходных данных файла JSON для локального аудита.

```JSON
{
    "hostName": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "domainHash": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "sqmId": "02AF58F5-753A-429C-96CD-3900E90DB990",
    "instanceName": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "schemaVersion": "3",
    "emitTime": "2016-09-08T17:20:22.1124269Z",
    "sessionId": "89decf9a-ad11-485c-94a7-fefb3a02ed86",
    "correlationId": 0,
    "sequence": 15,
    "clientVersion": "13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223)",
    "operatingSystem": "Microsoft Windows Server 2012 R2 Datacenter",
    "querySetVersion": "1.0.0.0",
    "traceName": "SQLServerPeriodicQueries",
    "queryIdentifier": "SQLServerProperties.002",
    "data": [
      {
        "Collation": "SQL_Latin1_General_CP1_CI_AS",
        "SqlFTinstalled": "0",
        "SqlIntSec": "1",
        "IsSingleUser": "0",
        "SqlFilestreamMode": "0",
        "SqlPbInstalled": "0",
        "SqlPbNodeRole": "",
        "SqlVersionMajor": "13",
        "SqlVersionMinor": "0",
        "SqlVersionBuild": "2161",
        "ProductBuildType": "",
        "ProductLevel": "RTM",
        "ProductUpdateLevel": "CU2",
        "ProductUpdateReference": "KB3182270",
        "ProductRevision": "3",
        "SQLEditionId": "-1534726760",
        "IsClustered": "0",
        "IsHadrEnabled": "0",
        "SqlAdvAInstalled": "0",
        "PacketReceived": "1210",
        "Version": "Microsoft SQL Server 2016 (RTM-CU2) (KB3182270) - 13.0.2161.3 (X64) \n\tSep  7 2016 14:24:16 \n\tCopyright (c) Microsoft Corporation\n\tStandard Edition (64-bit) on Windows Server 2012 R2 Datacenter 6.3 \u003cX64\u003e (Build 9600: ) (Hypervisor)\n"
      }
    ],
    "query": "SELECT\n      SERVERPROPERTY(\u0027Collation\u0027) AS [Collation],\n      SERVERPROPERTY(\u0027IsFullTextInstalled\u0027) AS [SqlFTinstalled],\n      SERVERPROPERTY(\u0027IsIntegratedSecurityOnly\u0027) AS [SqlIntSec],\n      SERVERPROPERTY(\u0027IsSingleUser\u0027) AS [IsSingleUser],\n      SERVERPROPERTY (\u0027FileStreamEffectiveLevel\u0027) AS [SqlFilestreamMode],\n      SERVERPROPERTY(\u0027IsPolybaseInstalled\u0027) AS [SqlPbInstalled],\n      SERVERPROPERTY(\u0027PolybaseRole\u0027) AS [SqlPbNodeRole],\n      SERVERPROPERTY(\u0027ProductMajorVersion\u0027) AS [SqlVersionMajor],\n      SERVERPROPERTY(\u0027ProductMinorVersion\u0027) AS [SqlVersionMinor],\n      SERVERPROPERTY(\u0027ProductBuild\u0027) AS [SqlVersionBuild],\n      SERVERPROPERTY(\u0027ProductBuildType\u0027) AS ProductBuildType,\n      SERVERPROPERTY(\u0027ProductLevel\u0027) AS ProductLevel,\n      SERVERPROPERTY(\u0027ProductUpdateLevel\u0027) AS ProductUpdateLevel,\n      SERVERPROPERTY(\u0027ProductUpdateReference\u0027) AS ProductUpdateReference,\n      RIGHT(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)),CHARINDEX(\u0027.\u0027, REVERSE(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)))) - 1) AS ProductRevision,\n      SERVERPROPERTY(\u0027EditionID\u0027) AS SQLEditionId,\n      SERVERPROPERTY(\u0027IsClustered\u0027) AS IsClustered,\n      SERVERPROPERTY(\u0027IsHadrEnabled\u0027) AS IsHadrEnabled,\n      SERVERPROPERTY(\u0027IsAdvancedAnalyticsInstalled\u0027) AS [SqlAdvAInstalled],\n      @@PACK_RECEIVED AS PacketReceived,\n      @@VERSION AS Version",
    "queryTimeInTicks": 0
  } ,
  {
    "hostName": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "domainHash": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "sqmId": "02AF58F5-753A-429C-96CD-3900E90DB990",
    "instanceName": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "schemaVersion": "3",
    "emitTime": "2016-09-08T17:20:24.9819144Z",
    "sessionId": "89decf9a-ad11-485c-94a7-fefb3a02ed86",
    "correlationId": 0,
    "sequence": 61,
    "clientVersion": "13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223)",
    "operatingSystem": "Microsoft Windows Server 2012 R2 Datacenter",
    "querySetVersion": "1.0.0.0",
    "traceName": "SQLServerPeriodicQueries",
    "queryIdentifier": "ExternalScriptStats.001",
    "data": [
      {
        "counter_name": "Total Executions                                                                                                                ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Parallel Executions                                                                                                             ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Streaming Executions                                                                                                            ",
        "cntr_value": "0"
      },
      {
        "counter_name": "SQL CC Executions                                                                                                               ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Implied Auth. Logins                                                                                                            ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Total Execution Time (ms)                                                                                                       ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Execution Errors                                                                                                                ",
        "cntr_value": "0"
      }
    ],  
    "query": "select counter_name, cntr_value from sys.dm_os_performance_counters where object_name like \u0027%External Scripts%\u0027",
    "queryTimeInTicks": 155834
  } 
```
## <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

**Как администраторы баз данных читают файлы журнала локального аудита?**
Эти файлы журналов записываются в формате JSON. Каждая строка соответствует объекту JSON, представляющему фрагмент телеметрии, отправляемый корпорации Майкрософт. Имена полей должны быть понятными и очевидными. 

**Что произойдет, если администратор базы данных отключит сбор отзывов об использовании?**
Запись файла локального аудита не выполняется. 

**Что произойдет, если нет подключения к Интернету или компьютер защищен брандмауэром?**
Отзывы об использовании SQL Server 2016 не будут отправляться в корпорацию Майкрософт. При правильной настройке функция по-прежнему будет пытаться записать журналы локального аудита.

**Как администраторы баз данных отключают локальный аудит?**
Удаляя запись раздела реестра UserRequestedLocalAuditDirectory.

**Кто может читать файлы журнала локального аудита?**
Любой пользователь в вашей организации, имеющий доступ к каталогу локального аудита.

**Как администраторы баз данных управляют файлами журналов, записываемыми в указанный каталог?**
Администраторам баз данных необходимо самостоятельно следить за очисткой файлов в каталоге, чтобы избежать использования слишком большого объема места на диске.

**Существует ли клиент или инструмент, который можно использовать для чтения выходных данных JSON?**
Выходные данные можно прочитать в Блокноте, Visual Studio или любом подходящем модуле чтения JSON.
Кроме того, прочитать файл JSON и проанализировать данные можно в экземпляре SQL Server 2016, как показано ниже. Дополнительные сведения чтении файла JSON в SQL Server см. в разделе [Импорт файлов JSON в SQL Server с помощью функции OPENROWSET (BULK) и OPENJSON (Transact-SQL)](http://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/10/07/bulk-importing-json-files-into-sql-server/).

```Transact-SQL
DECLARE @JSONFile AS VARCHAR(MAX)

-- Read the JSON file into variable 
SELECT @JSONFile = BulkColumn 
FROM OPENROWSET (BULK 'C:\SQLCEIPAudit\MSSQLSERVER\2016-09-08.json', SINGLE_CLOB) MyFile 

-- Check if the JSON file has been read properly and if it's in a JSON format
SELECT 
    @JSONFile LocalAuditOutput, 
    ISJSON(@JSONFile) IsFileInJSONFormat

-- Get the query identifier, query and the data (output of the query)   
SELECT 
    sequence,
    queryIdentifier,
    query,
    data
FROM OPENJSON(@JSONFile) 
    WITH (sessionId VARCHAR(64)
         ,sequence INT
         ,queryIdentifier VARCHAR(128)
         ,query VARCHAR(MAX)
         ,data NVARCHAR(MAX) AS JSON)
-- Get specific details about the output of "DatabaseProperties.001" query  
SELECT 
    QueryIdentifier,
    DatabaseID,
    CompatibilityLevel,
    IsQueryStoreOn
FROM OPENJSON(@JSONFile) 
    WITH (sessionId VARCHAR(64)
         ,sequence INT
         ,queryIdentifier VARCHAR(128)
         ,query VARCHAR(MAX)
         ,data NVARCHAR(MAX) AS JSON) 
    CROSS APPLY OPENJSON(data) 
        WITH (   DatabaseID varchar(128) '$.database_id'
                ,CompatibilityLevel varchar(128) '$.compatibility_level'
                ,IsQueryStoreOn varchar(128) '$.QS'
             )
WHERE queryIdentifier = 'DatabaseProperties.001'
```

## <a name="see-also"></a>См. также:
[Локальный аудит для сбора отзывов об использовании SSMS](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-telemetry-ssms)

