---
title: Просмотр и чтение журнала диагностики для экземпляра отказоустойчивого кластера | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 68074bd5-be9d-4487-a320-5b51ef8e2b2d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 19308ee2838238f0dea6cfdaeb228a250591613b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63049340"
---
# <a name="view-and-read-failover-cluster-instance-diagnostics-log"></a>Просмотр и чтение журнала диагностики экземпляра отказоустойчивого кластера
  Все критические ошибки и события предупреждений для библиотеки ресурсов SQL Server записываются в журнал событий Windows. Диагностические сведения, связанные с SQL Server и записываемые в журнал, перехватываются хранимой процедурой [sp_server_diagnostics (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) и записываются в файлы журнала диагностики отказоустойчивого кластера SQL Server (также называемые журналами *SQLDIAG*).  
  
-   **Перед началом:**  [Рекомендации по](#Recommendations), [безопасности](#Security)  
  
-   **Просмотр журнала диагностики с помощью:**  [среды SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
-   **Чтобы Настройка параметров журнала диагностики, с помощью:** [Transact-SQL](#TsqlConfigure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
 По умолчанию SQLDIAG хранятся в локальной папке LOG в каталоге экземпляра SQL Server, например, "C\Program Files\Microsoft SQL Server\MSSQL12. \<Имя_экземпляра > \MSSQL\LOG ", узла-владельца из экземпляра кластера отработки отказа AlwaysOn (FCI). Размер каждого файла журнала SQLDIAG ограничен 100 МБ. На компьютере сохраняются десять таких файлов журнала, после чего они освобождаются для новых журналов.  
  
 В журналах используется формат файлов расширенных событий. Для чтения файлов, созданных расширенными событиями, можно использовать системную функцию **sys.fn_xe_file_target_read_file** . Возвращается одно событие в каждой строке в формате XML. Выполните запрос к системному представлению для синтаксического анализа XML-данных в виде результирующего набора. Дополнительные сведения см. в разделе [sys.fn_xe_file_target_read_file (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для запуска **fn_xe_file_target_read_file**требуется разрешение VIEW SERVER STATE.  
  
 Откройте среду SQL Server Management Studio в качестве администратора  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр файлов журнала диагностики:**  
  
1.  В меню **Файл** выберите **Открыть**, **Файл**и выберите файл журнала диагностики для просмотра.  
  
2.  События отображаются в виде строк в правой панели, причем по умолчанию показаны только два столбца, **name**и **timestamp** .  
  
     Это также приводит к активации меню **ExtendedEvents** .  
  
3.  Для отображения большего числа столбцов перейдите в меню **ExtendedEvents** и укажите **Выбрать столбцы**.  
  
     Откроется диалоговое окно с доступными столбцами, позволяя выбрать столбцы для отображения.  
  
4.  Можно фильтровать и сортировать данные событий, используя меню **ExtendedEvents** и выбирая параметр **Фильтр** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр файлов журнала диагностики:**  
  
 Для просмотра всех записей в файле журнала SQLDIAG используйте следующий запрос.  
  
```  
SELECT  
xml_data.value('(event/@name)[1]','varchar(max)') AS 'Name'  
,xml_data.value('(event/@package)[1]','varchar(max)') AS 'Package'  
,xml_data.value('(event/@timestamp)[1]','datetime') AS 'Time'  
,xml_data.value('(event/data[@name=''state'']/value)[1]','int') AS 'State'  
,xml_data.value('(event/data[@name=''state_desc'']/text)[1]','varchar(max)') AS 'State Description'  
,xml_data.value('(event/data[@name=''failure_condition_level'']/value)[1]','int') AS 'Failure Conditions'  
,xml_data.value('(event/data[@name=''node_name'']/value)[1]','varchar(max)') AS 'Node_Name'  
,xml_data.value('(event/data[@name=''instancename'']/value)[1]','varchar(max)') AS 'Instance Name'  
,xml_data.value('(event/data[@name=''creation time'']/value)[1]','datetime') AS 'Creation Time'  
,xml_data.value('(event/data[@name=''component'']/value)[1]','varchar(max)') AS 'Component'  
,xml_data.value('(event/data[@name=''data'']/value)[1]','varchar(max)') AS 'Data'  
,xml_data.value('(event/data[@name=''info'']/value)[1]','varchar(max)') AS 'Info'  
FROM  
 ( SELECT object_name AS 'event'  
  ,CONVERT(xml,event_data) AS 'xml_data'  
  FROM sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SQLNODE1_MSSQLSERVER_SQLDIAG_0_129936003752530000.xel',NULL,NULL,NULL)   
)   
AS XEventData  
ORDER BY Time;  
  
```  
  
> [!NOTE]  
>  Можно отфильтровать результаты для определенных компонентов или состояний с помощью предложения WHERE.  
  
##  <a name="TsqlConfigure"></a> Использование Transact-SQL  
 **Настройка свойств журнала диагностики**  
  
> [!NOTE]  
>  Пример этой процедуры см. в подразделе [Примеры (Transact-SQL)](#TsqlExample)далее в этом разделе.  
  
 С помощью инструкции языка описания данных DDL, `ALTER SERVER CONFIGURATION`, можно запускать или останавливать запись в журнал диагностических данных, полученных с [sp_server_diagnostics &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) процедуры, а также журнал SQLDIAG набора параметры конфигурации, такие как количество переключений файлов журнала, размер файла журнала и расположение файла. Дополнительные сведения о синтаксисе см. в разделе [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic).  
  
###  <a name="ConfigTsqlExample"></a> Примеры (Transact-SQL)  
  
####  <a name="TsqlExample"></a> Setting diagnostic log options  
 В примерах этого раздела показана установка значений параметра журнала диагностики.  
  
##### <a name="a-starting-diagnostic-logging"></a>A. Запуск регистрации диагностических данных в журнале  
 В следующем примере запускается запись в журнал диагностических данных.  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG ON;  
```  
  
##### <a name="b-stopping-diagnostic-logging"></a>Б. Останов регистрации диагностических данных в журнале  
 В следующем примере запись в журнал диагностических данных прекращается.  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG OFF;  
```  
  
##### <a name="c-specifying-the-location-of-the-diagnostic-logs"></a>В. Задание расположения журналов диагностических данных  
 В следующем примере для журналов диагностических данных задается расположение по указанному пути к файлам.  
  
```  
ALTER SERVER CONFIGURATION  
SET DIAGNOSTICS LOG PATH = 'C:\logs';  
```  
  
##### <a name="d-specifying-the-maximum-size-of-each-diagnostic-log"></a>Г. Задание максимального размера каждого из журналов диагностики  
 В следующем примере задан максимальный размер каждого из журналов диагностики, равный 10 мегабайтам.  
  
```  
ALTER SERVER CONFIGURATION   
SET DIAGNOSTICS LOG MAX_SIZE = 10 MB;  
```  
  
## <a name="see-also"></a>См. также  
 [Политика отработки отказа для экземпляров отказоустойчивого кластера](failover-policy-for-failover-cluster-instances.md)  
  
  
