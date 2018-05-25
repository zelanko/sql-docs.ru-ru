---
title: sys.dm_external_script_requests | Документы Microsoft
ms.custom: ''
ms.date: 06/24/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bc6db4816e4ba890e132600874d5db21aa190c02
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmexternalscriptrequests"></a>sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает строку для каждой активной рабочей учетной записи, в которой выполняется внешний скрипт.
 
  
> [!NOTE] 
>  
>  Это динамическое административное представление доступно только в том случае, если вы установили и включили функцию, которая поддерживает выполнение внешнего скрипта. Сведения о том, как сделать это для скриптов R, см. в разделе [Установка служб SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**Уникальный идентификатор**|Идентификатор процесса, который отправил запрос на внешний скрипт. Соответствует идентификатору процесса как полученных [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|language|**nvarchar**|Ключевое слово, которое представляет поддерживаемый язык скриптов. Сейчас поддерживается только `R` .|  
|degree_of_parallelism|**int**|Число, указывающее количество созданных параллельных процессов. Это значение может отличаться от количества запрошенных параллельных процессов.|  
|external_user_name|**nvarchar**|Рабочая учетная запись Windows, под которой был выполнен скрипт.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW SERVER STATE для сервера.  
  
> [!NOTE]
>   
>  Пользователям, выполняющим внешние скрипты, требуется дополнительное разрешение EXECUTE ANY EXTERNAL SCRIPT, однако администраторы могут использовать это динамическое административное представление без такого разрешения. 
  
## <a name="remarks"></a>Примечания  

Это представление можно отфильтровать с помощью идентификатора языка скриптов.

Кроме того, оно возвращает рабочую учетную запись, под которой выполняется скрипт. Сведения о рабочих учетных записях, используемых скриптами R, см. в разделе [Изменение пула учетных записей пользователей для служб R](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).

Идентификатор GUID, который возвращается в поле **external_script_request_id** , также представляет имя файла защищенного каталога, где хранятся временные файлы. Каждая рабочая учетная запись, например MSSQLSERVER01, представляет отдельное имя входа SQL или пользователя Windows, а также может использоваться для выполнения нескольких запросов скриптов. По умолчанию эти временные файлы удаляются после завершения запрошенного скрипта. Если необходимо сохранить эти файлы в течении некоторого периода для отладки, можно изменить флаг очистки, как описано в разделе [Настройка и управление расширениями углубленной аналитики](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md).  
 
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
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

