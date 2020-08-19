---
description: sys.dm_external_script_requests
title: sys. dm_external_script_requests | Документация Майкрософт
ms.custom: ''
ms.date: 06/26/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_requests
- sys.dm_external_script_requests_TSQL
- dm_external_script_requests
- dm_external_script_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_requests dynamic management view
ms.assetid: e7e7c50f-b8b2-403c-b8c8-1955da5636c3
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 1b3c1f10be0b454503c5fbcfd9cdab191a687797
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489850"
---
# <a name="sysdm_external_script_requests"></a>sys.dm_external_script_requests
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

Возвращает строку для каждой активной рабочей учетной записи, в которой выполняется внешний скрипт.
  
> [!NOTE]
> Это динамическое административное представление доступно только в том случае, если вы установили и включили функцию, поддерживающую выполнение внешних скриптов. Дополнительные сведения см. в статьях [службы машинного обучения (R, Python) в SQL Server 2017 и более поздних версиях](../../machine-learning/sql-server-machine-learning-services.md), [службы R в SQL Server 2016](../../machine-learning/r/sql-server-r-services.md)и [службы машинного обучения в управляемый экземпляр SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**уникальный идентификатор**|Идентификатор процесса, который отправил запрос на внешний скрипт. Соответствует ИДЕНТИФИКАТОРу процесса, полученному экземпляром SQL.|  
|язык|**nvarchar**|Ключевое слово, которое представляет поддерживаемый язык скриптов. |  
|degree_of_parallelism|**int**|Число, указывающее количество созданных параллельных процессов. Это значение может отличаться от количества запрошенных параллельных процессов.|  
|external_user_name|**nvarchar**|Рабочая учетная запись Windows, под которой был выполнен скрипт.|  
  
## <a name="permissions"></a>Разрешения

 Требуется `VIEW SERVER STATE` разрешение на сервере.  
  
> [!NOTE]
> Пользователи, выполняющие внешние скрипты, должны иметь дополнительное разрешение `EXECUTE ANY EXTERNAL SCRIPT` , однако это динамическое административное представление может использоваться администраторами без этого разрешения. 
  
## <a name="remarks"></a>Комментарии  

Это представление можно отфильтровать с помощью идентификатора языка скриптов.

Кроме того, оно возвращает рабочую учетную запись, под которой выполняется скрипт. Сведения о рабочих учетных записях, используемых внешними скриптами, см. в разделе удостоверения, используемые при обработке (SQLRUserGroup) в статье [Общие сведения о безопасности для платформы расширяемости в SQL Server службы машинного обучения](../../machine-learning/concepts/security.md#sqlrusergroup).

Идентификатор GUID, который возвращается в поле **external_script_request_id** , также представляет имя файла защищенного каталога, где хранятся временные файлы. Каждая Рабочая учетная запись, например MSSQLSERVER01, представляет одно имя входа SQL или пользователя Windows и может использоваться для выполнения нескольких запросов скрипта. По умолчанию эти временные файлы удаляются после завершения запрошенного скрипта.

Это динамическое административное представление отслеживает только активные процессы и не может выводить данные по скриптам, которые уже выполнены. Если требуется отследить время выполнения скриптов, рекомендуется добавить сведения о времени в скрипт и фиксировать их во время его выполнения.

## <a name="examples"></a>Примеры  
  
### <a name="viewing-the-currently-active-scripts-for-a-particular-process"></a>Просмотр текущих активных скриптов для определенного процесса

 Следующий пример показывает число выполнений внешних скриптов в текущем экземпляре.  
  
```sql
SELECT external_script_request_id
  , [language]
  , degree_of_parallelism
  , external_user_name
FROM sys.dm_external_script_requests;
```  

Результаты  

external_script_request_id  |язык  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     R    |      1   |  MSSQLSERVER01

## <a name="see-also"></a>См. также

+ [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Динамические административные представления и функции, связанные с выполнением (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
+ [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
