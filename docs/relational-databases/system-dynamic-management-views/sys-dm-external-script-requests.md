---
title: sys.dm_external_script_requests | Документация Майкрософт
ms.custom: ''
ms.date: 10/28/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54c572acac645146e3db18195a0dbe5b794effdc
ms.sourcegitcommit: c2322c1a1dca33b47601eb06c4b2331b603829f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50743192"
---
# <a name="sysdmexternalscriptrequests"></a>sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает строку для каждой активной рабочей учетной записи, в которой выполняется внешний скрипт.
  
> [!NOTE] 
>  
> Это динамическое административное представление (DMV) доступна только в том случае, если вы установили и включили функцию, которая поддерживает выполнение внешнего скрипта. Дополнительные сведения см. в разделе [служб R в SQL Server 2016](../../advanced-analytics/r/sql-server-r-services.md) и [служб машинного обучения (R, Python) в SQL Server 2017](../../advanced-analytics/what-is-sql-server-machine-learning.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**Уникальный идентификатор**|Идентификатор процесса, который отправил запрос на внешний скрипт. Это соответствует идентификатору процесса, получаемому [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|language|**nvarchar**|Ключевое слово, которое представляет поддерживаемый язык скриптов. |  
|degree_of_parallelism|**int**|Число, указывающее количество созданных параллельных процессов. Это значение может отличаться от количества запрошенных параллельных процессов.|  
|external_user_name|**nvarchar**|Рабочая учетная запись Windows, под которой был выполнен скрипт.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW SERVER STATE для сервера.  
  
> [!NOTE]
>   
>  Пользователям, выполняющим внешние скрипты, требуется дополнительное разрешение EXECUTE ANY EXTERNAL SCRIPT, однако администраторы могут использовать это динамическое административное представление без такого разрешения. 
  
## <a name="remarks"></a>Примечания  

Это представление можно отфильтровать с помощью идентификатора языка скриптов.

Кроме того, оно возвращает рабочую учетную запись, под которой выполняется скрипт. Сведения о рабочих учетных записей, используемых внешних скриптов, см. в разделе удостоверений, используемых при обработке (SQLRUserGroup) статьи [Общие сведения о безопасности для инфраструктуры расширяемости в службах машинного обучения SQL Server](../../advanced-analytics/concepts/security.md#sqlrusergroup).

Идентификатор GUID, который возвращается в поле **external_script_request_id** , также представляет имя файла защищенного каталога, где хранятся временные файлы. Каждая рабочая учетная запись, например MSSQLSERVER01, представляет отдельное имя входа SQL или пользователя Windows, а также может использоваться для выполнения нескольких запросов скриптов. По умолчанию эти временные файлы удаляются после завершения запрошенного скрипта.
 
Это динамическое административное представление отслеживает только активные процессы и не может выводить данные по скриптам, которые уже выполнены. Если требуется отследить время выполнения скриптов, рекомендуется добавить сведения о времени в скрипт и фиксировать их во время его выполнения.

## <a name="examples"></a>Примеры  
  
### <a name="viewing-the-currently-active-r-scripts-for-a-particular-process"></a>Просмотр активных скриптов R для определенного процесса 
 Следующий пример показывает число выполнений внешних скриптов в текущем экземпляре.  
  
```  
SELECT external_script_request_id 
  , [language]
  , degree_of_parallelism
  , external_user_name
FROM sys.dm_external_script_requests; 
```  

Результаты  


external_script_request_id  |language  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     Чтение    |      1   |  MSSQLSERVER01       


  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

