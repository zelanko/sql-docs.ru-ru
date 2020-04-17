---
title: sys.dm_external_script_requests Документы Майкрософт
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
ms.openlocfilehash: 70f1024f73ff955facaa2b6a2af2b9f5f4ccf247
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488205"
---
# <a name="sysdm_external_script_requests"></a>sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает строку для каждой активной рабочей учетной записи, в которой выполняется внешний скрипт.
  
> [!NOTE] 
>  
> Это динамическое представление управления (DMV) доступно только в том случае, если вы установили и включили функцию, поддерживающую выполнение внешнего скрипта. Для получения более подробной информации см. [R-сервисы в S'L Server 2016](../../machine-learning/r/sql-server-r-services.md) и [Службы машинного обучения (R, Python) в S'L Server 2017 и позже.](../../machine-learning/sql-server-machine-learning-services.md)  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**уникальный идентификатор**|Идентификатор процесса, который отправил запрос на внешний скрипт. Это соответствует идентификатору процесса, полученному[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|Язык|**nvarchar**|Ключевое слово, которое представляет поддерживаемый язык скриптов. |  
|degree_of_parallelism|**int**|Число, указывающее количество созданных параллельных процессов. Это значение может отличаться от количества запрошенных параллельных процессов.|  
|external_user_name|**nvarchar**|Рабочая учетная запись Windows, под которой был выполнен скрипт.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW SERVER STATE для сервера.  
  
> [!NOTE]
>   
>  Пользователям, выполняющим внешние скрипты, требуется дополнительное разрешение EXECUTE ANY EXTERNAL SCRIPT, однако администраторы могут использовать это динамическое административное представление без такого разрешения. 
  
## <a name="remarks"></a>Примечания  

Это представление можно отфильтровать с помощью идентификатора языка скриптов.

Кроме того, оно возвращает рабочую учетную запись, под которой выполняется скрипт. Для получения информации об учетных записях работников, используемых внешними скриптами, см. раздел «Идентификаторы», используемые при обработке данных (S'LRUserGroup), в [обзоре безопасности для платформы для расширяемости в службах машинного обучения сервера S'L](../../machine-learning/concepts/security.md#sqlrusergroup)Server.

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


external_script_request_id  |Язык  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     R    |      1   |  MSSQLSERVER01       


  
## <a name="see-also"></a>См. также:  
 [Динамические представления и функции управления &#40;&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

